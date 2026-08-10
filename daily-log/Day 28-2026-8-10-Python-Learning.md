# Day 28-2026-8-10-Python-Learning 代码书写




#Task1: The function of grades

def grade(score):
    if score>=90:
        return "Excellent"
    elif score>=75:
        return "Good"
    elif score>=60:
        return "Pass"
    else:
        return "Fail"

#Test three different scores
print(grade(94))
print(grade(80))
print(grade(69))

Excellent
Good
Pass




#Task2: The function of consumption

def shipping(amount):
    if amount>=99:
        return amount
    else:
        return amount+8

print(shipping(103))
print(shipping(83))

103
91




#Task3: The distance of running

weekly_km=17

if weekly_km>=20:
    print("Reach the goal")
else:
    difference=20-weekly_km
    print(f"Still need {difference} km")

Still need 3 km




**f‑string** is Python's string formatting notation, which is used to **directly insert variables into strings**.

The prefix is followed by a lowercase letter f, and the variable is placed inside the curly braces { }.

### Core rules
1.The string must start with f, and before the quotes: f"text {variable}"

2.{ } Write the variable name directly in the curly brackets, and Python will automatically take the value of the variable and fill it into the sentence.


#### 关于条件语句的一些个人语言的形容，，，

- if/elif/else works like multi-way crossroads. Once one condition is satisfied, the corresponding branch runs, and all remaining branches are skipped.

- Remember that don't forget to add English colon at the end of if/elif/else.

- Multiple conditions must be met at the same time. If you want multiple conditions to be executed, do not use elif, use multiple independent if. elif is mutually exclusive and one-to-one; Multiple separate ifs allow simultaneous hits.

2. if nested (nested if) Inside the if, continue to write if, it is nested if, used for layered judgment.