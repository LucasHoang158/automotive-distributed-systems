# 🧠 Blog 1

## automotive_as_distributed_system.md

````md
# Automotive Systems as Distributed Systems: A Formal Perspective

## Abstract
Modern vehicles are evolving into distributed cyber-physical systems composed of heterogeneous compute nodes communicating over mixed-criticality networks. This article formalizes automotive architectures—focusing on IVI and OTA subsystems—using distributed systems theory. We define a system model, communication abstractions, and consistency/failure properties, and derive design implications for reliable OTA pipelines under real-time constraints.

---

## 1. Problem Statement & Thesis

**Thesis.** Automotive OTA systems should be modeled as distributed systems with explicit state machines to ensure correctness and reliability under real-time and safety constraints.

We study a system comprising nodes {HU1, HU3, HMI} interacting via CAN (low-level) and RSI/REST/WebSocket (service layer). The goal is to maintain **consistent update state** while executing a multi-phase OTA workflow.

---

## 2. System Model

### 2.1 Nodes and Roles
- **HU1**: source of truth for update availability and ECU state
- **HU3**: execution node (download + installation)
- **HMI**: observer/controller (user-triggered actions)

We define the system as a tuple:

\[
\mathcal{S} = (N, C, \Sigma, T)
\]

Where:
- \(N\): set of nodes
- \(C\): communication channels (CAN, RSI)
- \(\Sigma\): global system states
- \(T\): transition relation

---

### 2.2 Communication Channels

**CAN (deterministic bus)**
- bounded latency, broadcast semantics
- limited payload, prioritized arbitration

**RSI/REST (service layer)**
- request/response, stateless interactions

**WebSocket (event stream)**
- push-based updates, pub/sub semantics

---

## 3. Formal State Representation

Let each node \(n_i \in N\) maintain a local state \(s_i \in \Sigma_i\).

The **global state** is:
\[
\Sigma = \Sigma_{HU1} \times \Sigma_{HU3} \times \Sigma_{HMI}
\]

Consistency requires:
\[
\forall i,j: f(s_i) = f(s_j)
\]
for a projection \(f\) over update status.

---

## 4. Consistency Model

We consider two models:

### Strong Consistency
- All nodes observe identical state simultaneously
- Not feasible due to network delays and asynchronous execution

### Eventual Consistency (adopted)
- Nodes converge to a consistent state over time

**Implication:**
- Temporary divergence is allowed
- System must guarantee convergence

---

## 5. Failure Model

We define failures as:

- **Crash faults**: node stops responding (HU3 reboot)
- **Omission faults**: lost CAN messages
- **Timing faults**: delayed updates (network jitter)

We assume:
- no Byzantine behavior
- bounded message delay

---

## 6. Invariants (Safety Properties)

We define key invariants:

1. **No Install Before Download**
\[
\neg (state = INSTALLING \land \text{download\_complete} = false)
\]

2. **Single Active Update**
\[
\forall t: |active\_updates(t)| \le 1
\]

3. **Monotonic Progress (except failure)**
\[
state_{t+1} \ge state_t
\]

---

## 7. Architecture Diagram

```mermaid
graph TD
    HU1[HU1: Source of Truth]
    HU3[HU3: Execution Node]
    HMI[HMI: Observer]
    CS[CarService]

    HU1 -->|CAN| CS
    CS --> HU3
    HU3 -->|RSI| HMI
    HMI -->|User Action| HU3
````

---

## 8. Sequence (OTA Initiation)

```mermaid
sequenceDiagram
    participant HU1
    participant CS
    participant HU3
    participant HMI

    HU1->>CS: Update Available (CAN)
    CS->>HU3: Forward state
    HU3->>HMI: Notify via RSI
    HMI->>HU3: User confirms download
```

---

## 9. Design Implications

* Prefer **eventual consistency with validation checks**
* Use **explicit state machines** for coordination
* Separate **control plane (RSI)** and **data plane (CAN)**
* Design for **failure recovery and idempotency**

---

## 10. Conclusion

Viewing automotive OTA systems as distributed systems provides a rigorous framework for reasoning about correctness, consistency, and reliability. This foundation enables formal verification and scalable system design for next-generation software-defined vehicles.

````

---
