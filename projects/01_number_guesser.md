# Project 01 - Number Guesser

Topic: Python logic, loops, conditionals
Author: Vishvi

---

## What it does

A game where the computer picks a random number
and the user guesses it. Gives hints after each guess.

---

## Code

```python
import random

def number_guesser():
    number = random.randint(1, 100)
    attempts = 0
    max_attempts = 7

    print('Guess the number between 1 and 100!')
    print('You have', max_attempts, 'attempts.')

    while attempts < max_attempts:
        guess = int(input('Your guess: '))
        attempts += 1

        if guess == number:
            print('Correct! You got it in', attempts, 'attempts!')
            return
        elif guess < number:
            print('Too low! Attempts left:', max_attempts - attempts)
        else:
            print('Too high! Attempts left:', max_attempts - attempts)

    print('Game over! The number was', number)

number_guesser()
```

---

## What I learned

- random module
- while loops with a counter
- input validation
- early return vs loop exit
