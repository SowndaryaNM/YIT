# Java Collections — Student Worksheet

### Mode: Individual / Pair Activity

**Topics:**
ArrayList vs LinkedList • HashSet • TreeSet • HashMap • TreeMap • Iterator • Enhanced for loop • Common Collection Methods

### Learning Objective

By the end of this activity, you should be able to:

* Identify **when** to use different collection types.
* Explain **why** one collection is preferable over another.
* Predict the output/behavior of collection operations.
* Write small programs using Java Collections.
* Select an appropriate collection for a real-world requirement.

---

# PART 1 — WHAT? Observe Before Coding

### ⏱ 15 minutes

### Activity 1: Think About Real Life

Imagine you are designing applications for the following situations.

For each situation, decide what kind of data structure you would naturally want.

| Situation                                                                  | What would you need?        | Your Choice |
| -------------------------------------------------------------------------- | --------------------------- | ----------- |
| 1. Store marks of 50 students in the order they were entered               | Ordered, duplicates allowed | __________  |
| 2. Store unique employee IDs                                               | No duplicates required      | __________  |
| 3. Store employee names in alphabetical order without duplicates           | Unique + sorted             | __________  |
| 4. Store `employeeId → employeeName`                                       | Key-value relationship      | __________  |
| 5. Store product IDs and automatically maintain them in sorted order       | Key-value + sorted keys     | __________  |
| 6. Maintain a list where frequent insertions/removals happen in the middle | Frequent insertion/removal  | __________  |

### Activity 2: Predict

Without running the program:

```java
ArrayList<Integer> numbers = new ArrayList<>();

numbers.add(10);
numbers.add(20);
numbers.add(10);
numbers.add(30);

System.out.println(numbers);
System.out.println(numbers.size());
```

**Q1.** What will be printed?

Answer:

```text
____________________________________
____________________________________
```

**Q2.** Are duplicate values allowed in an `ArrayList`?

☐ Yes
☐ No

**Q3.** What do you think will happen with the following?

```java
HashSet<Integer> numbers = new HashSet<>();

numbers.add(10);
numbers.add(20);
numbers.add(10);
numbers.add(30);

System.out.println(numbers);
System.out.println(numbers.size());
```

Output:

```text
____________________________________
____________________________________
```

**Q4.** What changed compared with `ArrayList`?

```text
____________________________________
____________________________________
```

---

# PART 2 — WHY? Compare and Reason

### ⏱ 20 minutes

## Activity 3: ArrayList vs LinkedList

Consider this requirement:

> A university application maintains 10,000 student records. Students are frequently added and removed from the **beginning and middle** of the collection.

### Q1. Which would you initially choose?

☐ ArrayList
☐ LinkedList

### Q2. Why?

```text
____________________________________________________
____________________________________________________
```

Now consider:

> An application frequently accesses students using an index:

```java
students.get(5000);
students.get(7000);
students.get(9000);
```

Which would you prefer?

☐ ArrayList
☐ LinkedList

Why?

```text
____________________________________________________
____________________________________________________
```

### Activity 4: Complete the Comparison

| Feature                                      | ArrayList | LinkedList |
| -------------------------------------------- | --------- | ---------- |
| Maintains insertion order                    | ______    | ______     |
| Allows duplicates                            | ______    | ______     |
| Fast random/index access                     | ______    | ______     |
| Better suited for frequent insertion/removal | ______    | ______     |
| Uses index-based access                      | ______    | ______     |

### Think Like an Interviewer

An interviewer asks:

> "Why shouldn't I simply use `LinkedList` everywhere if insertion is faster?"

Write your answer:

```text
____________________________________________________
____________________________________________________
____________________________________________________
```

---

# PART 3 — SETS: WHAT PROBLEM DO THEY SOLVE?

### ⏱ 15 minutes

## Activity 5: Duplicate Detector

You are given:

```java
String[] names = {
    "Ravi", "Anu", "Ravi", "Kiran",
    "Anu", "Meena", "John"
};
```

The requirement is:

> Display each name only once.

### Q1. Which collection would you choose?

```text
____________________
```

### Q2. Write the program.

```java
_______________________________________________
_______________________________________________
_______________________________________________
_______________________________________________
_______________________________________________
```

### Activity 6: HashSet vs TreeSet

Consider:

```java
HashSet<Integer> h = new HashSet<>();

h.add(50);
h.add(10);
h.add(30);
h.add(20);
h.add(40);
```

And:

```java
TreeSet<Integer> t = new TreeSet<>();

t.add(50);
t.add(10);
t.add(30);
t.add(20);
t.add(40);
```

### Q1. What is the important difference between them?

```text
HashSet:
_____________________________________________

TreeSet:
_____________________________________________
```

### Q2. Which one would you use for:

> "Display unique employee IDs in ascending order."

Answer:

```text
____________________
```

### Q3. Why not use `HashSet`?

```text
____________________________________________________
```

---

# PART 4 — MAPS: KEY → VALUE THINKING

### ⏱ 20 minutes

## Activity 7: Student Marks

You need to store:

```text
101 → 85
102 → 92
103 → 76
104 → 88
```

where:

```text
Student ID → Marks
```

### Q1. Which collection would you use?

☐ ArrayList
☐ HashSet
☐ HashMap
☐ TreeSet

Why?

```text
____________________________________________________
```

### Q2. Create the `HashMap`.

```java
_______________________________________________
_______________________________________________
_______________________________________________
```

### Q3. Add the four students.

```java
_______________________________________________
_______________________________________________
_______________________________________________
_______________________________________________
```

### Q4. Retrieve the marks of student `103`.

```java
_______________________________________________
```

### Q5. Change student `102`'s marks from `92` to `95`.

```java
_______________________________________________
```

### Q6. Check whether student `105` exists.

```java
_______________________________________________
```

---

# PART 5 — HashMap vs TreeMap

### ⏱ 10 minutes

You have:

```java
HashMap<Integer, String> employees = new HashMap<>();
```

and

```java
TreeMap<Integer, String> employees = new TreeMap<>();
```

Both contain:

```text
105 → Ravi
101 → Anu
103 → Kiran
102 → Meena
104 → John
```

### Q1. Which one would you choose if the employee IDs must always appear in ascending order?

```text
____________________
```

### Q2. Complete the statement:

> `HashMap` is useful when ________________________________

> `TreeMap` is useful when ________________________________

### Q3. Predict the conceptual difference:

```text
HashMap → ___________________________________

TreeMap → ___________________________________
```

---

# PART 6 — ITERATOR: CONTROLLED TRAVERSAL

### ⏱ 15 minutes

Consider:

```java
ArrayList<String> names = new ArrayList<>();

names.add("Ravi");
names.add("Anu");
names.add("Kiran");
names.add("Meena");
```

## Activity 8

Complete the code:

```java
Iterator<String> it = __________________________;

while(__________________________) {

    String name = __________________________;

    System.out.println(name);
}
```

### Activity 9: Iterator + Removal

You want to remove `"Kiran"` while traversing the collection.

Try:

```java
Iterator<String> it = names.iterator();

while(it.hasNext()) {

    String name = it.next();

    if(name.equals("Kiran")) {
        __________________________;
    }
}
```

### Think

Why is using `Iterator.remove()` safer than directly modifying the collection while traversing it?

```text
____________________________________________________
____________________________________________________
```

---

# PART 7 — ENHANCED FOR LOOP

### ⏱ 10 minutes

The following code uses an `Iterator`:

```java
Iterator<String> it = names.iterator();

while(it.hasNext()) {
    String name = it.next();
    System.out.println(name);
}
```

Rewrite it using an enhanced `for` loop.

```java
_______________________________________________
_______________________________________________
_______________________________________________
```

### Q2. Which is easier to read?

☐ Iterator
☐ Enhanced for loop

### Q3. When might you prefer an Iterator?

```text
____________________________________________________
____________________________________________________
```

---

# PART 8 — COMMON COLLECTION METHODS

### ⏱ 10 minutes

Given:

```java
ArrayList<String> fruits = new ArrayList<>();

fruits.add("Apple");
fruits.add("Mango");
fruits.add("Orange");
fruits.add("Apple");
```

Complete the table.

| Requirement                    | Method     |
| ------------------------------ | ---------- |
| Add an element                 | __________ |
| Find number of elements        | __________ |
| Remove an element              | __________ |
| Check whether `"Mango"` exists | __________ |
| Retrieve element at index 2    | __________ |
| Replace element at index 1     | __________ |
| Remove everything              | __________ |

### Activity 10: Predict the Output

```java
System.out.println(fruits.size());

System.out.println(fruits.contains("Mango"));

System.out.println(fruits.get(2));

fruits.remove("Apple");

System.out.println(fruits);
```

Output:

```text
____________________________________
____________________________________
____________________________________
____________________________________
```

---

# PART 9 — REAL-WORLD CHALLENGE

### ⏱ 15 minutes

## Scenario: Employee Skill Management System

Your company wants a simple Java program to manage employee skills.

Employee:

```text
Employee ID → Employee Name
```

Skills:

```text
Java
SQL
Python
Java
HTML
SQL
```

The requirements are:

1. Store employees using employee ID.
2. Employee IDs should be maintained in ascending order.
3. Store employee skills without duplicates.
4. Display all employees.
5. Display all unique skills.
6. Search whether an employee exists.
7. Remove a skill.
8. Traverse the collections and display their contents.

### Your Task

Choose the appropriate collection for each requirement.

| Requirement                      | Collection |
| -------------------------------- | ---------- |
| Employee ID → Employee Name      | __________ |
| Sorted employee IDs              | __________ |
| Unique skills                    | __________ |
| Unique + sorted skills           | __________ |
| Ordered list allowing duplicates | __________ |

---

# PART 10 — BUILD IT

### ⏱ 20 minutes

Now implement the following mini application.

### Expected Output

Your program should be able to produce something similar to:

```text
EMPLOYEES
101 → Anu
102 → Ravi
103 → Kiran
104 → Meena

UNIQUE SKILLS
HTML
Java
Python
SQL

SEARCH
Employee 103 exists: true

AFTER REMOVAL
HTML
Java
Python
```

### Step 1 — Create the employee collection

```java
// Your code
```

### Step 2 — Add at least 4 employees

```java
// Your code
```

### Step 3 — Create the skill collection

Add at least 6 skills, including **at least two duplicates**.

```java
// Your code
```

### Step 4 — Display employees using enhanced `for`

```java
// Your code
```

### Step 5 — Display skills using an Iterator

```java
// Your code
```

### Step 6 — Search for an employee

```java
// Your code
```

### Step 7 — Remove one skill using Iterator

```java
// Your code
```

### Step 8 — Display the final result

```java
// Your code
```

---

# PART 11 — FINAL THINKING ROUND

### ⏱ 10 minutes

Do **not** look at your notes.

For each requirement, choose the best collection and justify your decision.






