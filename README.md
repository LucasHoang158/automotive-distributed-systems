# Automotive Distributed Systems

This repository presents a collection of system-level explorations in modern automotive software, focusing on communication across isolated domains, deterministic system design, and scalable debugging techniques.

---

## Research Focus

Modern automotive platforms integrate multiple operating systems (e.g., RTOS and Linux) on a single SoC under a hypervisor. These systems must coordinate while remaining isolated, creating challenges in communication, timing, and observability.

This repository investigates:

- Cross-OS communication using service-oriented middleware (SOME/IP)
- Deterministic system behavior through immutable RTOS image design
- Scalable debugging via automated log analysis

The goal is to analyze trade-offs between architectural choices and identify approaches to improve reliability and performance in safety-critical systems.

---

## System Perspective

This work explores three interconnected layers of automotive systems:

- **Communication** → Cross-domain IPC (SOME/IP, service-oriented design)  
- **System Design** → Deterministic RTOS behavior and image construction  
- **Observability** → Log analysis and anomaly detection  

These layers interact to determine overall system reliability:

- Communication affects latency and correctness  
- System design impacts determinism and safety  
- Observability enables debugging and validation  

---

## Architecture

```mermaid
graph LR
    subgraph Linux_Guest["Linux Guest"]
        A1[Client Application]
        A2[CommonAPI Proxy]
    end

    subgraph Virtual_Network["Virtual Ethernet"]
        V1[Bridge]
    end

    subgraph RTOS_Guest["RTOS Guest"]
        B1[CommonAPI Stub]
        B2[Service Implementation]
    end

    A1 --> A2
    A2 -->|SOME/IP| V1
    V1 -->|SOME/IP| B1
    B1 --> B2

    B2 -->|Event| B1
    B1 -->|SOME/IP| V1
    V1 -->|SOME/IP| A2
    A2 --> A1
