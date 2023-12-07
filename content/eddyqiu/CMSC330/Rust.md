---
title: Rust
tags:
  - CMSC330
---
- Made to be secure, fine grain control of memory but doesn't let you malloc/free
- Has static typing, prefers explicit typing
- The default value or return type of an empty codeblock is unit
	- Codeblocks can have statements and one (return) expression
	- {}: unit
	- end with statement -> returns and unit, end with expression, returns expression
- **Safety**
	- Immutable variables by default, use mut keyword to make mutable
	- No Garbage Collector (costly, space and runtime tradeoffs) and allows for mutability makes Rust low-level but safe
	- #### **Ownership**
		- Each value in Rust has an owner
		- Only one owner at a time
		- When owner goes out of scope, the value will be dropped
		- really only impacts heap values (still applied to stack)
		- .clone() creates a deep copy, which also has ownership
		- **Borrowing**
			- let c = &a; <- immutable reference
			- let c = &mut a;  <- mutable reference
		- #### **Rule of references:**
			1. **every reference must be valid**
			2. **there can be infinitely many immutable references XOR there can be only 1 mutable reference**
- **structs**
	- can be a tuple without value "names"
	- **impl** keyword to implement methods or override attributes like "clone" and "drop" etc.
```Rust
struct Shape {
	length: i32,
	width: i32,
}
 // mutability is associated with variables, not values

let mut shape1 = Shape {
						length: 4, 
						width: 6, 
						}
```
- pattern matching exists
- enums
- #### **Lifetimes**
	- a "timeframe" of when a variable is created to the time it's last used
	- lifetime of variable can differ from the lifetime of the value
		- ie, let b = String::from("hello");
			- b's lifetime ends when it is last used
			- the value "hello"'s lifetime ends when it goes out of scope
	- sometimes the same as scope, but not always
	- all references in rust have an implicit lifetime parameter
	- the rule of references does not apply if the lifetime of a reference ends before the original reference is used again
	- Rust makes a lifetime as part of a reference's type
	- Few rules of lifetime inference: **Lifetime Elision**
		- Compiler is not all-knowing, could need a little help
		- Rust's compiler needs to figure out 3 rules. If insufficient, then the programmer needs to help it out
		- **Rule 1**: For every input reference: a different lifetime is assigned
		- **Rule 2**: If there is only 1 input reference and the output is also a reference, then the lifetime of the return value is the same as the input
		- **Rule 3**: If there is more than 1 input reference, but one of them is &self (or &mut self) and the return value is a reference, then the return value has the same lifetime as self
		- Adding explicit lifetime parameters does not change the actual lifetime of anything, it just tells the Rust compiler what you are expecting
	```Rust 
	fn invalid(x:&i32, y:&i32) -> &i32 {} // this will not compile
	
	// examples of valid headers
	fn valid1(x:&'a i32, y:&'b i32) -> &'a i32 {} // cannot return y
	
	fn valid2(x:&'a i32, y:&'b i32) -> &'b i32 {} // cannot return x
	
	fn valid3(x:&'a i32, y:&'a i32) -> &'a i32 {} 
	// accurate way to think: return value must live as long as the two inputs
	// or the two inputs must live as long as the return value
	// (opposed to x, y, and return have the same lifetime)
	```
- **Smart pointers**
	- ie let x = String::from("hello")
	- usually implemented using structs, implements Deref and Drop traits
	- Box\<T> is a special type of smart pointer
		- Allocated on heap rather than stack
- **Traits**
	- similar to "interfaces" in other languages
	- guarantees behavior based on traits
	- Abstracts low level properties to larger level viewpoint