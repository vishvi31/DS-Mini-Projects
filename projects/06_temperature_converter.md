# Project 06 - Temperature Converter

Topic: Functions, conditionals, user input
Author: Vishvi
Branch: feature/temperature-converter

---

## What it does

Converts temperatures between Celsius, Fahrenheit and Kelvin.
A clean example of functions with multiple return paths.

---

## Code

```python
def celsius_to_fahrenheit(c):
    return round((c * 9/5) + 32, 2)

def fahrenheit_to_celsius(f):
    return round((f - 32) * 5/9, 2)

def celsius_to_kelvin(c):
    return round(c + 273.15, 2)

def kelvin_to_celsius(k):
    return round(k - 273.15, 2)

def convert(value, from_unit, to_unit):
    units = ['C', 'F', 'K']
    if from_unit not in units or to_unit not in units:
        return 'Invalid unit. Use C, F or K.'
    if from_unit == to_unit:
        return value
    if from_unit == 'C' and to_unit == 'F':
        return celsius_to_fahrenheit(value)
    if from_unit == 'F' and to_unit == 'C':
        return fahrenheit_to_celsius(value)
    if from_unit == 'C' and to_unit == 'K':
        return celsius_to_kelvin(value)
    if from_unit == 'K' and to_unit == 'C':
        return kelvin_to_celsius(value)
    if from_unit == 'F' and to_unit == 'K':
        return celsius_to_kelvin(fahrenheit_to_celsius(value))
    if from_unit == 'K' and to_unit == 'F':
        return celsius_to_fahrenheit(kelvin_to_celsius(value))

print(convert(100, 'C', 'F'))
print(convert(212, 'F', 'C'))
print(convert(0,   'C', 'K'))
print(convert(300, 'K', 'C'))
```

---

## What I learned

- Breaking one big problem into small functions
- Chaining functions (F to K goes via C)
- Input validation with clear error messages
- This is how real world unit conversion libraries work!
