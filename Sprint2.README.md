## What is a Strategy in Design and Analysis of Algorithm?

In the context of Design and Analysis of Algorithm (DAA), a **strategy** refers to a general approach or method used to solve algorithmic problems. It is a high-level plan that guides the design of algorithms to efficiently solve a class of problems. Strategies help in breaking down complex problems, organizing solutions, and improving efficiency.

Common algorithmic strategies include:
- Divide and Conquer
- Greedy Method
- Dynamic Programming
- Backtracking
- Branch and Bound

---

## Divide and Conquer Strategy in Design and Analysis of Algorithm

**Divide and Conquer** is one of the most important and widely used algorithmic strategies. It involves breaking a problem into smaller subproblems, solving each subproblem independently, and then combining their solutions to solve the original problem.

### Steps in Divide and Conquer

1. **Divide:**  
   Split the original problem into two or more smaller subproblems of the same type.

2. **Conquer:**  
   Solve each subproblem recursively. If the subproblem is small enough, solve it directly (base case).

3. **Combine:**  
   Merge the solutions of the subproblems to get the solution to the original problem.

### Examples of Divide and Conquer Algorithms

- **Merge Sort**
- **Quick Sort**
- **Binary Search**
- **Strassen’s Matrix Multiplication**
- **Closest Pair of Points Problem**

---

### Important Points about Divide and Conquer

- **Recursion:**  
  Divide and conquer algorithms are often implemented using recursion.

- **Efficiency:**  
  This strategy can significantly reduce the time complexity of problems compared to naive approaches.

- **Parallelism:**  
  Subproblems are independent, so they can often be solved in parallel.

- **Overhead:**  
  There may be extra overhead in dividing and combining steps, especially if the subproblems are not large enough.

- **Master Theorem:**  
  The time complexity of divide and conquer algorithms can often be analyzed using the Master Theorem.

- **Space Complexity:**  
  May require additional space for recursive calls and combining steps (e.g., in Merge Sort).

---

**Summary:**  
A strategy in DAA is a general approach to problem-solving. Divide and conquer is a powerful strategy that breaks problems into smaller parts, solves them independently, and combines their results. It is efficient, supports parallelism, and is the basis for many fundamental algorithms.

---

## What is a Recurrence Relation?

In the context of Design and Analysis of Algorithm (DAA), a **recurrence relation** is an equation or formula that defines a sequence of values, where each term is expressed as a function of its preceding terms. Recurrence relations are commonly used to describe the running time (time complexity) of recursive algorithms.

- **Purpose:**  
  Recurrence relations help us mathematically model and analyze the performance of recursive algorithms by expressing the total work done in terms of smaller subproblems.

- **Example Use:**  
  If an algorithm solves a problem of size `n` by recursively solving a smaller problem (like size `n-1`), the time taken can be described using a recurrence relation.

---

## Example: Recurrence Relation T(n) = T(n-1) + 1

This is a simple recurrence relation often seen in algorithms that reduce the problem size by 1 at each step (such as linear recursion).

- **Meaning:**  
  The time to solve a problem of size `n` (`T(n)`) is equal to the time to solve a problem of size `n-1` (`T(n-1)`) plus a constant amount of work (1 unit).

- **Typical Scenario:**  
  This relation appears in algorithms like:
  - Simple recursive functions that process one element at a time (e.g., finding the maximum element in an array recursively).
  - Linear search implemented recursively.

- **Solving the Recurrence:**
  - Expand the relation:
    - T(n) = T(n-1) + 1
    - T(n-1) = T(n-2) + 1
    - ...
    - T(1) = T(0) + 1
  - Substitute back:
    - T(n) = T(n-1) + 1
           = [T(n-2) + 1] + 1
           = T(n-2) + 2
           = ...
           = T(0) + n
  - If T(0) = c (some constant), then:
    - T(n) = c + n

- **Time Complexity:**  
  The solution is **O(n)**, meaning the algorithm takes linear time.

---

**Summary:**  
A recurrence relation expresses the running time of a recursive algorithm in terms of smaller inputs. The relation T(n) = T(n-1) + 1 describes algorithms that reduce the problem size by 1 at each step, leading to a linear time complexity O(n).








## Recurrence Relation for Decreasing Functions

In the Design and Analysis of Algorithm (DAA), a **recurrence relation for decreasing functions** describes the running time of algorithms that solve a problem by reducing its size at each step, typically by subtracting a constant value (often 1) from the input size.

---

### General Form

The general recurrence relation for such algorithms is:

T(n) = T(n - k) + f(n)

- **T(n):** Time to solve a problem of size n.
- **k:** The amount by which the problem size decreases at each step (often k = 1).
- **f(n):** The amount of work done at each step (could be a constant or a function of n).

---

### Common Example

For most simple recursive algorithms that decrease the problem size by 1 and do a constant amount of work at each step:

T(n) = T(n - 1) + c

where **c** is a constant.

---

### Solution

By expanding the recurrence:
- T(n) = T(n-1) + c  
- T(n-1) = T(n-2) + c  
- ...  
- T(1) = T(0) + c  

Adding up, we get:
- T(n) = T(0) + n * c

If T(0) is a constant, the overall time complexity is **O(n)**.

---

### Applications

- **Linear Search (recursive)**
- **Finding maximum/minimum in an array recursively**
- **Simple counting problems**

---

**Summary:**  
Recurrence relations for decreasing functions model algorithms that reduce the problem size by a fixed amount at each step. They typically lead to linear or arithmetic time complexity, depending on the amount of work done at each

## Master Theorem for Decreasing Functions and General Form

The **Master Theorem** is a tool used to determine the time complexity of recurrence relations, especially for divide and conquer algorithms. However, for **decreasing functions** (where the problem size reduces by subtraction, not division), the Master Theorem does **not** directly apply.

---

### General Form for Decreasing Functions

A typical recurrence relation for decreasing functions is:

T(n) = T(n - k) + f(n)

- **k** is a constant (often 1).
- **f(n)** is the work done at each step (could be constant or a function of n).

---

### Solution Approach

To solve such recurrences, we use **iteration (expansion)** rather than the Master Theorem:

#### Example 1: Constant Work

T(n) = T(n - 1) + c

- Expanding:
  - T(n) = T(n-1) + c
  - T(n-1) = T(n-2) + c
  - ...
  - T(1) = T(0) + c
- Summing up:
  - T(n) = T(0) + n * c
- **Time Complexity:** O(n)

#### Example 2: Linear Work

T(n) = T(n - 1) + n

- Expanding:
  - T(n) = T(n-1) + n
  - T(n-1) = T(n-2) + (n-1)
  - ...
  - T(1) = T(0) + 1
- Summing up:
  - T(n) = T(0) + 1 + 2 + ... + n = T(0) + n(n+1)/2
- **Time Complexity:** O(n²)

---

### Key Point

- The **Master Theorem** is used for recurrences of the form:  
  `T(n) = aT(n/b) + f(n)` (where the problem size is divided, not subtracted).
- For **decreasing functions** (subtraction), use **iteration/expansion** to solve the recurrence.

---

**Summary:**  
The Master Theorem does not apply to decreasing function recurrences. Instead, solve them by expanding the recurrence and summing the work at each step. The general form is `T(n) = T(n-k) + f(n)`, and the solution depends on the nature







## Recurrence Relation for Dividing Functions

In the Design and Analysis of Algorithm (DAA), a **recurrence relation for dividing functions** describes the running time of algorithms that solve a problem by dividing it into smaller subproblems, typically by reducing the problem size by a constant factor (such as half) at each step. This is common in divide and conquer algorithms.

---

### General Form

The general recurrence relation for dividing functions is:

T(n) = a * T(n / b) + f(n)

- **T(n):** Time to solve a problem of size n.
- **a:** Number of subproblems at each step.
- **n / b:** Size of each subproblem (problem size is divided by b).
- **f(n):** The amount of work done outside the recursive calls (such as dividing and combining).

---

### Examples

- **Binary Search:**  
  T(n) = T(n/2) + c  
  (Divides the array into two halves each time)

- **Merge Sort:**  
  T(n) = 2T(n/2) + O(n)  
  (Divides the array into two halves and merges them)

- **Strassen’s Matrix Multiplication:**  
  T(n) = 7T(n/2) + O(n²)

---

### Solution Using Master Theorem

The **Master Theorem** provides a direct way to find the time complexity for recurrences of this form:

T(n) = a * T(n / b) + f(n)

- Compare f(n) with n^log_b(a):
  - If f(n) = O(n^c) where c < log_b(a): T(n) = Θ(n^log_b(a))
  - If f(n) = Θ(n^c) where c = log_b(a): T(n) = Θ(n^c * log n)
  - If f(n) = Ω(n^c) where c > log_b(a): T(n) = Θ(f(n))

---

**Summary:**  
Recurrence relations for dividing functions model algorithms that break problems into smaller subproblems by division. Their general form is `T(n) = a * T(n / b) + f(n)`, and their time complexity can be efficiently determined using the Master











## Master Theorem for Dividing Functions

The **Master Theorem** is a powerful tool in the Design and Analysis of Algorithm (DAA) for determining the time complexity of divide and conquer algorithms. It provides a direct way to solve recurrence relations where a problem is divided into smaller subproblems of equal size.

---

### General Form of Recurrence for Dividing Functions

The Master Theorem applies to recurrences of the form:

T(n) = a * T(n / b) + f(n)

Where:
- **T(n):** Time to solve a problem of size n.
- **a:** Number of subproblems at each step.
- **n / b:** Size of each subproblem (problem size is divided by b).
- **f(n):** Work done outside the recursive calls (e.g., dividing, combining).

---

### Master Theorem Statement

Let **T(n) = a * T(n / b) + f(n)**, where:
- **a ≥ 1** and **b > 1** are constants,
- **f(n)** is an asymptotically positive function.

Then:

1. **If** f(n) = O(n^c) where c < log_b(a):  
   **T(n) = Θ(n^log_b(a))**

2. **If** f(n) = Θ(n^c) where c = log_b(a):  
   **T(n) = Θ(n^c * log n)**

3. **If** f(n) = Ω(n^c) where c > log_b(a), and if a * f(n/b) ≤ k * f(n) for some k < 1 and sufficiently large n:  
   **T(n) = Θ(f(n))**

---

### How to Use the Master Theorem

1. Identify **a**, **b**, and **f(n)** in your recurrence.
2. Compute **log_b(a)**.
3. Compare **f(n)** to **n^log_b(a)**.
4. Apply the appropriate case from the theorem.

---

### Examples

- **Merge Sort:**  
  T(n) = 2T(n/2) + O(n)  
  Here, a = 2, b = 2, f(n) = O(n), log_2(2) = 1  
  f(n) = Θ(n^1) ⇒ Case 2 ⇒ T(n) = Θ(n log n)

- **Binary Search:**  
  T(n) = T(n/2) + O(1)  
  a = 1, b = 2, f(n) = O(1), log_2(1) = 0  
  f(n) = Θ(n^0) ⇒ Case 2 ⇒ T(n) = Θ(log n)

---

**Summary:**  
The Master Theorem gives a quick and systematic way to determine the time complexity of divide and conquer algorithms with recurrences of the form `T(n) = a * T(n / b) + f(n)`. It is widely used for analyzing algorithms like Merge Sort, Binary Search, and