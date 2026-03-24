# System Architecture: Cross-OS Communication via SOME/IP

## Overview

This diagram illustrates communication between a Linux guest and an RTOS guest running on a virtualized automotive SoC. The two domains interact using SOME/IP over a virtual Ethernet interface.

## Architecture Diagram

```mermaid
graph LR
    subgraph Linux_Guest["Linux Guest (General-purpose OS)"]
        A1[Client Application]
        A2[CommonAPI Proxy]
    end

    subgraph Virtual_Network["Virtual Ethernet"]
        V1[Virtual Switch / Bridge]
    end

    subgraph RTOS_Guest["RTOS Guest (Real-Time OS)"]
        B1[CommonAPI Stub]
        B2[Media / Sensor Service]
    end

    A1 --> A2
    A2 -->|SOME/IP| V1
    V1 -->|SOME/IP| B1
    B1 --> B2

    B2 -->|Event Notification| B1
    B1 -->|SOME/IP| V1
    V1 -->|SOME/IP| A2
    A2 --> A1
