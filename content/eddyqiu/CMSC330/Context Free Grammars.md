---
title: Context Free Grammars
tags:
  - CMSC330
---
Syntax - what something looks like
Semantics - what something means
Grammar - subset of syntax

- **Nonterminal**: symbol that stands or is a placeholder of other symbols
- **Terminals**: base symbols/symbols found in alphabet
- **Production rules**: rules that declare what terminals/order of terminals nonterminals can stand for
- **Derivation**: way to prove/derive a string from a CFG
	- **Leftmost derivation:** when you expand or define the leftmost nonterminal during a derivation
	- **Rightmost derivation**: when you expand or define the rightmost nonterminal during a derivation
- **Ambiguity** - multiple ways to derive a solution
	- Not optimal, occurs if at least 2 valid leftmost derivations exist for any particular string
- Regex -> FSM like CFG -> PDA like REG -> Turing Machine

**Lexing** (tokenizing): is the process of taking a string of characters, and making sure that the string contains valid words
**Parsing**: is the process of making sure that the structures of the words is valid (making sure sentence is grammatically correct)
- There are a variety of parsers that exist
	- Left leaning and right leaning
	- Look-a-head
	- Backtracking
	- Recursive descent
	- Bottom-up
- LL(1) parser -> left leaning, look-a-head by 1 parser (via recursive descent)
	- cannot parse ambiguous grammars
	- however, ambiguous grammars can be converted to non-ambiguous grammars
- Parse tree: build a tree directly from the grammar including all non-terminals
**Evaluating**: the process of deriving meaning from a grammatically correct sentence

Lexing: string -> token list
Parsing: token list -> parse tree of abstract syntax tree
Evaluator: tree -> value | code
	interpreter: value
	compiler: code


