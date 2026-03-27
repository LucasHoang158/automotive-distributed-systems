# Fault Tolerance and Real-Time Constraints in Automotive OTA Systems
## 1. Problem Statement

Unlike cloud systems, automotive systems must handle:
- Real-time deadlines
- Safety-critical failures
- Limited resources

---

## 2. Failure Model

### Non-Fatal Failures
- Battery low
- Charging active
- Parking state violation

### Fatal Failures
- ECU crash
- Update corruption

---

## 3. Retry and Recovery Strategy

Non-fatal failures allow retry:
- State reset
- Re-trigger installation

Fatal failures require:
- Workshop intervention
- Manual recovery

---

## 4. Real-Time Constraints

Key constraints:
- Update must not block critical vehicle functions
- Latency must be bounded

Techniques:
- Multithreading
- Asynchronous execution

---

## 5. Consistency Under Failure

System must maintain:
- Valid state across HU1, HU3, HMI

Potential issue:
- Partial updates
- Inconsistent states

---

## 6. Design Implications

- Prefer eventual consistency with validation
- Ensure rollback capability
- Separate critical and non-critical updates

---

## 7. Conclusion

Fault tolerance in automotive OTA systems requires balancing distributed system principles with real-time safety constraints.
