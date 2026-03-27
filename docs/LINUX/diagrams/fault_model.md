
---
# Fault Model for Automotive OTA Systems

## Overview

This document defines the failure model for OTA systems in automotive environments.

---

## Fault Classification

```mermaid
graph TD
    F[Failure]

    F --> NF[Non-Fatal]
    F --> FT[Fatal]

    NF --> B[Battery Low]
    NF --> C[Charging Active]
    NF --> P[Parking Condition Violated]

    FT --> E[ECU Crash]
    FT --> U[Update Corruption]
```

## Failure Types

### Non-Fatal Failures

**Characteristics:**
- Temporary
- Recoverable

**Examples:**
- Battery low
- Charging state
- Unsafe vehicle condition

**Handling:**
- Pause execution
- Retry after recovery

---

### Fatal Failures

**Characteristics:**
- Critical
- Not recoverable at runtime

**Examples:**
- ECU crash
- Corrupted update package

**Handling:**
- Abort process
- Require manual intervention

---

## Failure Timeline

```mermaid
sequenceDiagram
    participant HU3
    participant System

    HU3->>System: Start Installation
    System-->>HU3: Battery Low
    HU3->>HU3: Pause
    HU3->>System: Retry
```
---

## Design Implications

- Distinguish between recoverable and unrecoverable faults
- Support retry for non-fatal failures
- Enforce safe abort for fatal failures

---

## Distributed System Perspective

This fault model aligns with classical distributed system failure types:

- Crash faults
- Omission faults
- Timing faults

---

## Conclusion

A well-defined fault model is essential for:

- Reliable OTA systems
- Predictable system behavior
- Safe recovery strategies
