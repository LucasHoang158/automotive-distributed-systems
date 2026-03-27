# System Perspective

## Context

In modern automotive systems, applications are no longer monolithic.

A camera system, for example, involves:
- data acquisition
- image processing
- rendering
- communication between components

These parts are often separated into different processes.

On QNX, this design is common due to:
- reliability
- isolation
- real-time requirements

## Problem

Building a full system directly is difficult.

Challenges include:
- complex communication
- synchronization between modules
- performance constraints

At the same time, studying only small code samples is not enough.

There is a need for a middle step:
- not too simple
- not too complex

## Approach

This repository takes an incremental approach.

Instead of building the full camera system at once:
- each part is explored separately
- each topic focuses on one idea

Examples:
- inter-process communication
- service-based interaction
- data flow between modules

These experiments are loosely connected.

## Why Camera System

The camera system is used as a reference.

It provides a clear structure:
- input → process → output

It is also relevant for:
- ADAS
- driver assistance
- HMI integration

## Distributed Aspect

Even on a single machine, the system behaves like a distributed system.

Reasons:
- multiple processes
- message-based communication
- asynchronous behavior

This allows studying:
- latency between modules
- communication overhead
- coupling between components

## Design Trade-offs

### Incremental vs Integrated

The system is not fully integrated yet.

This reduces complexity, but:
- limits end-to-end testing
- makes global optimization harder

### Realism vs Simplicity

Using vsomeip brings the design closer to real automotive systems.

However:
- not all features are implemented
- behavior is simplified

### Control vs Real Deployment

Running on one machine:
- easier to debug
- easier to measure

But:
- does not reflect full network conditions

## Research Value

Even with a simple setup, several aspects can be studied:

- process separation overhead
- communication latency
- module interaction patterns

This can serve as a base for:

- performance evaluation
- middleware design
- system architecture decisions

## Future Direction

Possible next steps:

- connect modules into a full pipeline
- introduce timing constraints
- simulate failures between modules
- evaluate different communication methods

## Conclusion

This work is not a finished system.

It is a structured exploration of how a real automotive application can be built.

The focus is on:
- understanding system behavior
- testing design ideas
- preparing for more complex implementations
