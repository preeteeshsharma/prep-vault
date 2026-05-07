# Prep Plan: General SWE Interview — Full-Stack Competency
**Budget:** 420 min over 7 days
**Rounds:** DSA, LLD, System Design, Behavioral
**Generated:** 2026-05-07

---

## Day 1 — DSA Foundations & Problem Solving
**Budget today:** 60 min

### DSA: Two Sum (LeetCode 1)
- **Pattern / goal:** Hash map lookups for O(n) solutions; avoid brute force.
- **Approach:**
  - Solve brute force first (nested loop), then optimize with single-pass hash map.
  - Write clean code; trace through 2–3 test cases including duplicates and negative numbers.
  - Explain time/space tradeoffs aloud.
- **Time:** 60 min

---

## Day 2 — DSA Pattern Drilling
**Budget today:** 60 min

### DSA: Best Time to Buy and Sell Stock (LeetCode 121)
- **Pattern / goal:** Single-pass greedy with state tracking; handles constraints naturally.
- **Approach:**
  - Walk through the greedy invariant: track min price so far, max profit so far.
  - Code the O(n) solution in 15 min; trace a 5–element array by hand.
  - Discuss why greedy works (no future information needed).
- **Time:** 60 min

---

## Day 3 — LLD Fundamentals
**Budget today:** 60 min

### LLD: Parking Lot System
- **Pattern / goal:** Object-oriented design with state machines; SOLID principles.
- **Approach:**
  - **Phase 1 (5 min):** Clarify scope — levels, spots, vehicle types, payment.
  - **Phase 2 (3 min):** Data model — Vehicle (immutable VO), ParkingSpot (mutable state).
  - **Phase 3 (15 min):** Design ParkingLot, Level, Spot, Ticket classes; use enum for spot status.
  - **Phase 4 (10 min):** Code parkVehicle() → findAvailableSpot() → updateSpot(); trace one reservation.
  - **Phase 5 (5 min):** Show how to add a new vehicle type (only VehicleType enum changes).
- **Time:** 40 min

### Behavioral: Quick Self-Inventory
- **Pattern / goal:** Identify 5–6 strong STAR stories you can tell in 90–120 sec each.
- **Approach:**
  - List one conflict, one failure, one technical impact, one cross-team collaboration, one learning.
  - Write a 1-line summary for each.
- **Time:** 20 min

---

## Day 4 — DSA + System Design Intro
**Budget today:** 60 min

### DSA: Merge Intervals (LeetCode 56)
- **Pattern / goal:** Interval merging; sorting + single pass.
- **Approach:**
  - Sort by start time; merge overlapping intervals in one pass.
  - Code in 20 min; test edge cases (no overlap, complete containment, adjacent).
  - State the condition for overlap clearly: `intervals[i].start <= intervals[i-1].end`.
- **Time:** 60 min

---

## Day 5 — System Design + LLD
**Budget today:** 60 min

### System Design: URL Shortener
- **Pattern / goal:** Distributed ID generation, key-value store design, lookup performance.
- **Approach:**
  - **Requirements:** Shorten long URLs, redirect via short key, handle scale (1M URLs/day).
  - **Capacity:** ~1M writes/day, 100M reads/day; QPS ≈ 1250 write, 1250 read.
  - **API:** POST /shorten (long_url) → {short_url}; GET /{code} → redirect.
  - **Data model:** {code, long_url, created_at, expiry}.
  - **Components:** Load balancer → API gateway → hash/encoding service → KV store (Redis) → SQL for persistence.
  - **Deep dive:** Collision handling (hash collisions, retry with new seed); caching strategy (hot codes in Redis).
  - **Bottlenecks:** ID collision, Redis capacity, redirect latency.
- **Time:** 60 min

---

## Day 6 — Behavioral + LLD
**Budget today:** 60 min

### Behavioral: STAR Story Drills (Impact + Conflict)
- **Pattern / goal:** Tell two compelling stories in 90–120 sec each; practice recovery from vague answers.
- **Approach:**
  - **Story 1 (impact):** Pick a time you shipped a feature that measurably improved something (latency, reliability, user adoption). State the before/after metric.
  - **Story 2 (conflict):** Pick a disagreement with a teammate over design. Walk through your position, theirs, and how you resolved it.
  - Record yourself or speak aloud 2× to polish pacing and detail.
- **Time:** 20 min

### LLD: Rate Limiter (Token Bucket)
- **Pattern / goal:** Concurrency, sliding windows, state consistency.
- **Approach:**
  - **Phase 1 (5 min):** Requirements — limit API calls per user per window (e.g. 100 req/min).
  - **Phase 2 (3 min):** Data: {userId, tokens, last_refill_time}.
  - **Phase 3 (15 min):** Design RateLimiter class, allowRequest(userId, tokens_needed) with lock/atomic ops.
  - **Phase 4 (10 min):** Implement refill logic (tokens += elapsed_sec × rate); trace a burst scenario.
  - **Phase 5 (5 min):** Show how to add a new strategy (distributed rate limiter) — swap the backend store.
- **Time:** 40 min

---

## Day 7 — Mock Interview & Final Review
**Budget today:** 60 min

### DSA: Longest Substring Without Repeating Characters (LeetCode 3)
- **Pattern / goal:** Sliding window with hash map; two pointers.
- **Approach:**
  - Build window left-to-right; expand right pointer, shrink left when char repeats.
  - Code in 25 min; trace "abcabcbb" by hand to verify window correctness.
- **Time:** 60 min

---

## Weak areas to revisit
None identified yet — first session will surface these. After Day 1–2, revisit this plan:
- If DSA solutions are slow (>45 min), spend Day 6 on array/hash map fundamentals.
- If LLD designs feel disorganized, use the 5-phase framework more deliberately.
- If system design capacity math is fuzzy, drill estimation formulas on Day 5.

---

## Next Steps
1. **Day 1:** Solve Two Sum cleanly; time yourself.
2. **After each round:** Note which phase (DSA pattern, LLD data model, sysdesign bottleneck) felt weakest.
3. **Day 7 evening:** Pick one weak pattern from the week and schedule a follow-up 30-min drill before the actual interview.