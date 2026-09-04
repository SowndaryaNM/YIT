# Java Arrays – Logic & Problem-Solving Worksheet

**Duration:** 1.5 Hours
**Level:** Medium → Upper Medium
**Focus:** Traversal, Indexing, Searching, Min/Max, Sum, Counting, Frequency
**Restriction:** Unless explicitly mentioned, do **not** use `Arrays.sort()`, `HashMap`, `HashSet`, or streams.

---

## Part 1 — Array Reasoning

### Q1. Maximum and Its Position

Given:

```java
int[] arr = {45, 82, 91, 67, 91, 38, 76};
```

Write a program to find:

* Maximum value
* Index of the **first occurrence** of maximum
* Index of the **last occurrence** of maximum
* Number of times maximum occurs

Expected:

```text
Maximum: 91
First Index: 2
Last Index: 4
Frequency: 2
```

**Constraint:** One traversal only.

---

### Q2. Second Largest — Without Sorting

Given:

```java
int[] arr = {12, 45, 7, 89, 34, 89, 56};
```

Find the **second largest distinct element**.

Expected:

```text
Second Largest: 56
```

Now test your logic with:

```java
{10, 10, 10, 8, 7}
```

and

```java
{5, 5, 5}
```

What should your program do when a second distinct value doesn't exist?

---

### Q3. Minimum and Maximum in One Traversal

Given:

```java
int[] arr = {34, 12, 78, 5, 90, 23, 5, 67};
```

Find:

* Minimum
* Maximum
* Index of minimum
* Index of maximum
* Difference between maximum and minimum

**Constraint:** Only one traversal.

---

# Part 2 — Search With Conditions

### Q4. First and Last Occurrence

Given:

```java
int[] arr = {4, 7, 2, 7, 9, 7, 3, 7, 1};
```

For a given target `7`, find:

```text
First occurrence: 1
Last occurrence: 7
Total occurrences: 4
```

**Challenge:** Do this using only **one traversal**.

---

### Q5. Search for the Largest Value Greater Than X

Given:

```java
int[] arr = {15, 42, 8, 67, 23, 91, 34};
```

Given `X = 30`, find the **smallest array value greater than X**.

Expected:

```text
Smallest value greater than 30: 34
```

For:

```text
X = 90
```

what should happen?

**Important:** Don't sort the array.

---

### Q6. Nearest Value

Given:

```java
int[] arr = {10, 25, 40, 55, 70, 85};
```

Given a target:

```text
Target = 48
```

Find the array element whose value is **closest to 48**.

Expected:

```text
Closest value: 40
```

Now test:

```text
Target = 62
```

What happens?

---

# Part 3 — Counting With Multiple Conditions

### Q7. Placement Eligibility Analyzer

A company has the following student scores:

```java
int[] scores = {45, 72, 88, 91, 56, 39, 72, 95, 61, 48, 88};
```

A student is eligible if the score is:

* At least `60`
* But scores `90+` are considered **premium candidates**

Find:

1. Total eligible students
2. Number of premium candidates
3. Number of students between `60–89`
4. Highest eligible score
5. Lowest eligible score

**Constraint:** Use a single traversal.

---

### Q8. Count Consecutive Values

Given:

```java
int[] arr = {5, 5, 5, 2, 2, 8, 8, 8, 8, 3};
```

Find the **longest consecutive repetition**.

Expected:

```text
Value: 8
Consecutive Count: 4
```

Now test:

```java
{1, 2, 3, 4, 5}
```

What should the result be?

---

### Q9. Longest Increasing Streak

Given:

```java
int[] arr = {10, 12, 15, 14, 18, 20, 22, 17, 19};
```

Find the length of the **longest continuously increasing sequence**.

For example:

```text
18, 20, 22
```

has length `3`.

Expected:

```text
Longest increasing streak: 3
```

**Think:** You are not looking for the longest increasing subsequence. The elements must be **consecutive**.

---

# Part 4 — Frequency Problems

### Q10. Most Frequent Element

Given:

```java
int[] arr = {4, 2, 7, 4, 2, 4, 7, 8, 2, 2};
```

Find the element occurring most frequently.

Expected:

```text
Most frequent: 2
Frequency: 4
```

**Restriction:** No `HashMap`.

### Challenge

If two elements have the same highest frequency:

```java
{4, 4, 7, 7, 2}
```

return the **smaller value**.

Expected:

```text
Element: 4
Frequency: 2
```

---

### Q11. Frequency Greater Than Once

Given:

```java
int[] arr = {10, 20, 10, 30, 40, 20, 10, 50, 30};
```

Print all elements that occur more than once **without printing duplicates in your output**.

Expected:

```text
10 → 3
20 → 2
30 → 2
```

**Restriction:** No HashMap/HashSet.

---

# Part 5 — Array + Search Logic

### Q12. Pair With a Given Sum

Given:

```java
int[] arr = {8, 3, 5, 2, 7, 4};
```

Given:

```text
Target = 10
```

Determine whether there are **two different elements** whose sum equals `10`.

Expected:

```text
Pair found: 3 + 7
```

### Follow-up

What is the time complexity of your approach?

Can you think of a way to solve this more efficiently if the array were sorted?

**Do not implement the optimized version yet. Just explain the idea.**

---

# Part 6 — Position-Based Problems

### Q13. Local Maximum

An element is called a **local maximum** if it is greater than both its immediate neighbors.

Given:

```java
int[] arr = {5, 9, 7, 12, 15, 10, 8, 11, 6};
```

Identify all local maxima.

Expected:

```text
9
15
11
```

**Important:** The first and last elements don't have two neighbors, so don't consider them.

---

### Q14. Find the First Valley

A valley is an element that is smaller than both its immediate neighbors.

Given:

```java
int[] arr = {10, 8, 12, 15, 7, 9, 11};
```

Find the **first valley**.

Expected:

```text
8
```

Return its index as well.

---

# Part 7 — Scenario Problem

## Q15. Website Traffic Analyzer

A website records hourly visitors:

```java
int[] visitors = {
    120, 145, 160, 160, 132,
    180, 210, 210, 195, 175,
    220, 220, 220, 180
};
```

Build an analyzer that determines:

### A.

Total visitors.

### B.

Peak visitors in an hour.

### C.

First hour at which peak traffic occurred.

### D.

Number of hours where traffic exceeded `200`.

### E.

Frequency of the peak traffic value.

### F.

Longest consecutive period where traffic was **at least 180**.

### G.

Whether traffic ever increased for **three consecutive hours**.

For example:

```text
120 → 145 → 160
```

is an increasing streak of 3 hours.

---

# Part 8 — Placement-Level Challenge

## Q16. Second Most Frequent Element

Given:

```java
int[] arr = {
    4, 2, 4, 7, 2, 9, 4,
    7, 2, 7, 7, 5
};
```

Find the **second most frequent element**.

Expected frequency ranking:

```text
7 → 4
4 → 3
2 → 3
9 → 1
5 → 1
```

If frequencies are tied, choose the **smaller value**.

Therefore:

```text
Second most frequent element: 2
Frequency: 3
```

**Restriction:** No sorting, HashMap, HashSet, or collections.

---

# Part 9 — Debugging & Optimization

## Q17. Find the Logical Error

A student wants to find the second largest element:

```java
int[] arr = {10, 50, 30, 40, 50};

int largest = arr[0];
int second = arr[0];

for(int i = 1; i < arr.length; i++) {

    if(arr[i] > largest) {
        second = largest;
        largest = arr[i];
    }
}

System.out.println(second);
```

The student expects:

```text
40
```

but gets:

```text
40
```

Now test:

```java
{10, 50, 50, 40, 30}
```

The logic fails to correctly handle **duplicate maximum values**.

Modify the algorithm so that "second largest" means **second largest distinct value**.

---

## Q18. Complexity Comparison

Two students solve a frequency problem.

### Student A

For every element, they scan the entire array to count its frequency.

### Student B

They build frequency information once and then use it.

Answer:

1. What is the likely time complexity of Student A?
2. Why can repeated scanning become expensive?
3. What data structure would normally be appropriate for Student B?
4. Why might an interviewer still ask you to solve it without that data structure?

---

# Part 10 — Final Integrated Challenge

## Q19. Sales Intelligence

A company records the number of products sold by different sales representatives:

```java
int[] sales = {
    12, 18, 7, 25, 18,
    30, 7, 22, 25, 30,
    18, 15, 30, 9
};
```

Write a program that produces:

```text
Total Sales: ______

Highest Sales: ______
Highest Sales Frequency: ______

Lowest Sales: ______
Lowest Sales Frequency: ______

Second Highest Distinct Sales: ______

Most Frequent Sales Value: ______
Most Frequent Count: ______

Number of Representatives Above Average: ______
```

That's much closer to the type of array logic that starts appearing in **coding rounds and placement assessments**.
