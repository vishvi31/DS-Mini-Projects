# Project 05 - Coin Flip Simulator

Topic: Probability, NumPy, Matplotlib
Author: Vishvi

---

## What it does

Simulates thousands of coin flips and shows
how probability converges to 50 percent over time.
Core concept behind every ML model evaluation.

---

## Code

```python
import numpy as np
import matplotlib.pyplot as plt

def coin_flip_simulator(n_flips=1000):
    flips = np.random.choice(['H', 'T'], size=n_flips)

    heads = np.cumsum(flips == 'H')
    total = np.arange(1, n_flips + 1)
    prob_heads = heads / total

    print('Total flips :', n_flips)
    print('Heads       :', heads[-1])
    print('Tails       :', n_flips - heads[-1])
    print('Heads pct   :', round(prob_heads[-1] * 100, 2), '%')

    plt.figure(figsize=(10, 4))
    plt.plot(total, prob_heads, color='steelblue', label='Heads probability')
    plt.axhline(0.5, color='red', linestyle='--', label='Expected 50%')
    plt.xlabel('Number of flips')
    plt.ylabel('Probability of Heads')
    plt.title('Coin Flip: Probability Convergence')
    plt.legend()
    plt.grid(True)
    plt.show()

coin_flip_simulator(1000)
```

---

## What I learned

- np.random.choice for simulations
- cumsum for running totals
- law of large numbers in action
- axhline for reference lines in plots
