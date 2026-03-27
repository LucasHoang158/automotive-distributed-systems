# Research Direction: Distributed Systems for Automotive

## Abstract

This repository investigates automotive software systems as **distributed systems operating under operating system constraints**. The focus is on OTA mechanisms, camera pipelines, and inter-process communication, with experiments conducted on QNX and Linux environments.

---

## 1. Problem Statement

Modern automotive systems (IVI, ADAS, camera systems) exhibit characteristics of:

- distributed systems
- real-time systems
- safety-critical systems

However, their design is often fragmented across:

- application-level logic
- middleware communication
- operating system behavior

This research aims to **unify these layers into a coherent system model**.

---

## 2. System Model

We model the automotive system as:

$$
\mathcal{S} = (N, C, \Sigma, T)
$$

Where:

- $N$: set of nodes (ECUs, IVI units, HMI)
- $C$: communication channels (CAN, middleware, REST)
- $\Sigma$: global system state space
- $T$: state transition relation

---

## 3. OTA as a Distributed System

OTA updates are modeled as a **finite state machine (FSM)**:

States:
- IDLE
- AVAILABLE
- DOWNLOADING
- DOWNLOADED
- INSTALLING
- SUCCESS
- FAILED

Key properties:

### Safety
- no installation before download completes
- no invalid state transitions

### Liveness
- system eventually reaches SUCCESS or FAILED

---

## 4. Fault Model

Failures are categorized as:

### Non-Fatal
- recoverable
- retry-based handling

### Fatal
- system-critical
- require rollback or manual intervention

This aligns with distributed system fault models:

- crash faults
- omission faults
- timing faults

---

## 5. Linux / QNX System Perspective

Distributed correctness depends on OS-level behavior:

### Process Model
- multi-process architecture
- thread-based concurrency

### File System
- atomic updates
- crash consistency

### I/O
- CAN (SocketCAN)
- network stack (REST/WebSocket)

---

## 6. Cross-Layer Insight

A key observation:

> System correctness emerges from the interaction between distributed coordination and OS-level guarantees.

Examples:

- FSM correctness depends on process execution
- update safety depends on file system behavior
- fault recovery depends on OS restart mechanisms

---

## 7. Research Contributions (Ongoing)

This repository contributes:

- a system-level view of automotive OTA
- formal modeling of update processes
- integration of distributed and OS-level perspectives

---

## 8. Future Research Directions

- formal verification (LTL, TLA+)
- fault-tolerant state machines
- real-time scheduling constraints
- end-to-end system validation

---

## 9. Conclusion

Automotive systems should be treated as **distributed systems constrained by operating system behavior**. A unified approach is required to ensure correctness, reliability, and scalability.
