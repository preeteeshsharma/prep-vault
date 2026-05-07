# Prep Plan: Unknown — Unknown
**Budget:** 420 min over 7 days
**Rounds:** DSA
**Generated:** 2026-05-07

---

## Day 1 — Arrays & Hashing Fundamentals
**Budget today:** 60 min

### DSA: Two Sum (LeetCode 1)
- **Pattern / goal:** Hash map lookup for two-pointer equivalents; O(n) time, O(n) space tradeoff.
- **Approach:**
  - Solve via brute force (O(n²)), then optimize with hash map.
  - Trace through a concrete example: `[2, 7, 11, 15], target=9` → store seen values, check `target - num` on each pass.
  - Discuss space/time tradeoffs; when to use hash map vs. sorting.
- **Time:** 60 min

---

## Day 2 — Sliding Window & Prefix Sums
**Budget today:** 60 min

### DSA: Maximum Subarray (LeetCode 53)
- **Pattern / goal:** Kadane's algorithm; linear scan with state tracking (max ending here vs. max so far).
- **Approach:**
  - Solve via brute force (O(n²)), then derive Kadane's O(n) solution.
  - Trace `[-2, 1, -3, 4, -1, 2, 1, -5, 4]` step-by-step; understand why we reset when sum goes negative.
  - Discuss why greedy choice (drop prefix if sum < 0) is safe.
- **Time:** 60 min

---

## Day 3 — Linked Lists & Two Pointers
**Budget today:** 60 min

### DSA: Reverse Linked List (LeetCode 206)
- **Pattern / goal:** Pointer manipulation; in-place reversal; iterative vs. recursive.
- **Approach:**
  - Implement iterative version (three pointers: prev, curr, next); trace through a small list.
  - Implement recursive version; understand call stack and base case.
  - Discuss space complexity and why iterative is preferred in interviews.
- **Time:** 60 min

---

## Day 4 — Trees & DFS/BFS
**Budget today:** 60 min

### DSA: Binary Tree Level Order Traversal (LeetCode 102)
- **Pattern / goal:** BFS with queue; level-by-level collection; null handling.
- **Approach:**
  - Implement BFS using collections.deque or queue.Queue.
  - Trace through a balanced tree; understand how to group nodes by level (process entire queue per iteration).
  - Discuss when to use BFS vs. DFS; space complexity differences.
- **Time:** 60 min

---

## Day 5 — Strings & Dynamic Programming
**Budget today:** 60 min

### DSA: Longest Palindromic Substring (LeetCode 5)
- **Pattern / goal:** DP (bottom-up) vs. expand-around-center; O(n²) time both ways, O(n²) space for DP vs. O(1) for center expansion.
- **Approach:**
  - Implement expand-around-center (simpler, fewer edge cases); handle even/odd length palindromes.
  - Trace through `"babad"` and `"cbbd"` to see both cases.
  - Discuss why DP table approach works; why it's harder to implement correctly.
- **Time:** 60 min

---

## Day 6 — Graphs & Backtracking
**Budget today:** 60 min

### DSA: Number of Islands (LeetCode 200)
- **Pattern / goal:** DFS/BFS on implicit grid graph; connected components; visited state tracking.
- **Approach:**
  - Implement DFS (recursive, simpler to code) over BFS.
  - Trace through a 2D grid with islands separated by water; mark visited cells in-place.
  - Discuss why we don't need an explicit visited set (can mutate grid) vs. when we must preserve state.
- **Time:** 60 min

---

## Day 7 — Interview Simulation & Review
**Budget today:** 60 min

### DSA: Merge k Sorted Lists (LeetCode 23)
- **Pattern / goal:** Heap / priority queue; merging multiple sequences; divide-and-conquer.
- **Approach:**
  - Implement using a min-heap (Python heapq) to always extract the smallest head; handle custom comparator for ListNode.
  - Trace through `[[1,4,5],[1,3,4],[2,6]]` to understand heap operations.
  - Discuss time complexity O(n*k*log k) where k is number of lists; space for heap.
- **Time:** 60 min

---

## Weak areas to revisit
None identified yet — first session will surface these.