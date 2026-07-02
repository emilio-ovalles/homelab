# homelab

## intro

this serves as a reference and inventory of my homelab setup - its current state and future work.

## purpose

this homelab from my experience taking down my home network experimenting with pihole. i needed a way to segment my network and have a sandbox environment where misconfigurations were self-contained and other people and devices would not be affected. the verizon-supplied internet gateway did not support the functionality required to do this, so the network hardware migrated to a unifi stack. the homelab has since evolved as a way to learn about networking, self-host applications and services, repurpose old hardware, and explore networking, security, and infrastructure concepts without running up an AWS bill.

## architecture
```mermaid
flowchart TD
    wan[WAN]
    
    subgraph mgmt["Management VLAN (1)"]
        cgu{{Cloud Gateway Ultra <br/> Router · Firewall · IPS}}
        switch[[USW-Lite-8-PoE]]
        ap1[[U6+ AP]]
        ap2[[U6 Lite AP]]
    end

    subgraph trustedvlan["Trusted VLAN (10)"]
        printer[Printer]
        iot[IoT Devices x10]
        gaming[Gaming Consoles x2]
        mobile[Mobile Devices x4]
        laptops[Laptops x3]
        ha[Home Assistant Pi]
        hue[Hue Bridge]
    end

    subgraph iotvlan["IoT VLAN (20)"]
        iotempty[Unused]
    end

    subgraph guestvlan["Guest VLAN (30)"]
        guestempty[Unused]
    end

    subgraph homelabvlan["Homelab VLAN (40)"]
        air[Media Server]
        pro[App Server]
    end

    wan --> cgu
    cgu --> switch
    switch --> ap1
    switch --> hue
    switch --> ha
    switch --> air
    ap1 --- |Mesh Uplink| ap2
    ap1 --> pro
    ap1 --> printer
    ap1 --> iot
    ap1 --> gaming
    ap1 --> mobile
    ap1 --> laptops
    ap2 --> iot
    ap2 --> mobile
    ap2 --> laptops
```
