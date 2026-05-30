# Project 04 - BMI Calculator

Topic: Functions, conditionals, input handling
Author: Vishvi

---

## Code

```python
def calculate_bmi(weight_kg, height_m):
    bmi = weight_kg / (height_m ** 2)
    bmi = round(bmi, 2)

    if bmi < 18.5:
        category = 'Underweight'
    elif bmi < 25.0:
        category = 'Normal weight'
    elif bmi < 30.0:
        category = 'Overweight'
    else:
        category = 'Obese'

    return bmi, category

def bmi_report(name, weight, height):
    bmi, category = calculate_bmi(weight, height)
    print('Name    :', name)
    print('BMI     :', bmi)
    print('Category:', category)
    if category == 'Normal weight':
        print('Status  : Healthy range!')
    else:
        print('Status  : Consider consulting a doctor.')

bmi_report('Vishvi', 60, 1.65)
bmi_report('Rohan',  85, 1.70)
bmi_report('Priya',  45, 1.60)
```

---

## What I learned

- clean function design
- returning multiple values
- conditional category assignment
- separating logic from display
