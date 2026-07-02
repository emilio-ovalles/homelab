# homelab

## intro

this serves as a reference and inventory of my homelab setup - its current state and future work.

## purpose

this homelab from my experience taking down my home network experimenting with pihole. i needed a way to segment my network and have a sandbox environment where misconfigurations were self-contained and other people and devices would not be affected. the verizon-supplied internet gateway did not support the functionality required to do this, so the network hardware migrated to a unifi stack. the homelab has since evolved as a way to learn about networking, self-host applications and services, repurpose old hardware, and explore networking, security, and infrastructure concepts without running up an AWS bill.

## architecture
```mermaid
flowchart TD
    A[WAN] --> B{Unifi CGU}
    B --> C[Media Server]
    B --> D[Home Assistant]
    B --> E{U6+ AP}
    B --> F[Hue Bridge]
    E --> Client1[Desk Echo Dot]
    E --> Client2[Printer]
    E --> Client3[PS4]
    E --> Client4[Thermostat]
    E --> Client5[Nintendo Switch]
    E --> Client6[Doorbell]
    E --> Client7[Tablet]
    E --- |Uplink| E2{U6 Lite AP - Uplink}
    E --> Client8[Roku]
    E --> Client9[Laptop]
    E --> Client10[iPhone]
    E --> Client11[Laptop]
    E --> Client12[App Server]
    E --> Client13[Kitchen Echo]
    E2 --> Client14[Bedroom TV]
    E2 --> Client15[Kid's TV]
    E2 --> Client16[Bedroom Echo Spot]
    E2 --> Client17[Bathroom Echo]
    E2 --> Client18[Laptop]
```
