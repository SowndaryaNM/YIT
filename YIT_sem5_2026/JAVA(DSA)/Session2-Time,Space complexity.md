# JAVA PLACEMENT WORKSHEET

## Time & Space Complexity • Big-O • Input Constraints • Brute Force vs Optimized

---

# PART 1 — CODE ANALYSIS

## Scenario 1: Processing Application Logs

An application receives `N` log entries. The following code checks whether each log entry contains a particular keyword.

```java
for (int i = 0; i < n; i++) {

    for (int j = 0; j < logs[i].length(); j++) {

        if (logs[i].charAt(j) == 'E') {
            System.out.println("Found");
            break;
        }
    }
}
```

Assume:

* `N` = number of log entries
* `M` = maximum length of a log entry

### Questions

**Q1.** Is the complexity simply `O(N)`?

**Q2.** Express the time complexity in terms of both `N` and `M`.

**Q3.** What is the worst-case complexity if every log has length `M`?

**Q4.** If:

```text
N = 1,000,000
M = 500
```

approximately how many character checks could occur in the worst case?

**Q5.** Does the `break` guarantee that the inner loop is O(1)?

Explain.

---

# PART 2 — NESTED LOOP WITH A TWIST

## Scenario 2: Recommendation System

A recommendation engine compares users with other users.

```java
for (int i = 0; i < n; i++) {

    for (int j = i + 1; j < n; j++) {

        if (users[i].equals(users[j])) {
            System.out.println("Match");
        }
    }
}
```

### Questions

**Q1.** How many comparisons occur when:

```text
N = 5
```

**Q2.** How many comparisons occur when:

```text
N = 100
```

**Q3.** Derive the approximate number of comparisons for `N` users.

**Q4.** What is the Big-O complexity?

**Q5.** Why is this not `O(N × N)` exactly, although the Big-O is `O(N²)`?

---

# PART 3 — MULTIPLE INPUT SIZES

## Scenario 3: Image Dataset

An AIML application processes:

* `N` images
* Each image has `P` pixels

```java
for (int i = 0; i < N; i++) {

    for (int j = 0; j < P; j++) {

        processPixel(images[i][j]);
    }
}
```

### Questions

**Q1.** What is the time complexity?

* [ ] O(N)
* [ ] O(P)
* [ ] O(N + P)
* [ ] O(N × P)

**Q2.** If:

```text
N = 10,000
P = 1,000,000
```

approximately how many pixel-processing operations occur?

**Q3.** Which variable is more important when estimating the total work: `N`, `P`, or both?

**Q4.** Why is writing only `O(N)` incorrect?

---

# PART 4 — SEQUENTIAL COMPLEXITY

## Scenario 4: Data Pipeline

A data-processing system performs three operations.

```java
for (int i = 0; i < n; i++) {
    clean(data[i]);
}

for (int i = 0; i < n; i++) {
    transform(data[i]);
}

for (int i = 0; i < n * n; i++) {
    validate(data[i % n]);
}
```

### Questions

**Q1.** Determine the complexity of each section.

| Section        | Complexity |
| -------------- | ---------- |
| Cleaning       | ______     |
| Transformation | ______     |
| Validation     | ______     |

**Q2.** What is the overall complexity?

**Q3.** Why don't we write:

```text
O(N + N + N²) = O(3N²)
```

as the final answer?

**Q4.** Which section dominates when `N` becomes very large?

---

# PART 5 — INPUT CONSTRAINTS DECISION

## Scenario 5: Pair Sum

You need to determine whether two numbers add up to a target.

```text
arr = [4, 8, 1, 6, 9, 3]
target = 10
```

Possible approaches:

### Approach A

Nested loops → `O(N²)`

### Approach B

Sort + two pointers → `O(N log N)`

### Approach C

HashSet → average `O(N)`

Now consider the following constraints.

### Case A

```text
N <= 20
```

### Case B

```text
N <= 10,000
```

### Case C

```text
N <= 1,000,000
```

### Questions

**Q1.** Which approach would you choose for Case A?

Why?

**Q2.** Which approach would you choose for Case B?

**Q3.** Which approach would you choose for Case C?

**Q4.** Is the `O(N)` solution automatically the best solution in every case?

Explain.

**Q5.** What additional consideration might make you prefer sorting + two pointers over HashSet?

---

# PART 6 — SPACE COMPLEXITY WITH A TRAP

## Scenario 6: Processing Transactions

```java
HashSet<Integer> seen = new HashSet<>();

for (int id : transactionIds) {

    if (seen.contains(id)) {
        return true;
    }

    seen.add(id);
}
```

### Questions

**Q1.** What is the average time complexity?

**Q2.** What is the worst-case additional space complexity?

**Q3.** Suppose all transaction IDs are unique. Approximately how many values could the HashSet store?

**Q4.** Suppose the first two transaction IDs are duplicates.

Does the HashSet still necessarily contain `N` elements?

Explain.

**Q5.** Is the space complexity still described as O(N)?

Why?

---

# PART 7 — HIDDEN O(N²)

## Scenario 7: Frequency Analysis

A student writes:

```java
for (int i = 0; i < n; i++) {

    int count = 0;

    for (int j = 0; j < n; j++) {

        if (arr[i] == arr[j]) {
            count++;
        }
    }

    System.out.println(arr[i] + " occurs " + count + " times");
}
```

The student claims:

> "There is only one `count` variable, so the algorithm is O(N)."

### Questions

**Q1.** Is the student's claim correct?

**Q2.** What is the time complexity?

**Q3.** What is the additional space complexity?

**Q4.** Why does the number of variables have nothing to do with the time complexity here?

**Q5.** Suggest a data structure that could reduce the repeated work.

---

# PART 8 — SORTING VS HASHING

## Scenario 8: Duplicate Detection

You have:

```text
N = 1,000,000
```

You need to determine whether duplicates exist.

Three approaches are proposed.

| Approach                     |         Time |        Extra Space |
| ---------------------------- | -----------: | -----------------: |
| Nested loops                 |        O(N²) |               O(1) |
| Sort then compare neighbours |   O(N log N) | Depends on sorting |
| HashSet                      | O(N) average |               O(N) |

### Questions

**Q1.** Which approach has the best average time complexity?

**Q2.** Which approach uses the least additional memory?

**Q3.** If memory is severely limited, which approach might become attractive?

**Q4.** What is the fundamental trade-off between sorting and HashSet?

**Q5.** If the array is already sorted, does the sorting-based approach still need O(N log N) sorting?

Why?

---

# PART 9 — EARLY TERMINATION

## Scenario 9: Searching a Large Dataset

Consider:

```java
for (int i = 0; i < n; i++) {

    if (arr[i] == target) {
        return true;
    }
}

return false;
```

### Questions

**Q1.** What is the best-case complexity?

**Q2.** What is the worst-case complexity?

**Q3.** What is the Big-O complexity usually reported for this algorithm?

**Q4.** If the target is found at index `2`, how many comparisons are required?

**Q5.** Why doesn't early termination change the worst-case Big-O?

---

# PART 10 — LOGARITHMIC THINKING

## Scenario 10: Server Capacity Search

A system stores sorted server-capacity values.

```java
int low = 0;
int high = n - 1;

while (low <= high) {

    int mid = (low + high) / 2;

    if (arr[mid] == target) {
        return true;
    }
    else if (arr[mid] < target) {
        low = mid + 1;
    }
    else {
        high = mid - 1;
    }
}

return false;
```

### Questions

**Q1.** What happens to the search space after each iteration?

**Q2.** Approximately how many elements remain after one iteration?

**Q3.** After two iterations?

**Q4.** What is the time complexity?

**Q5.** What property must the input have for this algorithm to work correctly?

**Q6.** What happens if the array contains 1 billion elements? Why can this still be efficient?

---

# PART 11 — COMPLEXITY COMPARISON

Arrange the following from **fastest growth to slowest growth** as `N` becomes very large.

```text
O(N²)
O(1)
O(N log N)
O(log N)
O(N)
```

### Answer

1. ---
2. ---
3. ---
4. ---
5. ---

### Follow-up

Which one grows the fastest?

---

Which one grows the slowest?

---

---

# PART 12 — FIND THE BUG IN THE ANALYSIS

A student analyzes this code:

```java
for (int i = 0; i < n; i++) {

    for (int j = 0; j < 100; j++) {

        System.out.println(arr[i]);
    }
}
```

The student says:

> "There are two loops, therefore complexity is O(N²)."

### Questions

**Q1.** Is the student correct?

**Q2.** What is the actual complexity?

**Q3.** Why does the inner loop not make this O(N²)?

**Q4.** What if the inner loop changed to:

```java
for (int j = 0; j < n; j++)
```

What would the complexity become?

---

# PART 13 — BRUTE FORCE → OPTIMIZATION

## Scenario 11: Two Numbers With Maximum Difference

Given:

```text
arr = [7, 1, 5, 3, 6, 4]
```

Find the maximum value of:

```text
arr[j] - arr[i]
```

where:

```text
j > i
```

### Example

For:

```text
i = 1 → arr[i] = 1
j = 4 → arr[j] = 6
```

Difference:

```text
6 - 1 = 5
```

---

### Step 1 — Brute Force

Describe the brute-force approach.

---

### Step 2

What is its time complexity?

---

### Step 3

Can we solve this in O(N)?

**Yes / No**

### Step 4

What information should we maintain while scanning?

---

### Step 5

Describe the optimized idea without writing code.

---

---

# PART 14 — BRUTE FORCE VS OPTIMIZED: REAL PLACEMENT SCENARIO

## Scenario 12: Log Monitoring

A monitoring system receives:

```text
N = 500,000
```

log records.

Each record contains:

```text
userId
timestamp
status
```

The requirement is:

> Find whether any user has generated two logs with the same `userId`.

A student proposes:

```java
for (int i = 0; i < n; i++) {

    for (int j = i + 1; j < n; j++) {

        if (logs[i].userId == logs[j].userId) {
            return true;
        }
    }
}
```

### Questions

**Q1.** What is wrong with this approach?

**Q2.** Approximately what is its worst-case time complexity?

**Q3.** Suggest an optimized data structure.

**Q4.** What would be the average time complexity?

**Q5.** What would be the additional space complexity?

**Q6.** Explain the optimization in **three interview sentences**.

---

# PART 15 — ADVANCED COMPLEXITY ANALYSIS

## Scenario 13

Consider the following:

```java
for (int i = 1; i <= n; i *= 2) {

    for (int j = 0; j < n; j++) {

        System.out.println(i + " " + j);
    }
}
```

### Questions

**Q1.** How many times does the outer loop execute?

**Q2.** What is the outer loop complexity?

**Q3.** What is the inner loop complexity?

**Q4.** What is the total complexity?

* [ ] O(N)
* [ ] O(log N)
* [ ] O(N log N)
* [ ] O(N²)

**Q5.** Explain your answer.

---

# PART 16 — ADVANCED: NARROWING LOOP

## Scenario 14

Analyze:

```java
for (int i = 0; i < n; i++) {

    for (int j = i; j < n; j++) {

        System.out.println(i + " " + j);
    }
}
```

### Questions

**Q1.** Does the inner loop execute exactly `N` times for every value of `i`?

**Q2.** Approximately how many total iterations occur?

**Q3.** What is the Big-O complexity?

**Q4.** Why is the answer still O(N²)?

---

# PART 17 — FINAL DECISION CHALLENGE

## Scenario 15: Online Coding Platform

You are given a problem:

> Given `N` integers, determine whether any two numbers have the same value.

The constraints are:

```text
Case 1: N <= 20

Case 2: N <= 5,000

Case 3: N <= 1,000,000
```

You have three approaches:

### Approach A

Nested loops

```text
Time: O(N²)
Space: O(1)
```

### Approach B

Sort + adjacent comparison

```text
Time: O(N log N)
Space: depends on implementation
```

### Approach C

HashSet

```text
Average Time: O(N)
Space: O(N)
```

### Your Decision

| Constraint    | Choice | Reason             |
| ------------- | ------ | ------------------ |
| N ≤ 20        | ______ | __________________ |
| N ≤ 5,000     | ______ | __________________ |
| N ≤ 1,000,000 | ______ | __________________ |

---

# PART 18 — INTERVIEW THINKING

The interviewer gives you a problem.

You immediately think of a brute-force solution.

Should you immediately discard it?

**Yes / No**

Explain:

---

---

---

The interviewer asks:

> **"Why did you optimize your solution?"**

Give a placement-level answer:

---

---

---

---

# FINAL CHALLENGE — NO OPTIONS GIVEN

## Scenario 16: Student Activity Analytics

An application records the IDs of students who logged into a platform during the day.

Example:

```text
[101, 205, 101, 310, 205, 450, 500]
```

The application needs to determine:

1. Whether a student logged in more than once.
2. The number of unique students.

Constraints:

```text
1 <= N <= 1,000,000
```

### Q1.

What is the most obvious brute-force approach?

---

### Q2.

What is its time complexity?

---

### Q3.

What data structure would you use for an optimized solution?

---

### Q4.

What is the average time complexity?

---

### Q5.

What is the additional space complexity?

---

### Q6.

Write the Java code.

```java
import java.util.*;

public class StudentAnalytics {

    public static void main(String[] args) {

        int[] studentIds = {
            101, 205, 101, 310, 205, 450, 500
        };

        // Your solution

    }
}
```

### Q7.

What should the output be?

**Unique students:** __________

**Duplicate exists:** __________

---



This version is considerably better for a **mixed CSE/ISE/IoT/AIML placement batch** because it tests whether students can *reason about an algorithm*, rather than simply identify that "nested loop = O(N²)."
