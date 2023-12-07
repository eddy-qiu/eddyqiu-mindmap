---
title: Operational Semantics
tags:
  - CMSC330
---
- Denotational Semantics: describing through mathematical constructs
- Axiomatic Semantics: describing through promises
- Operational Semantics: describing through how things execute
- Syntax
	- Value: v
	- Expression: e
	- Environment: A
- Prove recursively
	- numbers
	- addition
		- (e1 -> n1     e2 -> n2    n3 is n1 + n2) 
		-                   (e1 + e2 -> n3)
	- Variable lookup
		- Environment separated by semicolons