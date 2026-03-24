# Automotive Distributed Systems Research

This repository contains a collection of technical explorations in automotive embedded systems, focusing on cross-OS communication, real-time system design, and reliability tooling.

## Topics Covered

### 1. Cross-OS Communication (SOME/IP)
- Service-oriented IPC between RTOS and Linux guests
- CommonAPI abstraction
- Trade-offs vs shared memory

👉 docs/someip-cross-vm.md

---

### 2. Immutable RTOS Image Design
- Deterministic boot
- Reproducible builds
- System integrity

👉 docs/rtos-image.md

---

### 3. Log Analysis & Automated Detection
- Pattern-based anomaly detection
- Heuristic rules for embedded logs
- Tooling for debugging at scale

👉 docs/log-analysis.md

---

## Motivation

Modern automotive systems require reliable communication across isolated domains, deterministic system behavior, and scalable debugging approaches.  

This repository explores these challenges from a system-level perspective.

---

## Future Work

- Shared memory IPC vs SOME/IP benchmarking
- Deterministic scheduling analysis
- Real-time log monitoring system

---

## Author

Embedded systems engineer focused on real-time platforms, automotive middleware, and system reliability.
