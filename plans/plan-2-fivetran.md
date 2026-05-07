# Prep Plan: Fivetran — Senior Software Engineer
**Budget:** 120 min over 7 days
**Rounds:** dsa
**Generated:** 2026-05-07

---

**Note on Budget:** The provided total budget of 120 minutes over 7 days is extremely tight. A single DSA problem typically requires 45-60 minutes for a thorough approach (understanding, Big O, coding, testing, discussing edge cases). This plan prioritizes the most directly reported problems within your budget, front-loading the practice to allow for review. It covers 2 problems in total.

---

## Day 1 — Foundational DSA: Heaps
**Budget today:** 60 min

### DSA: Employee Score Management (Heap-based)
-   **Pattern / goal:** Practice using heaps (priority queues) to efficiently manage and query dynamic sets of data, often for "top K" or "Kth largest/smallest" scenarios. This directly addresses the reported "Employee score management problem (Heap-based)".
-   **Approach:**
    1.  Clarify requirements for an employee score management system (e.g., add score, find top K scores, find median score).
    2.  Model the problem as finding the Top K Frequent Elements, a common heap application.
    3.  Implement a solution using a frequency map and a min-heap (for Top K) or a double-heap approach (for median).
    4.  Analyze time and space complexity, discuss edge cases.
-   **Specific Problem:** LeetCode 347: Top K Frequent Elements
-   **Time:** 60 min

---

## Day 2 — Foundational DSA: Dynamic Programming
**Budget today:** 60 min

### DSA: Longest Increasing Subsequence (LIS)
-   **Pattern / goal:** Practice dynamic programming (DP) techniques, specifically for sequence problems where optimal substructure and overlapping subproblems are present. This is a classic DP problem reported directly by a Fivetran candidate.
-   **Approach:**
    1.  Start with a brute-force recursive solution to understand the overlapping subproblems.
    2.  Memoize the recursive solution to optimize.
    3.  Develop an iterative DP solution using an array to store subproblem results.
    4.  (Optional, if time permits): Explore the O(N log N) solution using patience sorting / binary search.
-   **Specific Problem:** LeetCode 300: Longest Increasing Subsequence
-   **Time:** 60 min

---

## Day 3 — Review & Rest
**Budget today:** 0 min
*Review solutions from Day 1 & 2. Understand any missed edge cases or alternative approaches.*

---

## Day 4 — Review & Rest
**Budget today:** 0 min
*Review core data structures (arrays, lists, maps, trees, graphs) and algorithms (sorting, searching).*

---

## Day 5 — Review & Rest
**Budget today:** 0 min
*Light review of Big O notation and common algorithm complexities.*

---

## Day 6 — Final Review
**Budget today:** 0 min
*Mentally walk through the solutions to Day 1 & 2 problems without coding. Focus on clear communication of your thought process.*

---

## Day 7 — Pre-interview Prep
**Budget today:** 0 min
*Relax. Ensure your environment is ready for the interview tomorrow.*

---

## Weak areas to revisit
None identified yet — first session will surface these.

---

## Research & Sources

Here is everything I found across Fivetran's official blog, LeetCode Discuss, Glassdoor, Blind, and aggregator sites. Note that Fivetran uses the round name **"Coding Ability and Problem Solving"** (C1 in their own nomenclature) specifically for the problem-solving DSA challenge.

---

## Interview Questions: Fivetran — "Coding Ability and Problem Solving" (DSA) — Senior Software Engineer

> Data compiled from 7+ sources across Glassdoor, LeetCode Discuss, Blind, Fivetran's own engineering blog, and aggregator sites. Most recent source: March 2025. Search date: May 7, 2026.

---

### Round Format & Structure



The coding challenge runs 60–90 minutes (video or in-person). The **C1 "Problem Solving"** challenge is described by Fivetran as "a fairly standard coding question, designed to determine a base level of problem-solving ability in the software language of your choice," conducted via HackerRank.





There is also a second coding challenge **(C2 "Coding Structure and Data Processing")** — a more focused problem evaluating your ability to interact with a codebase, think structurally, and perform basic data manipulation — given as part of the on-site.





C2 is given in Java, though there are very few advanced language features, and the interviewer is instructed to help with minor language difficulties (i.e., a Python engineer should be able to pass).





One candidate noted that the technical interview process involved several parts: discussing, estimation (Big O notation), improving or simplifying a solution, coding, checking, and then a detailed discussion of all pros and cons of your decision.



---

### Confirmed Questions Asked (Firsthand Accounts)

#### Arrays / Heaps / Greedy

1. **Employee score management problem (Heap-based)**
   - 

One SDE-2 candidate reported: the OA consisted of a single HackerRank question in Java only. "The problem was based on managing employee scores." The candidate approached it using a heap-based solution, with only 2–3 test cases failing.


   - Source: [LeetCode Discuss](https://leetcode.com/discuss/interview-experience/6836681/) — approx. 2024/2025

2. **Heaps question (general)**
   - 

A candidate reported being asked "a Heaps-related question" and was expected to write executable code with all test cases passing.


   - Source: [Glassdoor](https://www.glassdoor.com/Interview/Fivetran-Software-Developer-Interview-Questions-EI_IE1415980.0,8_KO9,27.htm) — approx. 2022/2023

3. **Array / medium-difficulty problem**
   - 

One candidate reported receiving a question "on arrays."


   - Source: [Glassdoor](https://www.glassdoor.com/Interview/Fivetran-Software-Engineer-Interview-Questions-EI_IE1415980.0,8_KO9,26.htm) — approx. 2022

4. **Greedy approach problem**
   - 

One candidate reported getting "a question of greedy approach" during the live coding (second technical) interview.


   - Source: [Glassdoor](https://www.glassdoor.com/Interview/Fivetran-Software-Engineer-Interview-Questions-EI_IE1415980.0,8_KO9,26.htm) — approx. 2022

5. **Minimum budget / scheduling problem (OA — Binary Search / Greedy)**
   - 

A 2024 HackerRank OA question: Given two arrays with "expected cost" and "worst case cost" for each product, return the minimum starting budget that allows producing all products. Tagged as Binary Search.


   - Source: [LeetCode Discuss](https://leetcode.com/discuss/interview-question/5179750/Fivetran-OA-SDE-2/) — May 2024

#### Dynamic Programming

6. **Longest Increasing Subsequence (LIS)**
   - 

In the first part of a technical coding round, a candidate was asked to solve the classic Longest Increasing Subsequence (LIS) problem, in a session "divided into two parts, both focused on data structures and algorithms."


   - Source: [LeetCode Discuss](https://leetcode.com/discuss/interview-experience/6836681/) — approx. 2024/2025

#### Greedy / Gas Station Variant

7. **"Aladdin and the Magic Carpet" — similar to LeetCode 134: Gas Station**
   - 

In the second part of the same session, the candidate was given a custom problem called "Aladdin and the Magic Carpet," conceptually similar to LeetCode 134 (Gas Station). The interviewer clarified the problem, and the candidate then "implemented a greedy approach."


   - Source: [LeetCode Discuss](https://leetcode.com/discuss/interview-experience/6836681/) — approx. 2024/2025

#### Graph Traversal

8. **Graph traversal (LC-medium) — live on HackerRank**
   - 

One SDE-2 candidate was given "1 LC medium question based on graph traversal" via HackerRank, where all test cases needed to pass. Basic graph-theory follow-up questions were also asked.


   - Source: [LeetCode Discuss](https://leetcode.com/discuss/interview-experience/1793270/fivetran-sde-2-bangalore/) — 2022

#### Strings / Encoding

9. **Decode compressed string to frequency array (advanced run-length encoding)**
   - 

A phone interview question hosted on HackerRank, described as "an advanced version of run-length encoding." The input string contains digits 0–9 and parentheses. Digits outside parentheses map to lowercase English alphabets; digits inside parentheses map to the frequencies of the corresponding alphabets.


   - Source: [LeetCode Discuss](https://leetcode.com/discuss/post/6046597/Fivetran-or-Data-Engineer-phone-interview-or-Decode-compressed-string-to-frequency-array/) — Nov 2024

---

### Topics Mentioned From Aggregators (Less Reliable — Prep-Site Listed)



One aggregator (Interview Solver) lists Fivetran as commonly asking ~44 coding problems, including **Longest Palindromic Substring**, **Populating Next Right Pointers in Each Node**, and **Reveal Cards In Increasing Order**, with a difficulty split of 10 Easy / 27 Medium / 7 Hard. The site notes that "Fivetran interviews typically emphasize Array and String."



*(These are aggregated from LeetCode tagging data — treat as directional signal, not confirmed questions.)*

---

### Themes & Patterns

- 

The first round is typically a HackerRank-based test with **one coding question at medium difficulty** — "like a LeetCode medium-level question" — with a 60-minute time limit.


- 

One candidate described the process as "R1 → Tough HackerRank question; R2 → F2F tough LeetCode-kind of question where you have to run all test cases in front of the interviewer."


- **All test cases must pass.** This is a recurring theme — HackerRank auto-grades, and interviewers also check during live sessions. Partial credit is not guaranteed.
- 

Candidates are encouraged to ask questions about the problem and the merits of different approaches. "This interview works best for both participants if it's a conversation."


- **Topics seen across reports:** Arrays, Heaps, Greedy, Graph traversal, Dynamic Programming (LIS), Strings/Encoding. Maps are also reported (primarily for SDET). 

One SDET candidate reported "an easy-level Map-based question" in the HackerRank coding test, and "primarily LC Medium questions, mainly consisting of Maps" in the DSA round.



---

### Preparation Tips (from candidates)

- 

Be prepared to explain your thought process and approach during live coding sessions — "interviewers appreciate candidates who can articulate their reasoning and problem-solving strategies."


- 

Expect estimation of time complexity (Big O), discussion of trade-offs, and code improvement as part of the conversation, not just writing the solution.


- 

Brush up on Java and DBMS. "For senior roles, technologies such as Docker and Kubernetes are important" (may come up outside the DSA round).


- 

One Blind user noted: "Was asked an easy HackerRank question. Solved it with all tests passing in the first 15 mins. Then was asked follow-up questions and asked to explain the approach verbally."

 — Don't assume you're done once the code runs; verbal walkthroughs follow.

---

### Sources

| # | Title / Thread | Platform | URL | Approx. Date |
|---|---------------|----------|-----|--------------|
| 1 | Fivetran SDE-2 interview review | LeetCode Discuss | https://leetcode.com/discuss/interview-experience/6836681/ | 2024/2025 |
| 2 | Fivetran OA — SDE-2 | LeetCode Discuss | https://leetcode.com/discuss/interview-question/5179750/Fivetran-OA-SDE-2/ | May 2024 |
| 3 | Fivetran \| SDE-2 \| Bangalore | LeetCode Discuss | https://leetcode.com/discuss/interview-experience/1793270/fivetran-sde-2-bangalore/ | Feb 2022 |
| 4 | Fivetran Data Engineer phone interview — Decode compressed string | LeetCode Discuss | https://leetcode.com/discuss/post/6046597/ | Nov 2024 |
| 5 | The Software Engineering Interview at Fivetran (official blog) | Fivetran Blog | https://www.fivetran.com/blog/software-engineering-interview | Mar 2025 |
| 6 | Fivetran Software Engineer Interview Questions | Glassdoor | https://www.glassdoor.com/Interview/Fivetran-Software-Engineer-Interview-Questions-EI_IE1415980.0,8_KO9,26.htm | Various (2022–2025) |
| 7 | Fivetran Software Developer Interview Questions | Glassdoor | https://www.glassdoor.com/Interview/Fivetran-Software-Developer-Interview-Questions-EI_IE1415980.0,8_KO9,27.htm | Various |
| 8 | Fivetran interview (Blind) | Blind | https://www.teamblind.com/post/Fivetran-interview-ci3YWmOB | Mar 2022 |
| 9 | Fivetran Interview Questions (aggregator) | Interview Solver | https://interviewsolver.com/interview-questions/fivetran | 2024 |
| 10 | Fivetran Senior SDET Interview Experience | Joint Taro | https://www.jointaro.com/interviews/companies/fivetran/experiences/senior-sdet-bengaluru-september-1-2024-no-offer-positive-9820d168/ | Sep 2024 |