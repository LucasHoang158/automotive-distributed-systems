# Research Notes

This is not a formal research project (yet), but a set of questions that came out of real system work.

---

## 1. Boot-time determinism

I ran into a case where a “fast” service was actually delayed by storage.

Moving it into IFS fixed it.

That raises a bigger question:

- Can we reason about boot timing *before* running the system?

Right now, most of it is trial-and-error.

---

## 2. Cross-OS communication

QNX and Android behave very differently.

- QNX expects determinism  
- Android does not guarantee it  

So any interface between them becomes a weak point.

Question:

- Can we bound latency across OS boundaries?

---

## 3. IPC trade-offs

Tried multiple approaches:

- sockets → simple but sometimes slow  
- shared memory → fast but tricky  

There is no perfect solution.

So:

- Can we combine both without making the system messy?

---

## 4. Observability

Most failures I saw:

- didn’t crash  
- didn’t throw errors  
- just… behaved wrong  

Logs were the only clue.

Question:

- Can logs be turned into something closer to a “signal” instead of noise?

---

## Direction

All of this points to one idea:

Determinism is not a property of a single component.

It’s a property of the whole system.
