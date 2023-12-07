---
title: OCaml
tags:
  - CMSC330
---
**Functional Programming**: a programming paradigm based on functions
Features of functional languages:
- Immutable states
	- Minimize side effects
- Declarative programming (tell what to do, not how to do it)
- Referential transparency
- Realistic about the machine

OCaml is compiled - `ocamlc file.ml`
Helpful programs:
- *ocaml*
- *utop* better 
- *dune* like Make
- *opam* package manager

- Everything is an expression (e)
	- evaluate to values (v), all values are expressions
- Statically typed, implicitly typed - very strict
	- expressions have types and must match in order to operate with each other

Example function:
```OCaml
let f x =
	if x mod 2 = 0 then
		1
	else
		0
;;
```

- function syntax: let name arg1 arg2 = e
- func x -> func y -> x + y is the same as func x y -> x + y (not the same with python lambdas)
- anonymous function syntax: fun arg1 arg2 -> e
- use rec keyword for recursive calls in a function

- default data structure - lists (linked lists)
	- [1;2;3;4], types of the entries have to be homogenous
	- lists of functions
	- cons operator 
		- 1 **::** [2;3;4] = [1;2;3;4]
		- takes in t and t list
	- append operator
		- [1;2] @ [3;4] = [1;2;3;4]
		- takes in t lists only
	- lists are recursive
		- the head is the first item, tail is the rest of the list
- **pattern matching**
	 match 3 with
	 1 -> "hello"       <- optional |
	 \| 2 -> "hye"
	 \| 3 -> "me"
	 \| x ->  "x"
	 - can use recursive definition of lists to apply match to every index
- **tuples**
	- length of tuple is its type
	- 'a * 'b
- variants
	- like enums
	- type coin = Heads | Tails (values have to start with capital letter)
	- type color = Red of int | Blue of int | Green of int
		- Red(255) - color = Red 255
	- type number = Int of int | Float of float
- scope
	- (let g x - x + 1 in (g))
		- this is a scope that g can be used in
- Closure
```OCaml
let f a b = a + b
let g = f 4 (* here the closure is created *)
g 3 (* there closure is called and evaluated *)
```
- Currying
	-  partially calling a function
- Map
```OCaml
let rec map f lst = 
	match lst with
	[] -> []
	|h::t -> (f h)::(map f t)

(* ('a -> 'b) -> 'a list -> 'b list *)
```
- Fold (reduce)
```OCaml
let rec fold f a lst = 
	match lst with
	[] -> a
	|h::t -> fold f (f a h) t

(* ('a -> 'b -> 'a) -> 'a -> 'b list -> 'a *)
```