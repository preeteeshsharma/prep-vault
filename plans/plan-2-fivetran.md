# Prep Plan: Fivetran — Senior Software Engineer
**Budget:** 120 min over 7 days
**Rounds:** DSA
**Generated:** 2026-05-07

---

## Day 1 — Dynamic Programming Foundations
**Budget today:** 20 min

### DSA: LeetCode 300 — Longest Increasing Subsequence
- **Pattern / goal:** Classic DP with overlapping subproblems; Fivetran has explicitly asked this in recent interviews.
- **Approach:**
  - Start by sketching the decision tree: for each element, include/exclude it and recur on remaining.
  - Identify overlapping subproblems (state: current index + previous element value).
  - Build bottom-up DP table: `dp[i]` = longest subsequence ending at index `i`.
  - Optimize to O(n log n) using binary search + patience sorting (bonus, not required).
- **Time:** 60 min

---

## Day 2 — Graph Traversal & DAG Problems
**Budget today:** 20 min

### DSA: LeetCode 207 — Course Schedule (Topological Sort on DAG)
- **Pattern / goal:** Detecting cycles in directed acyclic graphs; Fivetran interviewed on DAG-based problems in Round 1.
- **Approach:**
  - Model the problem as a directed graph: course → prerequisite edge.
  - Use DFS with three states (unvisited, visiting, visited) to detect back edges (cycle = impossible schedule).
  - Alternatively, use Kahn's algorithm (in-degree based topological sort).
  - Walk through a concrete example: `[1,0], [0,1]` (cycle detected) vs `[1,0]` (valid).
- **Time:** 60 min

---

## Day 3 — Graph Traversal & Medium Difficulty
**Budget today:** 20 min

### DSA: LeetCode 133 — Clone Graph
- **Pattern / goal:** Graph traversal (BFS/DFS) with state tracking; Fivetran reports "1 LC medium question based on graph traversal" in Round 1.
- **Approach:**
  - Use DFS or BFS; maintain a hash map of original → cloned node to avoid cycles and revisits.
  - Key insight: when you visit a node, immediately create its clone and map it before exploring neighbors.
  - Trace through a connected component: verify all edges are cloned correctly.
  - Practice both BFS (queue) and DFS (recursion) implementations.
- **Time:** 60 min

---

## Day 4 — Greedy & Problem Variant Understanding
**Budget today:** 20 min

### DSA: LeetCode 134 — Gas Station
- **Pattern / goal:** Greedy algorithm; Fivetran asked a variant called "Aladdin and the Magic Carpet" (conceptually Gas Station). Understanding the greedy insight is critical.
- **Approach:**
  - Greedy insight: if total gas ≥ total cost, a solution exists; iterate once to find the start position.
  - Track cumulative balance; whenever it goes negative, reset starting point (the current station cannot be the start).
  - Prove why this greedy choice is optimal: if you can't reach station `j` from station `i`, you can't reach it from any station between `i` and `j` either.
  - Implement and trace: `gas = [1,2,3,4,5], cost = [3,4,5,1,2]` → start at index 3.
- **Time:** 60 min

---

## Day 5 — Binary Search Depth Drill
**Budget today:** 20 min

### DSA: LeetCode 153 — Find Minimum in Rotated Sorted Array
- **Pattern / goal:** Binary search on sorted array variant; Fivetran's Glassdoor report mentions "Question based on Binary Search" in coding round.
- **Approach:**
  - Identify the invariant: one half is always sorted; use it to eliminate half of the search space.
  - Handle the edge case: when `nums[mid] == nums[right]`, you cannot determine which side is sorted; shrink the right boundary.
  - Walk through rotations: `[3,4,5,1,2]` and `[2,1]` to cement the binary search logic.
  - Time complexity must be O(log n) average, O(n) worst-case (when duplicates force sequential scan).
- **Time:** 60 min

---

## Day 6 — DP Variation & Requirement Extension
**Budget today:** 20 min

### DSA: LeetCode 188 — Best Time to Buy and Sell Stock IV
- **Pattern / goal:** DP with constraint; Fivetran reports "dynamic programming coding question with requirement extension on completion" — practice DP that can be quickly extended.
- **Approach:**
  - State: `dp[k][i][0/1]` = max profit with at most `k` transactions by day `i`, currently holding (1) or not holding (0) stock.
  - Optimize space: use 2D DP if `k` is large (fold the day dimension).
  - Extension readiness: be prepared to explain how the solution changes if a transaction has a fee, or cooldown period, or fractional shares.
  - Code once cleanly; then verbally walk through modifications for new constraints.
- **Time:** 60 min

---

## Day 7 — Mixed Difficulty Review & Mock
**Budget today:** 20 min

### DSA: LeetCode 199 — Binary Tree Right Side View (Medium, DFS/BFS variant)
- **Pattern / goal:** Tree traversal with level-order logic; reinforces graph/tree patterns under time pressure.
- **Approach:**
  - Use BFS (queue) to traverse level-by-level; collect the last node of each level.
  - Alternatively, DFS (pre-order) with depth tracking: record the first node visited at each depth (right-first traversal).
  - This is a "warm-up" problem to refresh tree/graph intuition before your interview.
  - Time yourself: aim for solution + explanation in under 35 min.
- **Time:** 60 min

---

## Weak areas to revisit

None identified yet — your interview will surface specific weak patterns. **Recommended triage:**

1. **If you struggle with DP:** prioritize Days 1 and 6; replay LeetCode 300 and 188 before interview day.
2. **If graph traversal is shaky:** replay Days 2, 3, and 7; ensure you can write DFS/BFS from scratch in under 10 min.
3. **If you time out on any drill:** after completion, re-solve it the next day with a 20-minute hard stop to build speed.

---

## Interview Week (2026-05-14)
- **Day before (May 13):** Replay LeetCode 300 (LIS) and 134 (Gas Station) — both confirmed Fivetran patterns.
- **Day of:** Arrive 10 min early. You'll face ~1–2 DSA problems on HackerRank in 45–60 min. All test cases must pass. Expect one problem from {DP, Graph, Greedy, or Binary Search}. **You are ready.**