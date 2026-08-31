# Java Generics & Object Sorting — Student Worksheet

**Topics:**
Generic Classes & Methods | Type Safety | Comparable | Comparator | Sorting Objects | Custom Comparison Logic

**Mode:** Individual / Pair Activity
**Placement Focus:** Writing reusable code, choosing the right comparison approach, reading and modifying existing Java code

---

## Part 1 — Think Before You Code | 5 Minutes

### Scenario

You are developing a placement application that stores student information.

Initially, the developer writes:

```java
ArrayList list = new ArrayList();

list.add("Rahul");
list.add(85);
list.add(92.5);
```

Later, the developer writes:

```java
String name = (String) list.get(1);
```

### Questions

**1.** What problem do you notice in the above code?

---

**2.** Why can using a raw `ArrayList` become risky in a large application?

---

**3.** How can Generics help us here?

---

---

# Part 2 — Generic Classes | 8 Minutes

### Scenario

A company wants to create a reusable `Box` class.

The box should be capable of storing different types of data:

* `String`
* `Integer`
* `Double`

Instead of creating:

```java
StringBox
IntegerBox
DoubleBox
```

the developer wants **one reusable class**.

### Task 1

Complete the generic class:

```java
class Box<______> {

    private ______ value;

    public void setValue(______ value) {
        this.value = value;
    }

    public ______ getValue() {
        return value;
    }
}
```

### Task 2

Complete the following:

```java
Box<String> nameBox = ______________________;
nameBox.setValue("Rahul");

Box<Integer> ageBox = ______________________;
ageBox.setValue(22);
```

### Think

**Why is `Box<String>` safer than simply using `Box`?**

---

---

# Part 3 — Generic Method | 7 Minutes

### Scenario

A utility method is required to print any type of data.

The developer doesn't want to write:

```java
printString()
printInteger()
printDouble()
```

Instead, one method should work for all types.

### Task

Complete the method:

```java
public static <____> void printValue(____ value) {
    System.out.println(value);
}
```

It should support:

```java
printValue("Java");
printValue(100);
printValue(25.5);
```

### Question

What is the advantage of using a **generic method** here?

---

---

# Part 4 — Comparable: Natural Ordering | 10 Minutes

### Scenario

A placement portal stores students:

```java
class Student {

    String name;
    int marks;

    Student(String name, int marks) {
        this.name = name;
        this.marks = marks;
    }
}
```

The company wants to sort students based on **marks**.

### Task 1

Which interface should `Student` implement?

```java
class Student __________________________ {
```

### Task 2

Complete the comparison logic:

```java
@Override
public int compareTo(Student other) {

    return __________________________;
}
```

### Task 3

Given:

```java
List<Student> students = new ArrayList<>();

students.add(new Student("Asha", 85));
students.add(new Student("Rahul", 72));
students.add(new Student("Vikram", 91));
```

Write the statement required to sort the students according to their natural ordering.

```java
______________________________;
```

### Think

If `compareTo()` returns:

* negative value → ______________________
* zero → ________________________________
* positive value → _______________________

---

# Part 5 — Comparator: Different Ways of Sorting | 10 Minutes

### Scenario

The HR team now says:

> "Marks are not the only thing we need. Sometimes we want to sort students by name."

The existing `Student` class already uses `Comparable` to sort by marks.

### Question 1

Should we change `compareTo()` every time HR wants a different sorting rule?

**Yes / No**

Why?

---

### Task 2

Write a `Comparator<Student>` that sorts students by **name**.

```java
Comparator<Student> byName = __________________________
```

Complete the logic:

```java
Comparator<Student> byName = (s1, s2) ->
        ________________________________;
```

### Task 3

Write the statement to sort using this comparator.

```java
students.______________________________;
```

---

# Part 6 — Custom Comparison Logic | 10 Minutes

### Scenario

A company has the following employees:

```java
class Employee {

    String name;
    double salary;

    Employee(String name, double salary) {
        this.name = name;
        this.salary = salary;
    }
}
```

The HR team wants employees sorted by:

> **Highest salary first**

### Task 1

Write a comparator using a lambda expression.

```java
Comparator<Employee> bySalary =
        (e1, e2) -> ____________________________;
```

### Task 2

Use the comparator to sort:

```java
List<Employee> employees = new ArrayList<>();

employees.add(new Employee("Arun", 45000));
employees.add(new Employee("Meena", 65000));
employees.add(new Employee("John", 52000));
```

Complete:

```java
employees.sort(________________________);
```

### Think

What would happen if you accidentally wrote:

```java
(e1, e2) -> Double.compare(e1.salary, e2.salary)
```

Would the result be:

**A. Highest salary first**

**B. Lowest salary first**

**C. No sorting**

Answer: _______

---

# Part 7 — Placement Scenario | 10 Minutes

### Scenario: Employee Shortlisting System

You are working on an employee recruitment system.

Each candidate has:

```java
class Candidate {

    String name;
    int aptitudeScore;
    int technicalScore;

    Candidate(String name, int aptitudeScore, int technicalScore) {
        this.name = name;
        this.aptitudeScore = aptitudeScore;
        this.technicalScore = technicalScore;
    }
}
```

The recruiter has the following requirements:

### Requirement 1

Sort candidates by **technical score in descending order**.

### Requirement 2

If two candidates have the same technical score, sort them by **name alphabetically**.

Example:

```text
Rahul   85
Asha    92
Vikram  85
Meena   92
```

Expected order:

```text
Asha
Meena
Rahul
Vikram
```

### Task

Write the comparator.

```java
Comparator<Candidate> ranking =
    (c1, c2) -> {

        // Compare technical score

        // If scores are equal,
        // compare candidate names

    };
```

**Bonus:** Try solving the same problem using `Comparator.comparing()` and `thenComparing()`.

---

# Part 8 — Quick Decision Check | 5 Minutes

For each situation, decide whether **Comparable** or **Comparator** is more appropriate.

| Situation                                                           | Comparable / Comparator |
| ------------------------------------------------------------------- | ----------------------- |
| Student normally sorted by roll number                              | __________              |
| Employee sometimes sorted by salary and sometimes by name           | __________              |
| Product has one obvious natural ordering by product ID              | __________              |
| Candidates need different rankings for different recruitment drives | __________              |
| Sort employees by salary without modifying the Employee class       | __________              |








This makes the topic much more placement-relevant than teaching `implements Comparable` and `compareTo()` as isolated syntax.

