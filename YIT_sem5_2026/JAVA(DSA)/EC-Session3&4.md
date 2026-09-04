# Java Methods + Modular Programming — 4-Hour Worksheet

### Topics Covered

* Methods
* Method declaration and calling
* Parameters
* Return values
* `void` vs value-returning methods
* Scope
* Local vs parameter variables
* Method decomposition
* Reusable methods
* Passing data to methods
* Combining multiple methods
* Designing modular solutions
* Debugging method-related problems
* Refactoring monolithic code

---

# PART 1 — WHY METHODS?

### 25 minutes

### Q1. The Repeated Code Problem

A student writes a program to process marks of three students:

```java
int total1 = m1 + m2 + m3 + m4 + m5;
double avg1 = total1 / 5.0;

int total2 = m6 + m7 + m8 + m9 + m10;
double avg2 = total2 / 5.0;

int total3 = m11 + m12 + m13 + m14 + m15;
double avg3 = total3 / 5.0;
```

**a)** What problem do you see in this approach?

**b)** If the university changes the grading rule, what problems could occur?

**c)** How could a method improve this design?

**d)** Write the method signature you would expect for calculating the average.

---

### Q2. Identify the Responsibility

Consider:

```java
System.out.println("Welcome to the placement portal");
System.out.println("Enter your marks");

int total = aptitude + coding + communication;
double percentage = total / 3.0;

if (percentage >= 70)
    System.out.println("Eligible");
else
    System.out.println("Not Eligible");
```

Identify the different **responsibilities** present in this code.

Try to divide them into separate methods.

| Responsibility          | Possible Method |
| ----------------------- | --------------- |
| Display welcome message | ?               |
| Calculate percentage    | ?               |
| Check eligibility       | ?               |

---

### Q3. Predict the Design

Which is better?

**Approach A**

```java
calculateTotal();
calculateAverage();
checkResult();
printReport();
```

**Approach B**

```java
processEverything();
```

Explain your choice from the perspective of:

1. Readability
2. Testing
3. Reusability
4. Maintenance

---

# PART 2 — METHOD BASICS

### 30 minutes

### Q4. Complete the Methods

Complete the following:

```java
static int square(int n) {
    ______________________
}

static int cube(int n) {
    ______________________
}

static boolean isEven(int n) {
    ______________________
}

static int findLarger(int a, int b) {
    ______________________
}
```

Write a `main()` method to test all four.

---

### Q5. Method Classification

For each requirement, decide whether the method should be:

* `void`
* returning `int`
* returning `double`
* returning `boolean`
* returning `String`

| Requirement                | Return Type |
| -------------------------- | ----------- |
| Display a menu             | ?           |
| Calculate total bill       | ?           |
| Check whether age is valid | ?           |
| Calculate average marks    | ?           |
| Generate student's grade   | ?           |

Give a reason for each choice.

---

### Q6. Method Signature Challenge

Write only the method signatures for:

1. Calculate area of a rectangle.
2. Calculate area of a circle.
3. Check whether a number is prime.
4. Convert Celsius to Fahrenheit.
5. Return the larger of three numbers.
6. Return `"PASS"` or `"FAIL"` based on marks.

---

# PART 3 — PARAMETERS AND RETURN VALUES

### 35 minutes

### Q7. Trace the Flow

Consider:

```java
static int add(int a, int b) {
    return a + b;
}

public static void main(String[] args) {
    int x = 10;
    int y = 20;

    int result = add(x, y);

    System.out.println(result);
}
```

Answer:

1. What are the parameters?
2. What are the arguments?
3. What value is returned?
4. Where is the returned value stored?
5. What happens to `a` and `b` after `add()` finishes?

---

### Q8. Fix the Method

The following code contains errors:

```java
static int calculateDiscount(double price) {
    if (price > 5000)
        return price * 0.10;
    else
        return 0;
}
```

Identify and fix the problem.

Then modify the method so that it returns the **discount amount as a `double`**.

---

### Q9. Method-Based Bill Calculator

A shopping application needs to calculate a customer's final bill.

Create separate methods for:

```text
calculateSubtotal()
calculateDiscount()
calculateTax()
calculateFinalAmount()
```

Assume:

* Discount = 10% if subtotal ≥ ₹5000
* GST = 18% after discount

Design the methods and call them from `main()`.

---

# PART 4 — SCOPE: WHO CAN SEE WHAT?

### 25 minutes

### Q10. Predict the Output

```java
static void display() {
    int x = 20;
    System.out.println(x);
}

public static void main(String[] args) {
    int x = 10;

    display();

    System.out.println(x);
}
```

What is the output?

Why are both `x` variables allowed?

---

### Q11. Find the Error

```java
static void calculate() {
    int total = 100;
}

public static void main(String[] args) {
    calculate();
    System.out.println(total);
}
```

Why does this fail?

How would you redesign the method so that `main()` can access the result?

---

### Q12. Scope Challenge

What happens here?

```java
static int calculate(int x) {
    int result = x * 2;
    return result;
}

public static void main(String[] args) {
    int result = calculate(10);

    System.out.println(result);
}
```

Explain why having `result` in both places does not cause a conflict.

---

# PART 5 — METHOD DECOMPOSITION

### 40 minutes

### Q13. Monolithic Program

A placement eligibility program is written as:

```java
public static void main(String[] args) {

    System.out.println("Placement Eligibility");

    int aptitude = 72;
    int coding = 68;
    int communication = 75;

    double average =
        (aptitude + coding + communication) / 3.0;

    if (average >= 70) {
        System.out.println("Eligible");
    } else {
        System.out.println("Not Eligible");
    }

    if (aptitude >= 60 &&
        coding >= 60 &&
        communication >= 60) {

        System.out.println("All section criteria satisfied");
    }
}
```

### Your task:

Break this program into meaningful methods.

Possible responsibilities:

```text
displayTitle()
calculateAverage()
isEligible()
checkSectionCriteria()
displayResult()
```

**Do not simply move lines into methods. Decide what each method should receive and return.**

---

### Q14. Method Dependency

Design the following system:

```text
Student Marks
      ↓
calculateTotal()
      ↓
calculateAverage()
      ↓
calculateGrade()
      ↓
displayResult()
```

Each method should have a clear responsibility.

Write:

1. Method signatures
2. Method implementations
3. `main()` showing how the methods interact

---

# PART 6 — THINK LIKE A DEVELOPER

### 30 minutes

### Q15. Which Design Is Better?

### Design A

```java
static void processStudent(
    int m1, int m2, int m3) {

    int total = m1 + m2 + m3;
    double avg = total / 3.0;

    if (avg >= 70)
        System.out.println("A");
    else if (avg >= 60)
        System.out.println("B");
    else
        System.out.println("C");
}
```

### Design B

```java
static int calculateTotal(int a, int b, int c) { ... }

static double calculateAverage(int total, int count) { ... }

static char calculateGrade(double average) { ... }
```

Which design would you prefer for a large application?

**Explain why.**

Then identify one situation where Design A could still be reasonable.

---

### Q16. Avoid Unnecessary Methods

A beginner creates:

```java
static int addOne(int x) {
    return x + 1;
}

static int addTwo(int x) {
    return x + 2;
}

static int addThree(int x) {
    return x + 3;
}
```

Do you consider this good modular programming?

If not, redesign it.

---

# PART 7 — DEBUGGING METHODS

### 30 minutes

### Q17. Debug the Program

Find all errors:

```java
public class Test {

    static int calculateTotal(int a, int b) {
        int total = a + b;
    }

    static void displayResult(int total) {
        System.out.println("Total = " + total);
    }

    public static void main(String[] args) {

        int result = calculateTotal(10, 20);

        displayResult();
    }
}
```

Identify:

* Compilation errors
* Method-call errors
* Return-related errors

Then provide the corrected program.

---

### Q18. Logical Bug

```java
static boolean isEligible(int marks) {

    if (marks > 40)
        return true;

    return false;
}
```

The requirement says:

> A student scoring **40 or above** is eligible.

Find the logical error.

Test your method with:

```text
39
40
41
```

---

# PART 8 — REAL-WORLD SCENARIO

### 35 minutes

## Q19. ATM Transaction System

You are developing a simple ATM application.

The program should support:

```text
1. Check Balance
2. Deposit
3. Withdraw
4. Exit
```

Design separate methods:

```java
displayMenu()
checkBalance()
deposit()
withdraw()
```

Rules:

* Deposit amount must be positive.
* Withdrawal must be positive.
* Withdrawal cannot exceed balance.

### Challenge

Instead of putting all logic inside `main()`, design the program using methods.

Think carefully about:

* What should each method receive?
* What should each method return?
* Which methods should be `void`?
* Which methods should return a value?

---

# PART 9 — METHOD COMPOSITION

### 30 minutes

## Q20. Online Food Delivery

An application needs to calculate the final amount of an order.

Requirements:

```text
Food Cost
Delivery Charge
Discount
Tax
Final Amount
```

Rules:

* Food cost > ₹1000 → 10% discount
* Food cost ≤ ₹1000 → no discount
* Delivery = ₹50
* GST = 5% on the amount after discount + delivery

Create:

```text
calculateDiscount()
calculateDeliveryCharge()
calculateTax()
calculateFinalAmount()
```

Then create a meaningful `main()`.

### Extension

What changes would be required if:

* Premium users get free delivery?
* Discount percentage changes?
* GST changes?

Your goal is to make the program easy to modify.

---

# PART 10 — FINAL CHALLENGE: REFACTOR THE SYSTEM

### 35 minutes

## Q21. Placement Readiness Analyzer

You are given the following requirement:

A company wants to shortlist students based on:

* Aptitude score
* Coding score
* Communication score
* CGPA

Eligibility rules:

```text
CGPA >= 7.0
AND
Aptitude >= 60
AND
Coding >= 60
AND
Communication >= 60
```

If eligible:

```text
Average >= 80 → "High Priority"
Average >= 70 → "Priority"
Otherwise      → "Eligible"
```

### Your task

Design the entire solution using methods.

You should have methods similar to:

```text
calculateAverage()
checkCGPA()
checkSectionScores()
isEligible()
getPriority()
displayResult()
```

### Restrictions

Do **not** write the entire solution inside `main()`.

`main()` should primarily coordinate the program.

---

# PART 11 — THINK BEYOND THE CODE

### 20 minutes

### Q22. Method Design Review

For each method below, identify whether the design is good or poor.

#### A

```java
static void calculateAverage(int a, int b, int c) {
    System.out.println((a + b + c) / 3.0);
}
```

#### B

```java
static double calculateAverage(int a, int b, int c) {
    return (a + b + c) / 3.0;
}
```

Which is more reusable?

---

### Q23. One Method, One Job?

Consider:

```java
static void processStudent() {

    // take input

    // calculate marks

    // calculate average

    // calculate grade

    // check eligibility

    // print report
}
```

Is this truly modular?

Explain the difference between:

> **Putting code inside methods**

and

> **Designing a modular program**

---

# PART 12 — INTERVIEW-STYLE QUESTIONS

### 20 minutes

Answer without running the code.

### Q24.

What is the difference between:

```java
void calculate()
```

and

```java
int calculate()
```

---

### Q25.

Why would you return a value from a method instead of printing it directly?

---

### Q26.

What is the difference between a **parameter** and an **argument**?

---

### Q27.

Can a method have multiple parameters?

Give an example.

---

### Q28.

Can a method return more than one value directly in Java?

If not, how could you design around this limitation?

---

### Q29.

Why is method decomposition useful in large software systems?

Give at least **three practical reasons**.

---
