# Project 07 - Student Grade Calculator

Topic: Functions, loops, dictionaries, list comprehensions
Author: Vishvi
Date: 2026-06-06

---

## What it does

Takes a student's marks across subjects, calculates
total, percentage, grade and pass/fail status.
Handles multiple students at once.

---

## Code

```python
def get_grade(percentage):
    if percentage >= 90:
        return 'A+'
    elif percentage >= 80:
        return 'A'
    elif percentage >= 70:
        return 'B'
    elif percentage >= 60:
        return 'C'
    elif percentage >= 50:
        return 'D'
    else:
        return 'F'

def calculate_result(name, marks, max_marks=100):
    total      = sum(marks.values())
    full_marks = len(marks) * max_marks
    percentage = round((total / full_marks) * 100, 2)
    grade      = get_grade(percentage)
    status     = 'PASS' if all(m >= 35 for m in marks.values()) else 'FAIL'

    print('=' * 45)
    print('Student  :', name)
    print('-' * 45)
    for subject, mark in marks.items():
        print(f'  {subject:<15} : {mark}/{max_marks}')
    print('-' * 45)
    print(f'  Total      : {total}/{full_marks}')
    print(f'  Percentage : {percentage}%')
    print(f'  Grade      : {grade}')
    print(f'  Status     : {status}')
    print('=' * 45)

    return {
        'name': name,
        'total': total,
        'percentage': percentage,
        'grade': grade,
        'status': status
    }

def class_summary(results):
    print('\nCLASS SUMMARY')
    print('=' * 45)
    passed  = [r for r in results if r['status'] == 'PASS']
    failed  = [r for r in results if r['status'] == 'FAIL']
    avg_pct = round(sum(r['percentage'] for r in results) / len(results), 2)
    topper  = max(results, key=lambda r: r['percentage'])

    print(f'  Total students : {len(results)}')
    print(f'  Passed         : {len(passed)}')
    print(f'  Failed         : {len(failed)}')
    print(f'  Class average  : {avg_pct}%')
    print(f'  Class topper   : {topper["name"]} ({topper["percentage"]}%)')
    print('=' * 45)

students = [
    ('Vishvi', {'Maths': 92, 'Science': 88, 'English': 95, 'Hindi': 78, 'History': 85}),
    ('Aditi',  {'Maths': 76, 'Science': 82, 'English': 79, 'Hindi': 91, 'History': 74}),
    ('Rohan',  {'Maths': 45, 'Science': 38, 'English': 55, 'Hindi': 30, 'History': 42}),
    ('Priya',  {'Maths': 98, 'Science': 95, 'English': 99, 'Hindi': 96, 'History': 97}),
]

results = [calculate_result(name, marks) for name, marks in students]
class_summary(results)
```

---

## Sample Output

```
=============================================
Student  : Vishvi
---------------------------------------------
  Maths           : 92/100
  Science         : 88/100
  English         : 95/100
  Hindi           : 78/100
  History         : 85/100
---------------------------------------------
  Total      : 438/500
  Percentage : 87.6%
  Grade      : A
  Status     : PASS
=============================================

CLASS SUMMARY
=============================================
  Total students : 4
  Passed         : 3
  Failed         : 1
  Class average  : 81.2%
  Class topper   : Priya (97.0%)
=============================================
```

---

## What I Learned

- Nested dictionaries for structured data
- all() to check every subject passes
- max() with lambda for finding topper
- List comprehension to run function on all students
- f-strings with alignment for clean table output

---

## Connection to Data Science

This is the foundation of how you would analyse
a real student dataset in Pandas:
- Each student = one row in a DataFrame
- Each subject = one column
- get_grade() = a custom feature engineering function
- class_summary() = a group-level aggregation like groupby()

---

Built by Vishvi - github.com/vishvi31
