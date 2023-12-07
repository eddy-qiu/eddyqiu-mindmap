---
title: "Higher Order Functions"
tags:
- CMSC330
---
#### Lambda Functions
`(lambda x: x + 1)`
 - Functions without names, for simple expressions
 - "anonymous functions"
 - Can use as a parameter for a function to reduce redundant code

environment: a mapping of variables to values
closure: a tuple of (code to be executed, environment related to that code)

#### map()
```python
a = [1,2,3,4]

list(map(lambda x: x + 1, a)) #have to cast back to a list
```
- Maps domain to co-domain

#### List comprehension
`[x + 1 for x in [1,2,3,4]]` returns `[2,3,4,5]`

#### reduce()
- for python 3, `from functools import reduce`
- `reduce(lambda x,y: x + y, [1,2,3,4], 0)`
					function, list, initial value
- reversing a list: `reduce(lambda x,y : [y] + x, [1,2,3,4], 0)`