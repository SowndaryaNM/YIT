# JAVA PLACEMENT WORKSHEET

## Time & Space Complexity, Big-O, Input Constraints & Optimization
**Level:** Beginner → Intermediate
**Focus:** Placement Coding + Problem-Solving Mindset

### Learning Objective

By the end of this worksheet, students should be able to:

* Understand why complexity matters.
* Identify basic Big-O complexities.
* Estimate how code behaves as input size increases.
* Use input constraints to choose an approach.
* Compare brute-force and optimized solutions.
* Understand time-space trade-offs.
* Explain complexity during an interview.

---

# PART 1 — BEFORE YOU CODE: WILL IT SCALE?

### Scenario 1: Finding a User

A college application stores the IDs of `N` users.

You need to check whether a particular user ID exists.

```java
for (int i = 0; i < n; i++) {
    if (userIds[i] == targetId) {
        System.out.println("User Found");
        break;
    }
}
```

### Questions

**Q1.** If there are 10 users, how many IDs might you have to check in the worst case?

**Q2.** If there are 1,00,000 users, what happens to the number of comparisons?

**Q3.** If there are 10 million users, would you still consider this approach?

Why?

---

**Q4.** Select the complexity:

* [ ] O(1)
* [ ] O(log N)
* [ ] O(N)
* [ ] O(N²)

**Q5.** In your own words, what does O(N) mean?

---

---

# PART 2 — COUNT THE WORK

### Scenario 2: Processing User Records

An application needs to process every user once.

```java
for (int i = 0; i < n; i++) {
    processUser(userIds[i]);
}
```

**Q1.** If `N = 100`, approximately how many times is `processUser()` called?

**Q2.** If `N = 1,000,000`?

**Q3.** What is the time complexity?

---

---

### Scenario 3: Comparing Products

An e-commerce application wants to compare every product with every other product.

```java
for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
        compare(products[i], products[j]);
    }
}
```

**Q4.** If `N = 10`, approximately how many comparisons occur?

**Q5.** If `N = 1,000`, approximately how many?

**Q6.** What is the time complexity?

---

**Q7.** Why does this become expensive as `N` increases?

---

---

# PART 3 — INPUT CONSTRAINTS MATTER

A coding problem says:

> Given an array of integers, determine whether two numbers add up to a target value.

Example:

```text
arr = [2, 7, 11, 15]
target = 9
```

Expected result:

```text
true
```

The problem gives the constraint:

```text
1 <= N <= 100
```

### Approach A — Brute Force

```java
for (int i = 0; i < n; i++) {
    for (int j = i + 1; j < n; j++) {

        if (arr[i] + arr[j] == target) {
            return true;
        }
    }
}

return false;
```

### Questions

**Q1.** What is the time complexity?

---

**Q2.** What is the additional space complexity?

---

**Q3.** Given `N <= 100`, is this solution acceptable?

Why?

---

---

Now imagine the constraint changes:

```text
1 <= N <= 1,000,000
```

**Q4.** Would you still choose the same solution?

---

**Q5.** Why does the input constraint change your decision?

---

---

# PART 4 — BRUTE FORCE VS OPTIMIZED

## Scenario 4: Detecting Duplicate Usernames

A system receives `N` usernames and needs to determine whether any username appears more than once.

Example:

```text
"alex"
"sam"
"john"
"alex"
```

The answer should be:

```text
Duplicate Found
```

### Brute-Force Approach

```java
for (int i = 0; i < n; i++) {

    for (int j = i + 1; j < n; j++) {

        if (names[i].equals(names[j])) {
            return true;
        }
    }
}

return false;
```

### Q1.

What is the time complexity?

---

### Q2.

What is the space complexity?

---

### Q3.

Would this be reasonable for:

```text
N = 50
```

Why?

---

### Q4.

Would it be reasonable for:

```text
N = 10,00,000
```

Why?

---

---

## Optimized Approach

Use a `HashSet`.

```java
HashSet<String> set = new HashSet<>();

for (String name : names) {

    if (set.contains(name)) {
        return true;
    }

    set.add(name);
}

return false;
```

### Q5.

What is the average time complexity?

---

### Q6.

What is the additional space complexity?

---

### Q7.

What did we sacrifice to improve time?

* [ ] Accuracy
* [ ] Memory
* [ ] Readability
* [ ] Input size

### Q8.

Complete the sentence:

> We improved the time complexity by using additional ____________.

---

# PART 5 — BIG-O DETECTIVE

Determine the time complexity of each code snippet.

---

### Q1 — Constant Time

```java
int first = arr[0];
System.out.println(first);
```

Complexity:

---

---

### Q2 — Linear Time

```java
for (int i = 0; i < n; i++) {
    System.out.println(arr[i]);
}
```

Complexity:

---

---

### Q3 — Quadratic Time

```java
for (int i = 0; i < n; i++) {

    for (int j = 0; j < n; j++) {

        System.out.println(arr[i] + arr[j]);
    }
}
```

Complexity:

---

---

### Q4 — Two Sequential Loops

```java
for (int i = 0; i < n; i++) {
    System.out.println(arr[i]);
}

for (int j = 0; j < n; j++) {
    System.out.println(arr[j]);
}
```

What is the complexity?

* [ ] O(N)
* [ ] O(2N)
* [ ] O(N²)
* [ ] O(1)

**Why?**

---

---

### Q5 — Repeated Doubling

```java
int i = 1;

while (i < n) {

    System.out.println(i);

    i = i * 2;
}
```

Complexity:

---

### Hint

Think about how many times you can double a number before reaching `N`.

---

# PART 6 — SEARCHING: BRUTE FORCE VS SMARTER SEARCH

## Scenario 5: Searching a Product Catalogue

You have a **sorted** array of product IDs:

```text
[101, 125, 140, 175, 201, 240, 290, 315]
```

You need to determine whether product ID `240` exists.

### Approach A — Linear Search

```java
for (int i = 0; i < n; i++) {

    if (arr[i] == target) {
        return true;
    }
}

return false;
```

### Q1.

What is the time complexity?

---

---

Now consider **Binary Search**.

The array is sorted.

Instead of checking every element, you repeatedly check the middle.

### Q2.

What is the time complexity of binary search?

* [ ] O(1)
* [ ] O(log N)
* [ ] O(N)
* [ ] O(N²)

### Q3.

Why does sorting enable us to use binary search?

---

### Q4.

Would binary search work correctly on this unsorted array?

```text
[201, 101, 315, 125, 240]
```

Why?

---

---

# PART 7 — SPACE COMPLEXITY

## Scenario 6: Processing Student Scores

You need to calculate the total score.

```java
int total = 0;

for (int i = 0; i < n; i++) {
    total += scores[i];
}
```

### Q1.

What is the time complexity?

---

### Q2.

How many additional variables are used apart from the input array?

---

### Q3.

What is the additional space complexity?

---

---

Now consider:

```java
int[] copy = new int[n];

for (int i = 0; i < n; i++) {
    copy[i] = scores[i];
}
```

### Q4.

Time complexity:

---

### Q5.

Additional space complexity:

---

### Q6.

What is the major difference between these two solutions?

---

---

# PART 8 — AIML / DATA PROCESSING SCENARIO

## Scenario 7: Duplicate Data in a Dataset

An AIML application receives `N` transaction IDs.

Example:

```text
[101, 204, 305, 101, 450]
```

Before training or analysis, the system wants to know whether duplicate transaction IDs exist.

The constraint is:

```text
1 <= N <= 1,000,000
```

### Q1.

What is your first instinct?

* [ ] Nested loops
* [ ] HashSet
* [ ] Sort and compare adjacent values
* [ ] Don't know yet

### Q2.

Give a brute-force solution idea.

---

### Q3.

What is its complexity?

---

### Q4.

Suggest an optimized approach.

---

### Q5.

What is its expected time complexity?

---

### Q6.

What is its space complexity?

---

---

# PART 9 — IoT / REAL-TIME DATA SCENARIO

## Scenario 8: Repeated Sensor Values

An IoT platform receives a stream of readings:

```text
25 27 29 31 29 30 28
```

For a particular analysis, you need to determine whether **any value occurs more than once**.

Assume:

```text
N <= 1,000,000
```

A student proposes:

> "I'll compare every reading with every other reading."

### Q1.

What is the student's approach?

---

### Q2.

What is the complexity?

---

### Q3.

Would this scale to one million readings?

---

### Q4.

Suggest a better approach.

---

### Q5.

What is the time-space trade-off?

---

---

# PART 10 — DON'T DO EXTRA WORK

## Scenario 9: Finding the Maximum

An application receives:

```text
[72, 91, 65, 88, 95, 76]
```

The requirement is simply:

> Find the highest value.

A student says:

> "I'll sort the array and take the last element."

Another student says:

> "I'll scan the array once and maintain the maximum."

### Q1.

What is the approximate complexity of sorting?

---

### Q2.

What is the complexity of scanning once?

---

### Q3.

Which solution would you choose?

---

### Q4.

Why is sorting unnecessary?

---

### Q5.

Complete the code:

```java
int max = __________________;

for (int i = 1; i < n; i++) {

    if (__________________) {

        __________________;
    }
}
```

---

# PART 11 — CONSTRAINT → COMPLEXITY

You are given the following constraints.

Choose the **most suitable target complexity**.

| Input Constraint | Preferred Approach |
| ---------------- | ------------------ |
| N ≤ 10           | __________________ |
| N ≤ 100          | __________________ |
| N ≤ 10,000       | __________________ |
| N ≤ 1,000,000    | __________________ |
| N ≤ 100,000,000  | __________________ |

Possible choices:

```text
O(1)
O(log N)
O(N)
O(N log N)
O(N²)
```

### Important Discussion

There is no rule saying:

> **"O(N²) is always bad."**

Explain why.

---

---

---

# PART 12 — FINAL PLACEMENT CHALLENGE

## Scenario 10: Online Shopping Platform

An e-commerce application receives a list of product prices.

```text
prices = [100, 250, 150, 100, 300, 250, 450]
```

The requirement is:

> Determine whether any price occurs more than once.

Constraint:

```text
1 <= N <= 1,000,000
```

### Step 1 — Understand

What exactly is the problem asking?

---

### Step 2 — Brute Force

Describe your brute-force approach.

---

### Step 3 — Complexity

Time:

---

Space:

---

### Step 4 — Scalability

Would your brute-force solution be suitable for one million elements?

Why?

---

### Step 5 — Optimize

What data structure would you use?

---

### Step 6 — Complexity

Time:

---

Space:

---

### Step 7 — Code

Write the Java solution.

```java
import java.util.*;

public class DuplicatePrices {

    public static boolean hasDuplicate(int[] prices) {

        // Write your optimized solution here


    }

    public static void main(String[] args) {

        int[] prices = {100, 250, 150, 100, 300, 250, 450};

        System.out.println(hasDuplicate(prices));
    }
}
```

---

# PART 13 — INTERVIEW ANSWER

The interviewer asks:

> **"Explain why your optimized solution is better."**

Complete the answer:

> "The brute-force approach would take approximately ____________ time because ________________________________.

> Since the input constraint is __________________, that approach may not scale well.

> I optimized the solution using __________________.

> This gives an average time complexity of __________________ while using approximately __________________ additional space."


That is much closer to what actually gets tested in placement coding rounds than memorizing definitions of O(1), O(N), O(N²), etc.
