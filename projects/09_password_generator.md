# Project 09 - Password Generator

Topic: String operations, random module, functions
Author: Vishvi
Date: 2026-06-16

---

## What it does

Generates strong, customisable passwords.
User can choose length, and whether to include
uppercase, lowercase, numbers, and symbols.
Also checks how strong a given password is.

---

## Code

```python
import random
import string

def generate_password(length=12, use_upper=True,
                      use_lower=True, use_digits=True,
                      use_symbols=True):
    characters = ''
    required   = []

    if use_upper:
        characters += string.ascii_uppercase
        required.append(random.choice(string.ascii_uppercase))
    if use_lower:
        characters += string.ascii_lowercase
        required.append(random.choice(string.ascii_lowercase))
    if use_digits:
        characters += string.digits
        required.append(random.choice(string.digits))
    if use_symbols:
        characters += string.punctuation
        required.append(random.choice(string.punctuation))

    if not characters:
        return 'Error: Select at least one character type!'

    remaining = length - len(required)
    if remaining < 0:
        remaining = 0

    password = required + [random.choice(characters) for _ in range(remaining)]
    random.shuffle(password)
    return ''.join(password)


def check_strength(password):
    score  = 0
    checks = {
        'Length >= 8'    : len(password) >= 8,
        'Length >= 12'   : len(password) >= 12,
        'Has uppercase'  : any(c.isupper() for c in password),
        'Has lowercase'  : any(c.islower() for c in password),
        'Has digit'      : any(c.isdigit() for c in password),
        'Has symbol'     : any(c in string.punctuation for c in password),
    }

    print('Password:', password)
    print('-' * 35)
    for check, passed in checks.items():
        status = 'PASS' if passed else 'FAIL'
        print(f'  {check:<18} : {status}')
        if passed:
            score += 1

    print('-' * 35)
    if score >= 5:
        level = 'STRONG'
    elif score >= 3:
        level = 'MEDIUM'
    else:
        level = 'WEAK'
    print(f'  Strength: {level} ({score}/6)')
    print()


def generate_batch(count=5, length=12):
    print('Generated', count, 'passwords:')
    print('=' * 40)
    for i in range(1, count + 1):
        pwd = generate_password(length=length)
        print(f'  {i}. {pwd}')
    print('=' * 40)


# Generate single passwords
print('--- Single Passwords ---')
print(generate_password(length=8))
print(generate_password(length=12))
print(generate_password(length=16))
print(generate_password(length=12, use_symbols=False))
print(generate_password(length=10, use_upper=False, use_symbols=False))

# Check strength
print('\n--- Strength Checker ---')
check_strength('password123')
check_strength(generate_password(length=16))

# Generate a batch
print('--- Batch Generator ---')
generate_batch(count=5, length=14)
```

---

## Sample Output

```
--- Single Passwords ---
kR7@mP2q
Xv#9mKpL2@qN
Tj8!nRx@2KmPqL#v

--- Strength Checker ---
Password: password123
-----------------------------------
  Length >= 8           : PASS
  Length >= 12          : FAIL
  Has uppercase         : FAIL
  Has lowercase         : PASS
  Has digit             : PASS
  Has symbol            : FAIL
-----------------------------------
  Strength: WEAK (3/6)
```

---

## What I Learned

- string module: ascii_uppercase, ascii_lowercase, digits, punctuation
- random.choice() and random.shuffle() for unpredictability
- Guaranteed character types using required list
- any() with generator expression for fast character checks
- Scoring system logic same as ML threshold classification

---

## Connection to Data Science

- random module is core to train_test_split and data shuffling
- Strength scoring = same logic as multi-criteria ML evaluation
- any() + generator expressions = memory efficient data checks
- string.punctuation, digits = character-level NLP tokenisation

---

Built by Vishvi - github.com/vishvi31
