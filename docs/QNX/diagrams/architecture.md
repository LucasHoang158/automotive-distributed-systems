# System Architecture

## Overview

The system is organized around a camera application.

It is not fully implemented yet.  
Instead, it is split into multiple small experiments.

Each experiment represents one part of the system.

## Target Architecture (Concept)

+-------------------+
| Camera Input |
+-------------------+
|
v
+-------------------+
| Processing |
| (Image pipeline) |
+-------------------+
|
v
+-------------------+
| Rendering |
| (EGL / Display) |
+-------------------+


In a real system, each block can run in a separate process.

## Current Implementation Style

Instead of one full system, the repo contains:

- small modules
- separate binaries
- independent experiments

Some modules already simulate:
- communication between processes
- service-based interaction

## Communication Layer

vsomeip is used in some experiments.

It allows:
- sending requests between modules
- publishing events

Example:

Processing → event → Rendering
or
Rendering → request → Processing


## Execution Model

- multi-process on one machine
- each module can run independently
- communication via vsomeip (socket-based)

This is close to how QNX systems are structured.

## Design Idea

### Why split into topics?

- easier to test one idea at a time
- avoids large and complex system early
- helps understanding each part clearly

### Why multi-process?

- closer to real automotive systems
- better isolation
- easier to extend later

### Why camera as target?

- simple but realistic use case
- includes:
  - data input
  - processing
  - rendering
  - communication

## Limitations

- modules are not fully connected
- no unified data model
- no synchronization between stages
