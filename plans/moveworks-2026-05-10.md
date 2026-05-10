# Prep Plan: Moveworks — Senior Software Engineer
**Interview:** 2026-05-17
**Rounds:** DSA
**Generated:** 2024-05-10

---

## Day 1 — Foundational Data Structures (Arrays & Strings)

### DSA: Longest Substring Without Repeating Characters (LC 3)
- **Pattern / goal:** Sliding Window, Hash Set for character tracking
- **Approach:**
    - Clarify constraints and edge cases (empty string, single character string).
    - Use two pointers (left, right) to define the current window.
    - Maintain a hash set to store characters in the current window.
    - Expand the window with `right` pointer, adding characters to the set.
    - If a duplicate is found, shrink the window with `left` pointer, removing characters from the set, until the window is valid again.
    - Keep track of the maximum length found.
    - Trace with example: "abcabcbb"
- **Time:** 60 min

### DSA: 3Sum (LC 15)
- **Pattern / goal:** Two Pointers, Sorting, Handling Duplicates
- **Approach:**
    - Clarify input (array of integers), output (list of unique triplets summing to zero).
    - Sort the array first to efficiently use two pointers and handle duplicates.
    - Iterate through the array with one pointer (`i`). For each `nums[i]`, use two pointers (`left`, `right`) on the remaining array to find `nums[left] + nums[right] == -nums[i]`.
    - Skip duplicate values for `nums[i]`, `nums[left]`, and `nums[right]` to ensure unique triplets.
    - Trace with example: `[-1, 0, 1, 2, -1, -4]`
- **Time:** 60 min

---

## Day 2 — Hash Maps & String Manipulation

### DSA: Group Anagrams (LC 49)
- **Pattern / goal:** Hash Maps, String Hashing/Sorting
- **Approach:**
    - Clarify input (array of strings), output (groups of anagrams).
    - For each string, generate a canonical representation (e.g., sort the characters of the string).
    - Use a hash map where the key is the canonical representation and the value is a list of strings that share that canonical form.
    - Iterate through the input array, compute the key, and add the original string to the corresponding list in the hash map.
    - Trace with example: `["eat", "tea", "tan", "ate", "nat", "bat"]`
- **Time:** 50 min

### DSA: Longest Palindromic Substring (LC 5)
- **Pattern / goal:** Dynamic Programming or Expand Around Center
- **Approach:**
    - Clarify definition of palindrome and substring.
    - Consider two main approaches:
        1.  **Expand Around Center:** Iterate through each character as a potential center (for odd length palindromes) and between each pair of characters (for even length palindromes). Expand outwards.
        2.  **Dynamic Programming:** `dp[i][j]` is true if `s[i...j]` is a palindrome. Base cases for length 1 and 2. Recurrence: `dp[i][j] = (s[i] == s[j]) && dp[i+1][j-1]`.
    - Implement the "Expand Around Center" method for efficiency and simplicity.
    - Trace with example: "babad"
- **Time:** 60 min

---

## Day 3 — Tree Traversal & Properties

### DSA: Binary Tree Level Order Traversal (LC 102)
- **Pattern / goal:** Breadth-First Search (BFS), Queue usage
- **Approach:**
    - Clarify output format (list of lists, each sublist containing nodes at a specific level).
    - Use a queue to manage nodes to visit.
    - Start by adding the root to the queue.
    - While the queue is not empty, process all nodes at the current level:
        - Get the current level's size.
        - Dequeue `size` nodes, add their values to a temporary list for the current level.
        - Enqueue their children (if they exist).
        - Add the temporary list to the final result.
    - Trace with example: `[3,9,20,null,null,15,7]`
- **Time:** 50 min

### DSA: Validate Binary Search Tree (LC 98)
- **Pattern / goal:** Depth-First Search (DFS), Binary Search Tree properties
- **Approach:**
    - Clarify the strict definition of a BST (left child < current < right child, and this applies transitively to all subtrees).
    - Use an in-order traversal approach, where values should be strictly increasing. Keep track of the `prev` node's value.
    - Alternatively, use a recursive DFS approach passing `min` and `max` bounds for each node.
    - Implement the `min/max` bounds approach for robustness: `isValidBST(node, min_val, max_val)`.
    - Trace with example: `[5,1,4,null,null,3,6]` (false)
- **Time:** 60 min

---

## Day 4 — Graph Traversal

### DSA: Number of Islands (LC 200)
- **Pattern / goal:** Depth-First Search (DFS) or Breadth-First Search (BFS) on a grid
- **Approach:**
    - Clarify input (2D grid of '1's and '0's), output (count of islands).
    - Iterate through each cell of the grid.
    - If a '1' is encountered, increment the island count and start a DFS (or BFS) from that cell.
    - During DFS/BFS, mark all connected '1's as '0' (or visited) to avoid recounting and cycles.
    - Define directions for traversal (up, down, left, right).
    - Trace with example: `[["1","1","1","1","0"],["1","1","0","1","0"],["1","1","0","0","0"],["0","0","0","0","0"]]`
- **Time:** 55 min

### DSA: Clone Graph (LC 133)
- **Pattern / goal:** Graph Traversal (DFS or BFS), Hash Map for visited nodes
- **Approach:**
    - Clarify input (reference to a node in a connected undirected graph), output (deep copy of the graph).
    - Use a hash map to store mappings from original nodes to their cloned counterparts to prevent infinite loops and ensure only one clone per node.
    - Implement a DFS (or BFS) traversal.
    - When visiting a node:
        - If already in the map, return its clone.
        - Otherwise, create a new clone node.
        - Add mapping (original -> clone) to the hash map.
        - Recursively call DFS for each neighbor and add the cloned neighbors to the cloned node's adjacency list.
    - Trace with example: `[[2,4],[1,3],[2,4],[1,3]]`
- **Time:** 60 min

---

## Day 5 — Dynamic Programming & Heaps

### DSA: Minimum Path Sum (LC 64)
- **Pattern / goal:** Dynamic Programming (2D grid DP)
- **Approach:**
    - Clarify input (m x n grid of non-negative integers), output (minimum sum path from top-left to bottom-right).
    - Define `dp[i][j]` as the minimum path sum to reach cell `(i, j)`.
    - Base case: `dp[0][0] = grid[0][0]`.
    - Recurrence relation: `dp[i][j] = grid[i][j] + min(dp[i-1][j], dp[i][j-1])`.
    - Handle boundary conditions for the first row and first column separately.
    - Optimize space if possible (using only two rows/columns).
    - Trace with example: `[[1,3,1],[1,5,1],[4,2,1]]`
- **Time:** 55 min

### DSA: Kth Largest Element in an Array (LC 215)
- **Pattern / goal:** Min-Heap (Priority Queue) or Quickselect Algorithm
- **Approach:**
    - Clarify input (unsorted array, integer k), output (kth largest element).
    - **Using Min-Heap:** Maintain a min-heap of size `k`. Iterate through the array; if the current element is greater than the heap's smallest element (root), pop the root and push the current element. The root of the heap after iterating through all elements will be the kth largest.
    - **Using Quickselect:** Implement a selection algorithm based on the partitioning step of Quicksort. Randomly pick a pivot, partition the array, and based on the pivot's position, recurse on the left or right sub-array. This has an average time complexity of O(N).
    - Implement the Min-Heap approach for simplicity and guaranteed worst-case performance.
    - Trace with example: `nums = [3,2,1,5,6,4], k = 2`
- **Time:** 60 min

---

## Day 6 — Linked Lists & Backtracking

### DSA: Linked List Cycle (LC 141)
- **Pattern / goal:** Two Pointers (Floyd's Cycle-Finding Algorithm / Tortoise and Hare)
- **Approach:**
    - Clarify input (head of a linked list), output (boolean indicating cycle presence).
    - Use two pointers, `slow` and `fast`.
    - `slow` moves one step at a time, `fast` moves two steps at a time.
    - If there's a cycle, `fast` will eventually catch up to `slow`.
    - If `fast` or `fast.next` becomes `null`, there is no cycle.
    - Trace with example: `head = [3,2,0,-4]`, pos = 1
- **Time:** 45 min

### DSA: Permutations (LC 46)
- **Pattern / goal:** Backtracking
- **Approach:**
    - Clarify input (array of distinct numbers), output (list of all possible permutations).
    - Use a recursive backtracking function: `backtrack(current_permutation, remaining_elements)`.
    - Base case: If `remaining_elements` is empty, add `current_permutation` to the results.
    - Recursive step: Iterate through `remaining_elements`. For each element:
        - Add it to `current_permutation`.
        - Recursively call `backtrack` with the updated `current_permutation` and `remaining_elements` (excluding the chosen element).
        - **Backtrack:** Remove the element from `current_permutation` to explore other choices.
    - Use a `visited` array or a temporary list removal to manage `remaining_elements`.
    - Trace with example: `[1,2,3]`
- **Time:** 60 min

---

## Day 7 — Advanced DSA / Comprehensive Problem

### DSA: Merge k Sorted Lists (LC 23)
- **Pattern / goal:** Divide and Conquer, Min-Heap (Priority Queue), Linked Lists
- **Approach:**
    - Clarify input (array of k sorted linked lists), output (one merged sorted linked list).
    - Consider two main approaches:
        1.  **Min-Heap:** Insert the head of each list into a min-heap. Repeatedly extract the minimum element, add it to the merged list, and if that element had a `next`, add its `next` to the heap.
        2.  **Divide and Conquer:** Recursively merge pairs of lists until only one remains. `mergeKLists(lists) = mergeTwoLists(mergeKLists(left_half), mergeKLists(right_half))`.
    - Implement the Min-Heap approach for its clear logic and efficiency (O(N log k) where N is total elements).
    - Trace with example: `lists = [[1,4,5],[1,3,4],[2,6]]`
- **Time:** 60 min

---

## Weak areas to revisit
None identified yet — first session will surface these.