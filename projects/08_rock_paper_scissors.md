# Project 08 - Rock Paper Scissors Game

Topic: Random module, functions, loops, score tracking
Author: Vishvi
Date: 2026-06-07

---

## What it does

A fully playable Rock Paper Scissors game against the computer.
Tracks scores across multiple rounds and declares a winner.

---

## Code

```python
import random

def get_computer_choice():
    return random.choice(['Rock', 'Paper', 'Scissors'])

def get_winner(player, computer):
    if player == computer:
        return 'Draw'
    wins = {
        'Rock':     'Scissors',
        'Paper':    'Rock',
        'Scissors': 'Paper'
    }
    if wins[player] == computer:
        return 'Player'
    return 'Computer'

def display_round(round_num, player, computer, winner):
    print('\n--- Round', round_num, '---')
    print('You chose    :', player)
    print('Computer chose:', computer)
    if winner == 'Draw':
        print('Result       : Its a Draw!')
    elif winner == 'Player':
        print('Result       : You Win!')
    else:
        print('Result       : Computer Wins!')

def play_game(rounds=5):
    choices = ['Rock', 'Paper', 'Scissors']
    scores  = {'Player': 0, 'Computer': 0, 'Draw': 0}

    print('=' * 40)
    print('  ROCK PAPER SCISSORS')
    print('  Best of', rounds, 'rounds!')
    print('=' * 40)

    for round_num in range(1, rounds + 1):
        print('\nChoose: Rock / Paper / Scissors')
        player = input('Your choice: ').strip().capitalize()

        if player not in choices:
            print('Invalid choice! Skipping round.')
            continue

        computer = get_computer_choice()
        winner   = get_winner(player, computer)
        scores[winner] += 1
        display_round(round_num, player, computer, winner)
        print('Score -> You:', scores['Player'],
              '| Computer:', scores['Computer'],
              '| Draws:', scores['Draw'])

    print('\n' + '=' * 40)
    print('  FINAL SCORE')
    print('  You      :', scores['Player'])
    print('  Computer :', scores['Computer'])
    print('  Draws    :', scores['Draw'])
    print('=' * 40)

    if scores['Player'] > scores['Computer']:
        print('  WINNER: YOU! Well played!')
    elif scores['Computer'] > scores['Player']:
        print('  WINNER: COMPUTER! Try again!')
    else:
        print('  Its a TIE! Evenly matched!')

play_game(rounds=5)
```

---

## Sample Output

```
========================================
  ROCK PAPER SCISSORS
  Best of 5 rounds!
========================================

Choose: Rock / Paper / Scissors
Your choice: Rock

--- Round 1 ---
You chose     : Rock
Computer chose: Scissors
Result        : You Win!
Score -> You: 1 | Computer: 0 | Draws: 0
```

---

## What I Learned

- random.choice() for computer decisions
- Dictionary to store win conditions cleanly
- Score tracking with a dict across rounds
- input validation with capitalize()
- Separating logic into small focused functions

---

## Connection to Data Science

- random module is used in train_test_split, shuffling data
- Score tracking = same as accumulating metrics during model evaluation
- get_winner() logic = same thinking as writing custom scoring functions

---

Built by Vishvi - github.com/vishvi31
