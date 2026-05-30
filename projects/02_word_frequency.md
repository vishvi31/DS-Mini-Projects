# Project 02 - Word Frequency Counter

Topic: NLP basics, dictionaries, Collections
Author: Vishvi

---

## What it does

Takes any text and returns the most common words.
Foundation of every NLP project including the
Disneyland Sentiment Analysis project.

---

## Code

```python
from collections import Counter
import re

def word_frequency(text, top_n=10):
    text = text.lower()
    text = re.sub(r'[^a-z\s]', '', text)
    words = text.split()

    stop_words = {'the','a','an','and','or','but',
                  'in','on','at','to','for','is','it',
                  'of','this','that','was','with','are'}

    words = [w for w in words if w not in stop_words]
    counts = Counter(words)

    print('Top', top_n, 'words:')
    for word, count in counts.most_common(top_n):
        bar = '#' * count
        print(f'{word:<15} {count:>3}  {bar}')

    return counts

sample = '''
Data science is the study of data to extract
meaningful insights. Data science uses scientific
methods, algorithms, and systems to extract knowledge
from data in various forms. Data is everywhere.
'''

word_frequency(sample)
```

---

## What I learned

- Counter from collections
- regex for text cleaning
- stopword removal
- formatted print output
