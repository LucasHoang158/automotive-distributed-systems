# Automotive Distributed Systems

## Overview

This repository explores the design of modern automotive software systems as **distributed systems running on embedded operating systems**.

The work is centered around a **camera-oriented pipeline** (similar to IVI / ADAS systems), implemented through a series of experiments on QNX and Linux-based environments.

Rather than building a monolithic application, this repository investigates:

- distributed communication between components
- multi-process system design
- data flow across system boundaries
- OTA (Over-The-Air) update mechanisms
- system reliability under failure conditions

---

## Motivation

Modern automotive systems (e.g., camera, IVI, ADAS) are no longer single processes.

They are **distributed, concurrent, and safety-critical systems** composed of:

- multiple processes
- asynchronous communication
- real-time constraints
- strict reliability requirements

This repository is a step toward understanding and designing such systems from both:

- **distributed systems perspective**
- **operating system (Linux/QNX) perspective**

---

## System Direction

The target system follows a pipeline architecture:

Camera Input → Processing → Rendering → Output

Each stage is designed as an independent process.

Communication between components is handled through middleware (e.g., vsomeip) or system-level interfaces.

---

## Repository Structure

Each directory represents a focused experiment:

- communication (e.g., vsomeip-based interaction)
- process separation (multi-process design)
- rendering (EGL-based output)
- data flow (pipeline behavior)

These components are intentionally loosely coupled, allowing exploration of individual system concerns.

---

## Key Concepts Explored

### 1. Distributed Systems in Automotive

- system modeled as interacting nodes
- asynchronous communication (CAN, REST, middleware)
- eventual consistency of system state

### 2. OTA Update Systems

- formal state machine (FSM)
- safety invariants and correctness
- fault handling and recovery

### 3. Linux / QNX System Perspective

- process lifecycle and scheduling
- concurrency and synchronization
- file system consistency and atomic updates

---

## Technologies

- **C++**
- **QNX (target embedded OS)**
- **Linux (system-level experiments)**
- **vsomeip (middleware communication)**
- **EGL (rendering pipeline)**

---

## Research Direction

This repository evolves toward a unified research theme:

> **Distributed Systems for Automotive under OS-Level Constraints**

It combines:

- distributed coordination
- real-time constraints
- fault tolerance
- operating system behavior

See [`research.md`](./research.md) for a formal research perspective.

---

## Status

This is an **ongoing experimental repository**.

The components are not fully integrated yet.  
Each module is a step toward a larger system.

---

## Future Work

- fault-tolerant OTA system design
- formal verification (FSM, invariants)
- integration of distributed pipeline
- real-time scheduling analysis
