---
title: Regular Expressions
tags:
  - CMSC330
---
- There is a minimum language needed to solve a problem
- Regular Expression: a pattern that describes a set of strings (REGEX)
	- Used to describe regular languages
- | - OR symbol
	- grey | gray
	- gr(e | a)y
- {} - repeat
	- (0,1){2} repeat twice
	- (0,1){2,5} repeat 2-5 times
- Kleene Operator
	- {"", "ha", "haha", "hahaha", ...} => (ha)*
- ASCII ranges
	- [0-9]
	- [A-Z]
	- [a-z]
	- [A-Za-z]
- ^ - negate (when used inside a bracket environment)
- + - one or more repeats
- ? - one or zero repeats
- . - any character
- ^ outside of bracket - starts with (left side)
- $ outside of bracket - ends with (right side)
- These are all shortcuts - all based on | and concatenation
- Python
	- Needs the re module
```Python
import re

my_re = re.compile("[0-9]+/.[0-9]+")
if(my_re.match("12.3")):
	print("successful")
else
	print("unsuccessful")
```
- .group()
	- returns the string corresponding to each match group
	- use () to "parse" match groups (parentheses will show precedence and group capture)
