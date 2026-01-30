# Data Structures and Algorithms Notes

**Author:** Fernando K.I. Fugihara  

## Table of Contents

### Fundamentals
- [Introduction](#introduction)
- [Big O Notation](#big-o-notation---how-code-slows-as-data-grows)

### Data Structures & Algorithms Topics
1. [Arrays & Hashing](#1-arrays--hashing) - [My Solutions](./%231-Arrays-Hashing/)
2. [Two Pointers](#2-two-pointers) - [My Solutions](./%232-Two-Pointers/)
3. [Stack](#3-stack) - [My Solutions](./%233-Stack/)
4. [Binary Search](#4-binary-search) - [My Solutions](./%234-Binary-Search/)
5. [Sliding Window](#5-sliding-window) - [My Solutions](./%235-Sliding-Window/)
6. [Linked List](#6-linked-list) - [My Solutions](./%236-Linked-List/)
7. [Trees](#7-trees) - [My Solutions](./%237-Trees/)
8. [Tries](#8-tries) - [My Solutions](./%238-Tries/)
9. [Heap / Priority Queue](#9-heap--priority-queue) - [My Solutions](./%239-Heap-Priority-Queue/)
10. [Backtracking](#10-backtracking) - [My Solutions](./%2310-Backtracking/)
11. [Graphs](#11-graphs) - [My Solutions](./%2311-Graphs/)
12. [1-D Dynamic Programming](#12-1-d-dynamic-programming) - [My Solutions](./%2312-1D-Dynamic-Programming/)
13. [Intervals](#13-intervals) - [My Solutions](./%2313-Intervals/)
14. [Greedy](#14-greedy) - [My Solutions](./%2314-Greedy/)
15. [Advanced Graphs](#15-advanced-graphs) - [My Solutions](./%2315-Advanced-Graphs/)
16. [2-D Dynamic Programming](#16-2-D-dynamic-programming) - [My Solutions](./%2316-2D-Dynamic-Programming/)
17. [Bit Manipulation](#17-bit-manipulation) - [My Solutions](./%2317-Bit-Manipulation/)
18. [Math & Geometry](#18-math--geometry) - [My Solutions](./%2318-Math-Geometry/)

**External Resources:**
- [NeetCode 150 Practice](https://neetcode.io/practice) - Official problem list
- [NeetCode Roadmap](https://neetcode.io/roadmap) - Visual learning path

## Introduction

In order to become a better programmer, I'll go back to one of the most fundamental and important subject of Computer Science: Data Structures and Algorithms. This guide was made by me for me, so them I can go back to this article and remember the concepts. I'll follow the [neetcode roadmap](https://neetcode.io/roadmap), it contains 150 leetcode problems divided into 18 topics: Arrays & Hashing, Two Pointers, Stack, Binary Search, Sliding Window, Linked List, Trees, Tries, Heap, Backtracking, Graphs, 1-D DP, Intervals, Greedy, Advanced Graphs, 2-D DP, Bit Manipulation, Math & Geometry. But first, let's learn and understand more about the Big O notation.

---

## Big O notation - "How code slows as data grows"

What is Big O? Is a notation to describe the performance and efficiency of an algorithm or data structure.

1. Describes the performance of an algorithm as the amount of data increases
2. Machine Independent (n steps to completion)
3. It's calculated based on the number of operations (like sums, comparisons, assignments) an algorithm performs
4. Ignore smaller operations O(n+1) = O(n)

### Time and Space Complexity

Time complexity of an algorithm quantifies the amount of time taken by an algorithm to run as a function of the length of the input.

Space complexity of an algorithm quantifies the amount of space or memory taken by an algorithm to run as a function of the length of the input.

### Examples

In the example below, we have a linear time complexity O(n), if n=100000, then it will take ≈100000 steps to execute the algorithm.

**Summation algorithm with linear time complexity O(n):**

```python
def addUp(int n) -> int:
    sum = 0
    for i in range(n):
        sum += i
    return sum
```

In this second example, we have a constant time complexity O(1), if n = 100000, it will take 3 steps to execute the algorithm. Why it's not O(3)? Because, in the grand scheme of things doesn't make difference.

**Summation algorithm with constant time complexity O(1):**

```python
def addUp(int n) -> int:
    sum = n * (n + 1) / 2;
    return sum
```

### Summary

**O(1)** = Constant time
- Random access of an element from an array
- Inserting at the beginning of a linked-list

**O(log n)** = Logarithmic time
- Binary Search
- Searching through a binary tree

**O(n)** = Linear time
- Looping through elements of an array
- Searching through a linked list

**O(n log n)** = Quasilinear time
- quicksort
- mergesort
- heapsort

**O(n²)** = Quadratic time
- insertion sort
- selection sort
- bubblesort

**O(n!)** = Factorial time
- Travelling salesman problem

---

## Data Structures & Algorithms

### 1. Arrays & Hashing

[📁 View My Solutions](./%231-Arrays-Hashing/)

#### Dynamic Arrays
Arrays are contiguous blocks of memory. In other words, are allocated memory with no gap bytes between them. When we create an array (static or dynamically), we allocate a contiguous block in memory.

##### Time and Space Complexity

* Access (random element): **O(1)** -> direct pointer to memory address
* Insert/Delete element: **O(n)** -> shift all elements left or right
* Insert/Delete last element: **O(1)**
* Search: **O(n)**
* Search Sorted: **O(log n)**
* Space Complexity (Space in Memory): **O(n)** -> Contiguous block of memory

#### Hash Tables
Hash tables are one of the most handy data structures, where you can quickly access a value through a key in O(1) time complexity, it can be a number or even a string. The hash table uses a hash function that transform a key into a memory location which is an index of an element within an array (known size). An example of hash function is down below:

```python
def hash(string key) {
    int n = 0
    for i in range(len(key))
        n = (256 * n + key[i]) % MAX # MAX is the size of the hash table array.
    return n
}
```

Also in Python we have the `hash` function within the standard library, which converts immutable objects such as strings or tuples into a integer hash value.

There is something called a `hash collision` that can occur when using hash tables. A collision occurs when two keys are mapped to the same index in the array. A good hash function will evenly distribute the keys across the hash table. This will minimize collisions and improve the time complexity of the hash table, which I'll talk about in a minute.

There are two approaches to program a hash table: `Linear probing` and `Open address`. Python uses in `dict` open addressing. In the `Linear Probing` approach when a key has the same hash, the value of the repeated hash is added in a linked list. In the `Open Adress` approach, when a repeated hash appear, the value is added in a empty array position.

##### Time and Space Complexity
* Access: **O(1)**
* Search: **O(1)**
* Insert/Delete: **O(1)**
* Space Complexity: **O(n)**

Hash tables are a great data structure for fast lookups. In Python, there are two hash-based data structures within the standard library: `dictionaries` and `sets`. The `dict` is a hash table with key value pairs based using `open addressing`. The `set` is a collection of unique elements, internally, a set is implemented as a hash table where only the keys are stored (with no associated values), ensuring no duplicates can exist. 

### 2. Two Pointers

[📁 View My Solutions](./%232-Two-Pointers/)

*(Section to be added)*

### 3. Stack

[📁 View My Solutions](./%233-Stack/)

*(Section to be added)*

### 4. Binary Search

[📁 View My Solutions](./%234-Binary-Search/)

*(Section to be added)*

### 5. Sliding Window

[📁 View My Solutions](./%235-Sliding-Window/)

*(Section to be added)*

### 6. Linked List

[📁 View My Solutions](./%236-Linked-List/)

*(Section to be added)*

### 7. Trees

[📁 View My Solutions](./%237-Trees/)

*(Section to be added)*

### 8. Tries

[📁 View My Solutions](./%238-Tries/)

*(Section to be added)*

### 9. Heap / Priority Queue

[📁 View My Solutions](./%239-Heap-Priority-Queue/)

*(Section to be added)*

### 10. Backtracking

[📁 View My Solutions](./%2310-Backtracking/)

*(Section to be added)*

### 11. Graphs

[📁 View My Solutions](./%2311-Graphs/)

*(Section to be added)*

### 12. 1-D Dynamic Programming

[📁 View My Solutions](./%2312-1D-Dynamic-Programming/)

*(Section to be added)*

### 13. Intervals

[📁 View My Solutions](./%2313-Intervals/)

*(Section to be added)*

### 14. Greedy

[📁 View My Solutions](./%2314-Greedy/)

*(Section to be added)*

### 15. Advanced Graphs

[📁 View My Solutions](./%2315-Advanced-Graphs/)

*(Section to be added)*

### 16. 2-D Dynamic Programming

[📁 View My Solutions](./%2316-2D-Dynamic-Programming/)

*(Section to be added)*

### 17. Bit Manipulation

[📁 View My Solutions](./%2317-Bit-Manipulation/)

*(Section to be added)*

### 18. Math & Geometry

[📁 View My Solutions](./%2318-Math-Geometry/)

*(Section to be added)*

---

[Back to Top](#data-structures-and-algorithms-notes)