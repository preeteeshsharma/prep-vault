# Prep Plan: General Software Engineering Interview
**Budget:** 120 min over 7 days  
**Rounds:** Unknown — assessment across DSA, LLD, behavioral  
**Generated:** 2026-05-07

---

## Day 1 — Foundation & DSA (Warm-up)
**Budget today:** 20 min

### DSA: Two Pointers / Array Manipulation
- **Pattern / goal:** Strengthen fundamentals on array traversal and pointer management — a foundation for any technical round.
- **Approach:**
  - Solve **LeetCode #167: Two Sum II** (Input Array Is Sorted) — classic two-pointer drill.
  - Focus on in-place logic and early termination conditions.
- **Time:** 20 min

---

## Day 2 — DSA (Core Pattern)
**Budget today:** 20 min

### DSA: Hash Maps & Frequency Counting
- **Pattern / goal:** Build fluency with hash-based lookups — essential for interviews at most companies.
- **Approach:**
  - Solve **LeetCode #1: Two Sum** — canonical hash map problem.
  - Practice the trade-off: O(n) time vs. O(n) space; write both a nested-loop and hash solution.
- **Time:** 20 min

---

## Day 3 — DSA (Graph/Recursion)
**Budget today:** 20 min

### DSA: DFS & Recursion
- **Pattern / goal:** Handle tree/graph traversal and recursive decomposition — common in interviews.
- **Approach:**
  - Solve **LeetCode #104: Maximum Depth of Binary Tree** — simple DFS to build confidence.
  - Trace a call stack on paper; understand base case and recursive case clearly.
- **Time:** 20 min

---

## Day 4 — LLD (Object-Oriented Design)
**Budget today:** 25 min

### LLD: Library Management System
- **Pattern / goal:** Practice class hierarchy, mutable state, and single responsibility — foundational OO skills.
- **Approach:**
  - **Phase 1 (5 min):** Clarify scope — members, books, borrow/return, holds, fines. What's NOT included (payments, reservations)?
  - **Phase 2 (3 min):** Sketch data models — `Book`, `Member`, `BorrowRecord` as immutable value objects.
  - **Phase 3 (10 min):** Design `Library` class with methods `borrowBook()`, `returnBook()`, `addMember()`. Identify a bug: can you borrow a book twice? Use sealed interfaces to make invalid states unrepresentable.
  - **Phase 4 (5 min):** Trace a borrowing scenario end-to-end; handle the case when a book is already borrowed.
  - **Phase 5 (2 min):** How would you add late fees? Show the single method that changes.
- **Time:** 25 min

---

## Day 5 — Behavioral & Soft Skills
**Budget today:** 20 min

### Behavioral: Impact & Collaboration
- **Pattern / goal:** Develop crisp, story-driven answers to common themes — critical for any company.
- **Approach:**
  - **Story 1 (10 min):** "Tell me about a time you had to work with a difficult teammate." Use STAR (Situation, Task, Action, Result). Record yourself; aim for 90–120 seconds.
  - **Story 2 (10 min):** "Describe a project where you had to learn something new quickly." Show curiosity and adaptability.
  - Prepare for follow-ups: "What would you do differently?" and "What did you learn?"
- **Time:** 20 min

---

## Day 6 — DSA (Medium Difficulty)
**Budget today:** 20 min

### DSA: Sliding Window / Prefix Sums
- **Pattern / goal:** Handle contiguous subarray/substring problems — very common in phone screens.
- **Approach:**
  - Solve **LeetCode #209: Minimum Size Subarray Sum** — sliding window to optimize from O(n²) to O(n).
  - Draw the window pointers; understand why left pointer only moves right (monotonicity).
- **Time:** 20 min

---

## Day 7 — Review & Mock Interview
**Budget today:** 15 min

### Mixed: Timed DSA Drill + Behavioral Refresh
- **Pattern / goal:** Simulate interview conditions and identify any remaining gaps.
- **Approach:**
  - **DSA (8 min):** Solve **LeetCode #217: Contains Duplicate** under timed conditions. Hash set approach — should be fast and confident.
  - **Behavioral (7 min):** Record one more 90-second story. Listen for clarity, specificity, and a clear outcome.
  - Identify which pattern felt weakest; earmark it for post-interview follow-up if interview is still pending.
- **Time:** 15 min

---

## Weak areas to revisit
**None identified yet** — First session (Days 1–3) will surface specific DSA patterns where you lose time or confidence. After Day 4 (LLD), you'll know whether class design or data modeling needs reinforcement. Adjust Day 6–7 drills accordingly.

---

**Note:** This plan assumes a **general SWE interview** with DSA focus. Once you know the company and role:
- Add company-specific problems (e.g., Stripe → payment patterns; Google → graph/DP).
- Swap the LLD drill if the domain is different (fintech, infra, consumer product).
- Tailor behavioral stories to the company's values (e.g., ownership, bias for action, learning velocity).