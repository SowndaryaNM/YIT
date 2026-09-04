# Java Arrays – Worksheet

### Topics

**Reverse • Shift • Rotate • Remove Elements • In-place Operations • Duplicates**

---
# PART A – TRACE & THINK

### 10 Minutes

### Q1. Reverse by Swapping

Given:

```java
int[] arr = {10, 20, 30, 40, 50, 60};
```

The following logic is intended to reverse the array:

```java
int left = 0;
int right = arr.length - 1;

while (left < right) {
    int temp = arr[left];
    arr[left] = arr[right];
    arr[right] = temp;

    left++;
    right--;
}
```

**a)** Trace the values of `left` and `right` after every iteration.

**b)** What is the final array?

**c)** Why is `left < right` used instead of `left <= right`?

**d)** Is this operation in-place? Explain.

---

### Q2. Identify the Problem

A student writes:

```java
for (int i = 0; i < arr.length; i++) {
    int temp = arr[i];
    arr[i] = arr[arr.length - i];
    arr[arr.length - i] = temp;
}
```

Answer:

**a)** What problem will occur?

**b)** Which index is invalid?

**c)** Correct the logic.

**d)** What additional problem would occur if the loop ran through the entire array even after fixing the index?

---

# PART B – REVERSE OPERATIONS

### 15 Minutes

### Q3. Reverse Only a Portion

Given:

```java
int[] arr = {10, 20, 30, 40, 50, 60, 70};
```

Reverse only the elements from index `2` to index `5`.

Expected result:

```text
10 20 60 50 40 30 70
```

Write an **in-place** solution.

**Constraint:** Do not create another array.

---

### Q4. Reverse Every Pair

Given:

```text
{1, 2, 3, 4, 5, 6, 7, 8}
```

Transform it into:

```text
{2, 1, 4, 3, 6, 5, 8, 7}
```

Now consider:

```text
{1, 2, 3, 4, 5}
```

What should the output be?

Write a generic solution that works for both even and odd-sized arrays.

---

# PART C – SHIFTING

### 15 Minutes

### Q5. Shift Elements Right

Given:

```java
int[] arr = {10, 20, 30, 40, 50};
```

Shift all elements one position to the right.

Expected:

```text
50 10 20 30 40
```

The operation must be performed **in-place**.

**Questions:**

1. Why must the loop move from right to left?
2. What would happen if you moved from left to right?
3. Modify your solution to shift the array **2 positions to the right**.

---

### Q6. Shift Elements Left

Given:

```text
{10, 20, 30, 40, 50}
```

Shift the elements one position to the left.

Expected:

```text
20 30 40 50 10
```

Write an in-place solution.

Then answer:

> Why is the direction of traversal different from Q5?

---

# PART D – ROTATION

### 20 Minutes

### Q7. Rotate Right by K

Given:

```java
int[] arr = {1, 2, 3, 4, 5, 6, 7};
int k = 3;
```

Expected:

```text
5 6 7 1 2 3 4
```

Write a solution to rotate the array **right by `k` positions**.

### Constraints

* Do not create a second array.
* `k` may be larger than the array length.
* Your solution should work for:

```text
k = 0
k = 1
k = arr.length
k > arr.length
```

### Think

Why is this necessary?

```java
k = k % arr.length;
```

---

### Q8. Rotation Without Repeated Shifting

A student solves Q7 by performing a one-position right shift `k` times.

For an array of size `n` and `k = n`, determine the approximate number of operations.

Then compare this with a solution based on **reversing parts of the array**.

Complete the idea:

For:

```text
{1, 2, 3, 4, 5, 6, 7}
```

To rotate right by `3`:

**Step 1:** Reverse __________

**Step 2:** Reverse __________

**Step 3:** Reverse __________

Final result:

```text
{5, 6, 7, 1, 2, 3, 4}
```

---

# PART E – REMOVE ELEMENTS

### 15 Minutes

### Q9. Remove an Element by Index

Given:

```java
int[] arr = {10, 20, 30, 40, 50, 60};
```

Remove the element at index `2`.

Expected logical array:

```text
10 20 40 50 60
```

Since Java arrays have fixed size:

**a)** Explain how you can represent the new logical size.

**b)** Write an in-place solution using shifting.

**c)** What value remains at the final physical position of the array?

**d)** Why should that position no longer be considered part of the logical array?

---

### Q10. Remove All Occurrences

Given:

```java
int[] arr = {10, 20, 10, 30, 40, 10, 50};
```

Remove **all occurrences of `10`**.

Expected logical result:

```text
20 30 40 50
```

You are given:

```java
int size = arr.length;
```

Modify the array **in-place** and return/update the new logical size.

### Constraint

Do not create another array.

---

# PART F – DUPLICATES

### 15 Minutes

### Q11. Count Duplicate Values

Given:

```text
{10, 20, 10, 30, 20, 40, 10}
```

Determine:

```text
10 → 3
20 → 2
30 → 1
40 → 1
```

Without using `HashMap`, write logic to identify the frequency of each distinct element.

### Follow-up

What is the time complexity of your approach?

---

### Q12. Remove Duplicates In-Place

Given:

```java
int[] arr = {10, 20, 10, 30, 20, 40, 10};
```

Modify the array so that each value occurs only once.

Expected logical result:

```text
10 20 30 40
```

### Constraints

* Do not use `HashSet`.
* Do not create another array.
* Preserve the **first occurrence order**.
* Maintain a variable representing the new logical size.

**Question:**

What is the worst-case time complexity?

---

# PART G – PLACEMENT CHALLENGE

### 10 Minutes

### Q13. Move All Zeros to the End

Given:

```java
int[] arr = {0, 5, 0, 3, 8, 0, 2};
```

Rearrange the array to:

```text
5 3 8 2 0 0 0
```

### Rules

* Preserve the relative order of non-zero elements.
* Perform the operation in-place.
* Do not create another array.

Now test your logic with:

```text
{1, 0, 2, 0, 3, 0}
{0, 0, 1, 2, 3}
{1, 2, 3}
{0, 0, 0}
```

---

# PART H – DEBUGGING CHALLENGE

### 10 Minutes

### Q14. Find and Fix the Bug

A student wants to remove duplicates:

```java
int size = arr.length;

for (int i = 0; i < size; i++) {

    for (int j = i + 1; j < size; j++) {

        if (arr[i] == arr[j]) {

            for (int k = j; k < size - 1; k++) {
                arr[k] = arr[k + 1];
            }

            size--;
        }
    }
}
```

The code fails for some inputs.

Test it with:

```text
{10, 10, 10, 20}
```

and

```text
{10, 20, 20, 20, 30}
```

**a)** Identify the problem.

**b)** Correct the code.

**c)** Explain why the inner-loop index may need to change after deletion.

---
