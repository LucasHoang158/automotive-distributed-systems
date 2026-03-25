# Research Notes

## 1. Background

Automotive software is becoming more complex, especially for applications like camera systems.

A typical camera system is not a single program.  
It includes several parts:
- data input from sensor
- processing pipeline
- rendering to display
- communication with other components

In modern systems, these parts are often separated into different processes.

On QNX, this approach is common because it improves:
- isolation
- stability
- maintainability

## 2. Problem Statement

Building a full camera system directly is difficult.

Some challenges:
- communication between processes
- data flow management
- latency between stages
- system complexity grows quickly

At the same time, using a full framework (like AUTOSAR Adaptive) is heavy and hard to study.

So there is a gap:
- simple examples are too small
- real systems are too complex

## 3. Research Approach

This project takes a step-by-step approach.

Instead of building a full system:
- each part is explored separately
- each topic focuses on one idea

Examples of topics:
- inter-process communication using vsomeip
- simple service interaction
- basic pipeline structure
- process-level separation

These experiments are not fully connected, but they follow the same direction.

## 4. System View

The reference system is a camera pipeline:
Input → Processing → Rendering


Each stage can run as a separate process.

Communication between stages can use:
- message passing
- service-oriented communication

This creates a distributed behavior, even on a single machine.

## 5. Key Questions

This research tries to answer some practical questions:

- How should modules communicate in a QNX system?
- What is the cost of process separation?
- How much latency is added by middleware?
- How tightly should modules be coupled?

These questions are important for real automotive systems.

## 6. Design Choices

### Multi-process model

Each module runs independently.

Reason:
- closer to real system design
- better isolation
- easier to test individual parts

### Use of vsomeip

vsomeip is used in some experiments.

Reason:
- common in automotive systems
- supports service-based communication
- simple enough to experiment with

### Incremental development

The system is not built all at once.

Instead:
- small parts are tested first
- integration comes later

## 7. Observations (Early Stage)

From initial experiments, some points can be seen:

- communication between processes is not free
- message-based systems add overhead
- simple designs are easier to debug

Even basic setups already show:
- latency between modules
- dependency between components

## 8. Limitations

Current work has some limitations:

- no full pipeline yet
- limited synchronization between modules
- no strict timing control
- no fault handling

This is expected at this stage.

## 9. Future Work

Next steps may include:

- connect all modules into one pipeline
- measure latency across stages
- compare different communication methods
- test on real QNX target
- add basic fault scenarios

## 10. Conclusion

This project is not about building a final product.

It is about understanding how a real system can be built.

By splitting the problem into smaller parts,  
it becomes easier to study and improve each part.

This work can be a base for:
- deeper system design
- performance evaluation
- future research (PhD level)
