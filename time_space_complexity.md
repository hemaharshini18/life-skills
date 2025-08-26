# Time and Space Complexity 
---

## Introduction
When solving computational problems, multiple algorithms may exist to reach a solution. To evaluate and compare them, we use **time and space complexity analysis**. This analysis helps us understand how the performance of an algorithm grows with respect to input size. Importantly, complexity analysis is **independent of machine configurations**, making it a reliable measure for theoretical performance.

---

## Time Complexity
Time complexity quantifies the amount of time taken by an algorithm as a function of the input size. It measures the **order of growth** of execution time rather than the exact runtime on a specific machine.

- **Definition:** The time required by an algorithm to solve a given problem.
- **Assumption:** Each fundamental operation takes a constant time `c`.
- **Focus:** Worst-case analysis is often used in complexity evaluation.

### Example 1: Addition of Scalars
```python
def add(a,b):
    c=a+b
    return c
```
- Only one addition operation is required.  
- **Time Complexity:** `O(1)` (constant time).

### Example 2: Finding a Pair with a Given Sum
```python
def findPair(a, n, z):
    for i in range(n):
        for j in range(n):
            if i != j and a[i] + a[j] == z:
                return True
    return False
```
- Outer loop runs **N** times.
- Inner loop runs **N** times for each outer iteration.
- Total ≈ `N²` comparisons.
- **Time Complexity:** `O(N²)`.

### Example 3: Nested Loop with Halving
```python
count = 0
i = N
while i > 0:
    for j in range(i):
        count += 1
    i //= 2
```
- Runs `N + N/2 + N/4 + ... + 1 ≈ 2N` times.
- **Time Complexity:** `O(N)`.


## Space Complexity
Space complexity quantifies the amount of memory required by an algorithm as a function of the input size.

### Components:
1. **Fixed Part** – independent of input (instructions, constants, variables).
2. **Variable Part** – dependent on input (recursion stack, dynamic structures).

### Example 1: Addition of Scalars
```python
def add(a,b):
    c=a+b
    return c
```
- Requires one additional variable `C`.
- **Space Complexity:** `O(1)`.

### Example 2: Frequency Counting
```python
def countFreq(arr, n):
    freq = {}
    for i in arr:
        if i not in freq:
            freq[i] = 0
        freq[i] += 1
    for x in freq:
        print(x, freq[x])
```
- Uses an auxiliary dictionary of size `N`.
- **Space Complexity:** `O(N)`.
- **Auxiliary Space:** Memory apart from the input (`freq` array).

---

## Key Differences
- **Time Complexity:** Measures execution time growth.
- **Space Complexity:** Measures memory usage growth.
- **Auxiliary Space:** Extra memory beyond input storage.

---

## Conclusion
Understanding **time and space complexity** is crucial for designing efficient algorithms. By analyzing performance in terms of input size, developers can:
- Choose the optimal algorithm.
- Predict scalability.
- Balance between **speed** and **memory usage**.

This forms the foundation for advanced topics in **competitive programming, optimization, and real-world software engineering**.

