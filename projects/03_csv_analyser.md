# Project 03 - CSV Analyser

Topic: Pandas EDA, Matplotlib visualisation
Author: Vishvi

---

## What it does

Load any CSV and instantly get a full EDA report:
shape, missing values, data types, distributions,
and correlation heatmap.

---

## Code

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

def analyse_csv(filepath):
    df = pd.read_csv(filepath)

    print('SHAPE:', df.shape)
    print('\nCOLUMNS:', list(df.columns))
    print('\nDATA TYPES:')
    print(df.dtypes)
    print('\nMISSING VALUES:')
    print(df.isnull().sum())
    print('\nSTATISTICS:')
    print(df.describe())

    num_cols = df.select_dtypes(include='number').columns

    df[num_cols].hist(figsize=(12, 8), bins=20, color='steelblue')
    plt.suptitle('Distributions')
    plt.tight_layout()
    plt.show()

    if len(num_cols) > 1:
        plt.figure(figsize=(10, 6))
        sns.heatmap(df[num_cols].corr(), annot=True,
                    fmt='.2f', cmap='coolwarm')
        plt.title('Correlation Heatmap')
        plt.show()

    return df

# Usage - plug in any CSV!
# df = analyse_csv('your_file.csv')
```

---

## What I learned

- reusable EDA function
- select_dtypes for filtering columns
- subplots and tight_layout
- correlation heatmap with seaborn
