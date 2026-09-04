# JAVA BASICS - SCENARIO-BASED WORKSHEET

### ECE / EEE Placement Training

**Duration:** 2 Hours
**Focus:** Think → Analyze → Code → Test

### Topics Covered

| Part    | Concept                                |
| ------- | -------------------------------------- |
| Part 1  | Understanding Java & Program Structure |
| Part 2  | Variables & Data Types                 |
| Part 3  | Input & Type Conversion                |
| Part 4  | Operators                              |
| Part 5  | if-else & Decision Making              |
| Part 6  | switch-case                            |
| Part 7  | Loops                                  |
| Part 8  | Arrays                                 |
| Part 9  | Strings                                |
| Part 10 | Methods                                |
| Part 11 | Integrated ECE/EEE Problem             |
| Part 12 | Placement Challenge                    |

---

## PART 1 — Read the Requirement First

### Scenario: Temperature Monitoring System

You are developing a small Java program for an embedded temperature-monitoring system.

The system should:

1. Accept the temperature recorded by a sensor.
2. Display the temperature.
3. If temperature is above `40°C`, display `"HIGH TEMPERATURE"`.
4. Otherwise display `"NORMAL TEMPERATURE"`.

### Q1. Before writing code, answer:

a. What information does the program need to store?

b. Which Java data type would you choose for temperature?

c. Which programming concept is required to decide between HIGH and NORMAL?

d. What input would you expect from the user?

---

### Q2. Write the Java program.

Expected interaction:

```text
Enter temperature: 42.5

Temperature: 42.5
HIGH TEMPERATURE
```

---

### Q3. What happens if the user enters:

```text
35.5
```

Write the expected output.

---

## PART 2 — Variables & Data Types

### Scenario: Motor Monitoring

An electrical motor monitoring system stores the following information:

```text
Motor ID       → 105
Motor Name     → Pump Motor
Voltage        → 230.5
Current        → 4.8
Running        → true
```

### Q4. Choose the most appropriate Java data type for each.

| Information    | Data Type |
| -------------- | --------- |
| Motor ID       | ______    |
| Motor Name     | ______    |
| Voltage        | ______    |
| Current        | ______    |
| Running status | ______    |

---

### Q5. Declare variables for the above information.

---

### Q6. Calculate the approximate power using:

**Power = Voltage × Current**

Write Java code to calculate and display the power.

Expected result:

```text
Power = 1106.4 W
```

---

## PART 3 — Input from the User

### Scenario: Battery Testing

A battery-testing application asks the user to enter:

* Battery voltage
* Battery current
* Battery temperature

### Q7. Write a Java program using `Scanner` to accept these three values.

The program should display:

```text
Battery Voltage: 12.5 V
Battery Current: 2.4 A
Battery Temperature: 32.5 C
```

---

### Q8. The user enters:

```text
12
2
30
```

Calculate the power using:

```text
Power = Voltage × Current
```

What should the program display?

---

## PART 4 — Operators

### Scenario: Energy Consumption

An electrical device consumes:

```text
Power = 1000 W
Operating Hours = 5
```

Energy consumed is calculated as:

```text
Energy = Power × Hours
```

### Q9. Write Java code to calculate energy consumption.

---

### Q10. A device has:

```text
Power = 750 W
Hours = 8
```

Calculate the energy consumed.

---

### Q11. A placement interviewer gives you:

```java
int a = 10;
int b = 3;

System.out.println(a / b);
System.out.println(a % b);
```

What is the output?

Explain **why** the second result occurs.

---

## PART 5 — Decision Making

### Scenario: Motor Safety System

A motor is considered safe to operate only when:

```text
Temperature <= 70
Current <= 10
```

Otherwise, the system should display:

```text
Motor Shutdown Required
```

### Q12. Write a Java program that accepts temperature and current.

Use an `if-else` statement to determine whether the motor is safe.

---

### Q13. Test your program with:

**Case 1**

```text
Temperature = 60
Current = 8
```

Output:

```text
Motor Safe
```

**Case 2**

```text
Temperature = 75
Current = 8
```

What should the output be?

---

### Q14. Modify the condition.

The motor should be safe **only when both conditions are satisfied**.

Which operator should you use?

```text
&&
||
!
```

Explain your choice.

---

## PART 6 — Multiple Decisions

### Scenario: Signal Strength

A communication device measures signal strength.

| Signal Strength | Status    |
| --------------- | --------- |
| >= 80           | Excellent |
| >= 60           | Good      |
| >= 40           | Average   |
| < 40            | Poor      |

### Q15. Write a Java program using `if-else-if` to display the signal status.

---

### Q16. What will your program display for:

```text
Signal Strength = 72
```

---

### Q17. What will happen if the input is:

```text
Signal Strength = 25
```

---

## PART 7 — switch-case

### Scenario: Electrical Measurement Menu

Create a menu:

```text
1. Voltage
2. Current
3. Resistance
4. Power
```

The user enters a choice.

### Q18. Write a Java program using `switch-case`.

For example:

```text
Enter choice: 3

You selected Resistance
```

---

### Q19. What should happen if the user enters:

```text
5
```

Add a suitable `default` case.

---

## PART 8 — Loops

### Scenario: Sensor Readings

A temperature sensor records readings for **5 consecutive measurements**.

The program should accept 5 temperature values and display each one.

### Q20. Which loop would you choose?

```text
for
while
do-while
```

Why?

---

### Q21. Write a Java program using a `for` loop to accept 5 temperature readings.

Example:

```text
Enter temperature 1: 32
Enter temperature 2: 34
Enter temperature 3: 35
Enter temperature 4: 36
Enter temperature 5: 38
```

---

### Q22. Modify the program to calculate the average temperature.

For the above readings:

```text
32 34 35 36 38
```

What is the average?

---

### Q23. Modify the program so that it counts how many readings are above `35°C`.

Expected result:

```text
Readings above 35: 2
```

---

## PART 9 — Arrays

### Scenario: Voltage Analysis

A testing system stores voltage measurements:

```text
220
225
218
230
227
```

### Q24. Store these values in an integer array.

---

### Q25. Write a Java program to display all voltage readings.

Expected:

```text
220
225
218
230
227
```

---

### Q26. Write a program to calculate the average voltage.

---

### Q27. Write a program to find the highest voltage.

Expected:

```text
Highest Voltage = 230
```

---

### Q28. Write a program to count how many voltage readings are greater than `220`.

---

## PART 10 — Strings

### Scenario: Component Identification

An electronics inventory system stores the component name:

```text
"ESP32"
```

### Q29. Write Java code to:

a. Store the component name.

b. Display its length.

c. Convert it to lowercase.

d. Check whether it equals `"ESP32"`.

---

### Q30. Consider:

```java
String component = "Resistor";
```

What will each statement produce?

```java
System.out.println(component.length());
System.out.println(component.toUpperCase());
System.out.println(component.charAt(0));
```

---

## PART 11 — Methods

### Scenario: Power Calculation

You have noticed that your program repeatedly calculates power.

Instead of writing the calculation repeatedly, create a method.

### Q31. Create a method:

```java
calculatePower()
```

that accepts:

```text
voltage
current
```

and returns:

```text
power
```

---

### Q32. Call your method using:

```text
Voltage = 230
Current = 5
```

Expected:

```text
Power = 1150
```

---

### Q33. Why is using a method better than repeatedly writing:

```java
power = voltage * current;
```

throughout a large program?

Write **two advantages**.

---

# PART 12 — INTEGRATED ECE/EEE PROBLEM

## Scenario: Power Monitoring System

You are developing a basic power-monitoring program for an electrical panel.

The system receives **5 voltage readings**.

Example:

```text
220
225
230
218
240
```

The program must:

1. Store the readings in an array.
2. Display all readings.
3. Find the highest voltage.
4. Find the lowest voltage.
5. Calculate the average voltage.
6. Count how many readings are above `230V`.
7. Display `"WARNING"` if any reading is above `240V`.
8. Otherwise display `"SYSTEM NORMAL"`.

### Q34. Identify the concepts required.

Tick the concepts you would need:

```text
[ ] Variables
[ ] Scanner
[ ] if-else
[ ] switch
[ ] for loop
[ ] Array
[ ] String
[ ] Method
```

---

### Q35. Draw the logic before coding.

Complete:

```text
START
   ↓
Read ______ voltage readings
   ↓
Store readings in ______
   ↓
Find highest and ______
   ↓
Calculate ______
   ↓
Check readings above ______
   ↓
Check whether any reading is above ______
   ↓
Display result
   ↓
END
```

---

### Q36. Write the complete Java program.

Test with:

```text
220
225
230
218
240
```

---

# PART 13 — PLACEMENT-STYLE DEBUGGING

This section is intentionally different. **Do not immediately run the code. First predict the problem.**

### Q37. Find the error.

```java
int voltage = 230;
double current = 5;

int power = voltage * current;

System.out.println(power);
```

What is wrong?

How would you correct it?

---

### Q38. Predict the output.

```java
int temperature = 45;

if (temperature > 40)
    System.out.println("HIGH");
else
    System.out.println("NORMAL");
```

---

### Q39. Predict the output.

```java
int x = 10;

for(int i = 1; i <= 3; i++) {
    x = x + 5;
}

System.out.println(x);
```

---

### Q40. Find the logical error.

```java
int current = 8;

if(current > 10);
{
    System.out.println("Overload");
}
```

Why might this program produce an unexpected result?

---

# PART 14 — PLACEMENT CHALLENGE

### Scenario: Smart Motor Diagnostic System

You are asked to create a simple diagnostic program for a motor.

The system accepts:

```text
Motor Temperature
Motor Current
Motor Voltage
```

The program should calculate:

```text
Power = Voltage × Current
```

Then apply these rules:

### Rule 1

If temperature > `80°C`:

```text
CRITICAL TEMPERATURE
```

### Rule 2

Otherwise, if current > `10A`:

```text
OVERLOAD
```

### Rule 3

Otherwise, if power > `2000W`:

```text
HIGH POWER CONSUMPTION
```

### Rule 4

Otherwise:

```text
MOTOR OPERATING NORMALLY
```

### Q41. Identify the sequence of concepts required.

---

### Q42. Write the complete Java program.

---

### Q43. Test your program using:

| Temperature | Current | Voltage | Expected Status |
| ----------: | ------: | ------: | --------------- |
|          85 |       5 |     230 | __________      |
|          60 |      12 |     230 | __________      |
|          60 |       5 |     450 | __________      |
|          60 |       5 |     230 | __________      |

---

# FINAL 10-MINUTE THINKING ROUND

Do **not** write code immediately.

### Q44.

You are given this requirement:

> "Read 10 sensor readings and determine how many are above the acceptable limit."

What concepts would you use?

---

### Q45.

You are given:

> "Store the names of 20 electronic components and search whether a particular component exists."

What concepts would you use?

---

### Q46.

You are given:

> "Calculate the power of 100 different devices."

Would you write the power calculation 100 times?

If not, what Java concept would you use?

---

### Q47.

A recruiter asks:

> **"What is the difference between a variable and an array?"**

Answer in your own words.

---

### Q48.

A recruiter asks:

> **"Why do we need loops?"**

Give a practical answer rather than a textbook definition.

---

### Q49.

A recruiter asks:

> **"What is the difference between `==` and `.equals()` when working with Strings?"**

Write what you currently understand.

---
