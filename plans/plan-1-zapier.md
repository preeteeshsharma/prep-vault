# Prep Plan: Zapier — Unknown Role
**Budget:** 120 min over 7 days
**Rounds:** DSA, LLD, sysdesign, behavioral
**Generated:** 2026-05-07

---

## Day 1 — DSA: String Manipulation & Hash Maps
**Budget today:** 18 min

### DSA: Longest Substring Without Repeating Characters (#3)
- **Pattern / goal:** Sliding window over strings — core pattern for Zapier's text-processing and trigger-parsing problems.
- **Approach:**
  - Spend 5 min writing out the two-pointer window contract before coding: left pointer shrinks when a duplicate enters the window.
  - Implement using a `HashMap<char, index>` to O(1) detect and jump past duplicates — not just a Set.
  - After solving, mutate the problem: what if you allowed *k* repeated characters? Trace through #340 (Longest Substring with At Most K Distinct Characters) mentally to lock in the generalisation.
- **Time:** 18 min

---

## Day 2 — DSA: Hash Maps & Interval Logic
**Budget today:** 18 min

### DSA: Meeting Rooms II (#253)
- **Pattern / goal:** Interval merging / sweep line — Zapier's workflow scheduler deals heavily with overlapping task windows and concurrency limits.
- **Approach:**
  - Sort by start time; use a min-heap keyed on end times to track "rooms in use" (analogous to worker slots).
  - After coding, trace the concrete example `[[0,30],[5,10],[15,20]]` step by step on paper to verify heap pops and pushes.
  - Identify the invariant: heap size at any moment = minimum concurrent workers needed — connect this to Zapier's task queue depth.
- **Time:** 18 min

---

## Day 3 — LLD: Webhook Delivery System
**Budget today:** 17 min

### LLD: Webhook Delivery System
- **Pattern / goal:** Model Zapier's core delivery primitive — reliable, retryable, ordered event dispatch to external HTTP endpoints.
- **Approach:**
  - **Phase 1 — Requirements (3 min):** IN scope: register endpoints, deliver events, retry with exponential back-off, record delivery status. OUT scope: auth token rotation, fan-out to 1000s of subscribers.
  - **Phase 2 — Data Models (2 min):** `WebhookEndpoint` (id, url, secret, createdAt) as an immutable record; `DeliveryAttempt` (id, endpointId, payload, status: `PENDING | DELIVERED | FAILED`, attemptNumber, nextRetryAt) as a mutable class.
  - **Phase 3 — Class & Interface Design (5 min):** Name the pattern first — **Strategy + Retry Policy**. Define `interface DeliveryTransport { Result send(Attempt a); }` and `interface RetryPolicy { Duration nextDelay(int attempt); }`. Use a sealed interface for `DeliveryResult { record Success(); record Failure(int httpStatus, String body); }` to make unhandled states a compile error. Check SOLID: `RetryPolicy` is open for extension (exponential, linear, none) without touching `DeliveryWorker`.
  - **Phase 4 — Happy Path + Edge Cases (5 min):** Trace: event arrives → `DeliveryWorker` calls `transport.send()` → `Success` → mark `DELIVERED`. Edge: endpoint returns 429 → `Failure(429)` → `retryPolicy.nextDelay(attempt)` schedules re-queue. Edge: attempt 5 fails → status = `PERMANENTLY_FAILED`, emit a dead-letter event.
  - **Phase 5 — Extensibility (2 min):** New requirement — "add circuit breaker per endpoint." Show only `DeliveryWorker` changes: wrap `transport.send()` with a `CircuitBreaker` check; `RetryPolicy` and `DeliveryTransport` are untouched.
- **Time:** 17 min

---

## Day 4 — System Design: Workflow Automation Engine
**Budget today:** 17 min

### Sysdesign: Design Zapier's Workflow Automation Engine (Trigger → Action Pipeline)
- **Pattern / goal:** Design the core product — event ingestion, rule evaluation, and reliable task execution at scale.
- **Approach:**
  - **Requirements (2 min):** Users define Zaps (trigger + action steps). System must ingest webhook/poll triggers, evaluate filters, execute HTTP actions, and guarantee at-least-once delivery. Target: ~10M Zap executions/day.
  - **Capacity & API (2 min):** ~115 executions/sec avg; spike to ~1000/sec. API: `POST /triggers/{zapId}` (ingest), `GET /executions/{id}` (status). Each execution payload ~2 KB → ~20 MB/sec ingest.
  - **Data Model (2 min):** `Zap(id, ownerId, triggerConfig, steps[])`, `Execution(id, zapId, status, payload, createdAt, updatedAt)`, `StepResult(executionId, stepIndex, httpStatus, responseBody)`.
  - **Core Components (5 min):** Trigger Ingestor → Kafka topic `zap.triggers` → Execution Planner (resolves steps, writes `Execution` row) → Task Queue (Redis + worker pool) → HTTP Action Executor → Result Writer. Kafka provides durable buffering between ingest spikes and worker capacity.
  - **Deep Dive: Retry & Idempotency (4 min):** Workers claim tasks with a visibility timeout (like SQS). On action HTTP failure: exponential back-off, max 5 retries, then dead-letter. Idempotency: execution ID is passed as `X-Zap-Execution-Id` header so downstream services can deduplicate. Zap filter evaluation is stateless and CPU-cheap → scale horizontally.
  - **Bottlenecks (2 min):** Hot Zaps (viral triggers) → per-zap rate limiting at ingestor. DB write amplification on `StepResult` → batch-write or use append-only event log. Worker starvation → priority queue lanes (paid tier vs free tier).
- **Time:** 17 min

---

## Day 5 — DSA: Two Pointers & Graph Traversal
**Budget today:** 17 min

### DSA: Number of Islands (#200)
- **Pattern / goal:** BFS/DFS graph traversal on a grid — maps to Zapier's dependency graph traversal when resolving multi-step Zap execution order.
- **Approach:**
  - Implement iterative BFS (not recursive DFS) first — it avoids stack overflow on large grids and is closer to a real task-graph traversal in production.
  - Use a `visited` set of `(row, col)` tuples rather than mutating the input — practice the non-destructive pattern.
  - After solving, extend mentally: what if cells had weights (latency)? Connect to Dijkstra's — this bridges to sysdesign thinking about step execution ordering.
- **Time:** 17 min

---

## Day 6 — DSA: Sliding Window + Behavioral
**Budget today:** 17 min

### DSA: Minimum Window Substring (#76)
- **Pattern / goal:** Sliding window with frequency map — mirrors filtering/matching logic in Zapier's trigger condition evaluation over streaming event payloads.
- **Approach:**
  - Maintain two maps: `need` (target char counts) and `window` (current counts); advance right pointer until `formed == required`, then contract left.
  - Write the invariant as a comment before coding: *"window is valid iff all chars in `need` are satisfied."*
  - Test edge cases: `t` longer than `s` (return `""`), all same characters, single character target.
- **Time:** 10 min

### Behavioral: Impact & Cross-Team Collaboration
- **Pattern / goal:** Surface concrete stories aligned with Zapier's async-first, high-ownership remote culture.
- **Approach:**
  - **Story 1 — Impact (90 sec):** Prep a STAR story where *you* drove a measurable outcome without being asked (quantify: latency reduced X%, users unblocked, revenue saved). Zapier values self-directed impact.
  - **Story 2 — Cross-