
# Learning Journal Unit 8 CS 1101

Include the following in your Learning Journal submission: 

The input file for your original dictionary (with at least six items).
The Python program to read from a file, invert the dictionary, and write to a different file.
The output file for your inverted dictionary.
A description of how you chose to encode the original dictionary and the inverted dictionary in text files.

### Original code, unit 7
```python
running_log = {
    'day_1': [0.5, 1],        
    'day_2': [2],
    'day_3': [0.25],
    'day_4': [],
    'day_5': [0.3, 0.8],
    'day_6': [],
    'day_7': []
}
```
### Original modified function, unit 7:
```python
def invert_dict(d):
    inverse = dict()
    for key in d:
        val = tuple(d[key])
        if val not in inverse:
            inverse[val] = [key]
        else:
            inverse[val].append(key)
    return inverse
```

### Unit 8 modified function:
```python
import numpy as np
import os
import pickle

running_log = {
    'day_1': [0.5, 1],        
    'day_2': [2],
    'day_3': [0.25],
    'day_4': [11],
    'day_5': [0.3, 0.8],
    'day_6': [4],
    'day_7': [12, 16]
}

def invert_dict(d):
    inverse = dict()
    for key in d:
        val = tuple(d[key])
        if val not in inverse:
            inverse[val] = [key]
        else:
            inverse[val].append(key)
    return inverse

def save_data(data):
    with open('inverted_dict.pickle', 'wb') as fl:
        pickle.dump(data, fl, protocol = pickle.HIGHEST_PROTOCOL)

def load_data():
    with open('inverted_dict.pickle', 'rb') as fl:
        data = pickle.load(fl)
    return data

inverted = invert_dict(running_log)

save_data(inverted)

loaded = load_data()

print(loaded)
```