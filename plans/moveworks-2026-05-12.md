# Prep Plan: Moveworks — Senior Software Engineer
**Interview:** 2026-05-19
**Rounds:** DSA
**Generated:** 2026-05-12

---

## Day 1 — String & Text Processing Fundamentals

### DSA: LeetCode 30 — Substring with Concatenation of All Words
- **Pattern / goal:** Sliding window with hash map for multiple substring matching — core for NLP text processing.
- **Approach:**
  - Understand the two-pointer sliding window tracking concatenated word positions.
  - Implement hash map frequency counting for all words in the concatenation list.
  - Trace through edge cases: overlapping matches, words appearing multiple times, substring length mismatches.
- **Time:** 60 min

---

## Day 2 — Dynamic Programming & Sequence Matching

### DSA: LeetCode 72 — Edit Distance
- **Pattern / goal:** DP for sequence alignment — essential for matching user intents and fuzzy matching in conversational AI.
- **Approach:**
  - Build the 2D DP table with recurrence: cost of delete, insert, replace operations.
  - Trace backtracking to reconstruct the actual edit sequence.
  - Optimize space complexity and reason about why Moveworks NLP uses similar logic for matching user queries to intents.
- **Time:** 60 min

---

## Day 3 — Graph Traversal & Relationship Modeling

### DSA: LeetCode 207 — Course Prerequisites (Topological Sort)
- **Pattern / goal:** Graph cycle detection and topological ordering — for dependency resolution in IT workflows.
- **Approach:**
  - Implement DFS-based cycle detection using a state array (unvisited, visiting, visited).
  - Build the topological sort ordering and validate correctness.
  - Reason about how Moveworks workflows model task dependencies as DAGs.
- **Time:** 60 min

---

## Day 4 — Trie & Prefix-based Queries

### DSA: LeetCode 208 — Implement Trie (Prefix Tree)
- **Pattern / goal:** Trie data structure for prefix matching and autocomplete — critical for intent recognition and command suggestions.
- **Approach:**
  - Design the TrieNode class with child pointers and end-of-word marker.
  - Implement insert, search, and startsWith methods with careful string traversal.
  - Trace memory layout and reason about how Moveworks uses tries for matching user inputs to known commands.
- **Time:** 60 min

---

## Day 5 — Hash Map & Frequency Analysis

### DSA: LeetCode 49 — Group Anagrams
- **Pattern / goal:** Hash map for grouping by canonical form — useful for clustering similar user intents and request categorization.
- **Approach:**
  - Normalize strings to canonical form (sorted chars or character frequency).
  - Use hash map to collect all anagrams under a single key.
  - Analyze time/space trade-offs and discuss how Moveworks might use this pattern for intent deduplication.
- **Time:** 60 min

---

## Day 6 — BFS & Shortest Path

### DSA: LeetCode 127 — Word Ladder
- **Pattern / goal:** BFS for shortest transformation path — applicable to workflow routing and state transitions in IT service automation.
- **Approach:**
  - Model the problem as an unweighted graph where each word is a node.
  - Implement BFS to find shortest path from start to end word.
  - Optimize by building neighbors on-the-fly using wildcard pattern matching.
  - Trace how Moveworks might apply this to finding the shortest resolution path for user requests.
- **Time:** 60 min

---

## Day 7 — Review & Integration

### DSA: LeetCode 146 — LRU Cache
- **Pattern / goal:** Hash map + doubly-linked list for O(1) caching — essential for scaling conversational AI systems.
- **Approach:**
  - Design the cache node structure and explain why DLL is needed (O(1) removal from middle).
  - Implement get and put with proper eviction and frequency tracking.
  - Discuss real-world trade-offs: when to cache intent predictions, user context, and API responses in Moveworks.
- **Time:** 60 min

---

## Weak areas to revisit
None identified yet — first session will surface these.