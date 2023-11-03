# LeetCodeSolution
logs for my leetcoding fall 2023



----

### Usage of list comparison: 
- set(listA) <= set(listB) can be used for list subset relationship. (e.g., Curriculum I, II)
- set() minus is useful in finding unique elements


### list arg max operation
- np.argsort (from the largest idx to the smallest idx)
```python
x = np.array([3, 1, 2])
np.argsort(x)
# array([1, 2, 0])
```

### String operators

- str.index
```python
import numpy as np
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        if needle in haystack:
            return haystack.index(needle)
        else:
            return -1
```
- str.strip() method
```python
string = '  xoxo love xoxo   '

# Leading and trailing whitespaces are removed
print(string.strip())

# All <whitespace>,x,o,e characters in the left
# and right of string are removed
print(string.strip(' xoe'))

# Argument doesn't contain space
# No characters are removed.
print(string.strip('stx'))

string = 'android is awesome'
print(string.strip('an'))


# xoxo love xoxo
# lov
#  xoxo love xoxo   
# droid is awesome
```



