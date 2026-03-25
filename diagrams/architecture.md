# System Architecture (QNX + Android)

## Setup

Two OSes, one SoC:

- QNX handles real-time services
- Android handles UI and apps
- A hypervisor sits in between

---

## Simplified view

```mermaid
graph LR
    Android --> IPC
    IPC --> QNX
    QNX --> Hardware
