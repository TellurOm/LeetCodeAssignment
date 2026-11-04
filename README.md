# LeetCode Solutions — DSA 3 Assignment

## Problem Index

| # | Problem Title | Difficulty | Algorithmic Paradigm | Time Complexity | Space Complexity | Solution Code |
|:---:|:---|:---:|:---|:---:|:---:|:---:|
| **5** | [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/) | `Medium` | Two Pointers (Expand Center) | $\mathcal{O}(n^2)$ | $\mathcal{O}(1)$ | [`LeetCode5.cpp`](./LeetCode5.cpp) |
| **72** | [Edit Distance](https://leetcode.com/problems/edit-distance/) | `Medium` | 2D Dynamic Programming | $\mathcal{O}(n \cdot m)$ | $\mathcal{O}(n \cdot m)$ | [`LeetCode72.cpp`](./LeetCode72.cpp) |
| **139** | [Word Break](https://leetcode.com/problems/word-break/) | `Medium` | 1D Dynamic Programming + Set | $\mathcal{O}(n^2)$ | $\mathcal{O}(n + m)$ | [`LeetCode139.cpp`](./LeetCode139.cpp) |
| **146** | [LRU Cache](https://leetcode.com/problems/lru-cache/) | `Medium` | Hash Map + Doubly Linked List | $\mathcal{O}(1)$ avg | $\mathcal{O}(\text{capacity})$ | [`LeetCode146.cpp`](./LeetCode146.cpp) |
| **206** | [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/) | `Easy` | Iterative 3-Pointer Traversal | $\mathcal{O}(n)$ | $\mathcal{O}(1)$ | [`LeetCode206.cpp`](./LeetCode206.cpp) |
| **207** | [Course Schedule](https://leetcode.com/problems/course-schedule/) | `Medium` | Topological Sort (Kahn's BFS) | $\mathcal{O}(V + E)$ | $\mathcal{O}(V + E)$ | [`LeetCode207.cpp`](./LeetCode207.cpp) |
| **295** | [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/) | `Hard` | Two Heaps (Max-Heap & Min-Heap) | $\mathcal{O}(\log n)$ / $\mathcal{O}(1)$ | $\mathcal{O}(n)$ | [`LeetCode295.cpp`](./LeetCode295.cpp) |
| **307** | [Range Sum Query - Mutable](https://leetcode.com/problems/range-sum-query-mutable/) | `Medium` | Segment Tree (Point Update, Range Query) | $\mathcal{O}(\log n)$ | $\mathcal{O}(n)$ | [`LeetCode307.cpp`](./LeetCode307.cpp) |
| **315** | [Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/) | `Hard` | Divide & Conquer (Merge Sort Inversions) | $\mathcal{O}(n \log n)$ | $\mathcal{O}(n)$ | [`LeetCode315.cpp`](./LeetCode315.cpp) |

---

## Solutions & Approaches

### 1. LeetCode 5 — Longest Palindromic Substring
- **Approach:** Expand around potential centers (both odd-length center `(i, i)` and even-length center `(i, i+1)`).
- **Core Logic:** A palindrome mirrors around its center. Checking all $2n - 1$ centers takes $\mathcal{O}(n^2)$ time with $\mathcal{O}(1)$ auxiliary space, avoiding table DP memory overhead.
- **Solution:** [`LeetCode5.cpp`](./LeetCode5.cpp)

### 2. LeetCode 72 — Edit Distance
- **Approach:** Bottom-up 2D Dynamic Programming.
- **Core Logic:** State `dp[i][j]` stores minimum operations to convert `word1[0..i-1]` to `word2[0..j-1]`. If characters match, take diagonal value `dp[i-1][j-1]`; otherwise take `1 + min(insert, delete, replace)`.
- **Solution:** [`LeetCode72.cpp`](./LeetCode72.cpp)

### 3. LeetCode 139 — Word Break
- **Approach:** 1D Dynamic Programming with `std::unordered_set`.
- **Core Logic:** `dp[i]` is true if prefix `s[0..i-1]` can be segmented into dictionary words. For index $i$, check if there exists $j < i$ such that `dp[j] == true` and substring `s[j..i-1]` exists in dictionary.
- **Solution:** [`LeetCode139.cpp`](./LeetCode139.cpp)

### 4. LeetCode 146 — LRU Cache
- **Approach:** Doubly Linked List (`std::list`) + Hash Map (`std::unordered_map`).
- **Core Logic:** The hash map provides $\mathcal{O}(1)$ key lookup to list iterators. Accessed elements move to the front; when capacity is reached, least recently used elements are evicted from the tail in $\mathcal{O}(1)$.
- **Solution:** [`LeetCode146.cpp`](./LeetCode146.cpp)

### 5. LeetCode 206 — Reverse Linked List
- **Approach:** Iterative 3-pointer traversal (`prev`, `curr`, `next`).
- **Core Logic:** Reverses pointers in-place in linear $\mathcal{O}(n)$ time and $\mathcal{O}(1)$ space without requiring recursion stack memory.
- **Solution:** [`LeetCode206.cpp`](./LeetCode206.cpp)

### 6. LeetCode 207 — Course Schedule
- **Approach:** Topological Sort using Kahn's Algorithm (BFS).
- **Core Logic:** Track course in-degrees in a directed graph. Enqueue courses with 0 prerequisites. Process queue and decrement adjacent in-degrees. If total processed courses equal `numCourses`, no cycles exist.
- **Solution:** [`LeetCode207.cpp`](./LeetCode207.cpp)

### 7. LeetCode 295 — Find Median from Data Stream
- **Approach:** Dual Heaps (`std::priority_queue`).
- **Core Logic:** Max-heap stores the smaller half, min-heap stores the larger half. Balancing sizes ensures $\mathcal{O}(\log n)$ insertion and $\mathcal{O}(1)$ median retrieval.
- **Solution:** [`LeetCode295.cpp`](./LeetCode295.cpp)

### 8. LeetCode 307 — Range Sum Query - Mutable
- **Approach:** Segment Tree.
- **Core Logic:** Binary tree built over $4n$ array space. Supports single element updates and arbitrary range sum queries in logarithmic $\mathcal{O}(\log n)$ time.
- **Solution:** [`LeetCode307.cpp`](./LeetCode307.cpp)

### 9. LeetCode 315 — Count of Smaller Numbers After Self
- **Approach:** Modified Merge Sort with index tracking.
- **Core Logic:** While merging sorted halves, if a right-half element is smaller than a left-half element, it counts as an inversion for all remaining left-half elements, achieving $\mathcal{O}(n \log n)$ overall runtime.
- **Solution:** [`LeetCode315.cpp`](./LeetCode315.cpp)

---

## Repository Structure

```text
LeetCodeAssignment1/
├── LeetCode5.cpp       # Longest Palindromic Substring
├── LeetCode72.cpp      # Edit Distance
├── LeetCode139.cpp     # Word Break
├── LeetCode146.cpp     # LRU Cache
├── LeetCode206.cpp     # Reverse Linked List
├── LeetCode207.cpp     # Course Schedule
├── LeetCode295.cpp     # Find Median from Data Stream
├── LeetCode307.cpp     # Range Sum Query - Mutable
├── LeetCode315.cpp     # Count of Smaller Numbers After Self
└── README.md           # Assignment documentation & index
```
