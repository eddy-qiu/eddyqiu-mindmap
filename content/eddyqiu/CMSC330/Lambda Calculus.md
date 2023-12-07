---
title: Lambda Calculus
tags:
  - CMSC330
---
e -> x           x is variable
	| $\lambda$ x.e      function def - x is param e is body
	| e e         application

- left associative
	- To put parentheses
		- Around entire expression + lambdas
		- Around lambda arguments
		- Around function applications
- bound variables: variables that are referring to the parameter variable
- free variable: variables that are not bound
- $\alpha$-equivalence
	- example - ($\lambda$x.x)a equivalent to ($\lambda$b.b)a
	- not equivalent to ($\lambda$y.y)b
	- we can change bound variables, not free ones
	- bound variable can't become free, free variable can't become bound
- $\beta$-normal form: a $\lambda$-calc expression that cannot be reduced further
	- Beta-reduction: apply an argument to function
- Call by name (lazy) -> evaluate only when needed
- Call by value (eager) -> evaluate argument first
- Church encodings
	- Numbers, lists, pairs, booleans, functions