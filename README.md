# Automotive Distributed Systems (QNX + Android)

This repo comes from a simple but annoying problem I kept hitting while working on an automotive platform:

Things look fine in isolation, but once QNX and Android run together under a hypervisor, timing and behavior become unpredictable.

---

## What this is about

The system I worked on has:

- QNX (real-time, safety-critical)
- Android (UI, applications)
- A hypervisor separating the two

They share the same SoC, but not the same assumptions.

That’s where problems start.

---

## The real problem

Not performance. Not features.

**Determinism.**

- A service starts “early” — but actually waits for storage  
- A message is “fast” — until Android gets busy  
- A system “works” — but you can’t explain why it failed once  

This repo is about understanding and fixing those kinds of problems.

---

## What I explored

Instead of one big solution, I ended up working on three different layers:

### 1. Boot timing (QNX side)

Moving critical services into IFS changed boot behavior completely.

Not just faster — **predictable**.

→ docs/qnx-ifs-boot-optimization.md

---

### 2. QNX ↔ Android interface

Tried different approaches. Some looked clean on paper, but broke under load.

Ended up with a design that favors:

- non-blocking behavior
- strict validation
- explicit state handling

→ docs/qnx-android-interface-architecture.md

---

### 3. Debugging reality (logs)

A lot of issues never show up as “failures”.

They sit in logs.

So I built a small detector to surface patterns automatically.

→ docs/robotframework-log-detection.md

---

## How these connect

Boot timing → affects when services exist

Communication → affects how they interact

Logs → explain when things go wrong


None of them works alone.

---

## Why this matters

In automotive systems:

- You don’t just need it to work  
- You need it to behave the same way every time  

That’s much harder than it sounds once multiple OSes are involved.

---

## Notes

All details are anonymized, but the problems and solutions are real.

---

## Author

Embedded engineer working on Linux, QNX, Android, and system integration.
