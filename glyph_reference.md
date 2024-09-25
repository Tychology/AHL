- [`. dup`](#-dup)
- [`: swap`](#-swap)
- [`' over`](#-over)
- [`, dupd`](#-dupd)
- [`; swapd`](#-swapd)
- [`´ rotu`](#-rotu)
- [`` ` rotd ``](#-rotd-)
- [`" string`](#-string)
- [`# number`](#-number)
- [`! intensity`](#-intensity)
- [`⟟ get`](#-get)
- [`⍼ invoke`](#-invoke)
- [`⊏ select`](#-select)
- [`= equals`](#-equals)
- [`¬ not`](#-not)
- [`∧ and`](#-and)
- [`∨ or`](#-or)
- [`⊻ xor`](#-xor)
- [`⇔ eqvivalent`](#-eqvivalent)
- [`⇒ implies`](#-implies)
- [`∩ intersection`](#-intersection)
- [`∪ union`](#-union)
- [`⊂ subset`](#-subset)
- [`⊆ subseteq`](#-subseteq)
- [`∁ complemet`](#-complemet)
- [`→ cause`](#-cause)
- [`⊳ then`](#-then)
- [`⧅ diag`](#-diag)
- [`∀ forall`](#-forall)
- [`∃ forall`](#-forall-1)
- [`⧉ collect`](#-collect)
- [`⎀ insert`](#-insert)
- [`∵ map`](#-map)
- [`/ reduce`](#-reduce)
- [`\ scan`](#-scan)
- [`‟ quote`](#-quote)
- [`🌐 context`](#-context)
- [`📐 measure`](#-measure)
- [`ℹ IMPORT`](#-import)
- [`🔀 SWITCH`](#-switch)
- [`🗩 STATEMENT`](#-statement)
- [`❓ QUESTION`](#-question)
- [`🅰️ ANSWER`](#-answer)
- [`® SET`](#-set)


Digit modifiers below the default are invalid
Digit modifiers are one indexed

It is an error to declare a parameter outside the arity range of the operator to not be bound `∧C  error, C is outside the arity of ∧ (∧ is 2-ary)`

```
´  1 2 3 -> 2 3 1
^  ^ ^	    ^^^^^
|  | |      Effect on the stack of the operation
|  | |
|  | Second element etc...
|  Top element of the stack
Glyph of the operation

```
---
## `. dup`
1-ary (default)
Duplicates the top element of the stack.
`.  1 -> 1 1`
### Modifiers
`[0-9]` Duplicates the top x elements, where x is encoded with the digit modifiers in base ten.\
Example: `.3  1 2 3 -> 1 2 3 1 2 3`\
Default is 1, `.` is equivalent to `.1` 

---
## `: swap`
2-ary (default)\
Exchanges the positions of the top two elements.\
`:  1 2 -> 2 1`
### Modifiers
`[0-9]` Swaps the first and the xths element, where x is encoded with the digit modifiers in base ten.\
Example: `:4  1 2 3 4 -> 4 2 3 1`\
Default is 2, `.` is equivalent to `.2` 

---
## `' over`
2-ary (default)\
Duplicates the second element to the top.\
`'  1 2 -> 2 1 2`
### Modifiers
`[0-9]` Duplicates the xths element to the top.\
Example: `'4  1 2 3 4 -> 4 1 2 3 4`\
Default is 2, `'` is equivalent to `'2`

---
## `, dupd`
2-ary (default)\
Duplicates the second element under the top element.\
`,  1 2 -> 1 2 2`
### Modifiers
`[0-9]` Duplicates x elements starting with the second under the top element, where x is encoded with the digit modifiers in base ten.\
Example: `,3  1 2 3 4 -> 1 2 3 4 2 3 4`\
Default is 1, `,` is equivalent to `,1` 

---
## `; swapd`
3-ary (default)\
Exchanges the positions of the second and third element.\
`;  1 2 3 -> 1 3 2`
### Modifiers
`[0-9]` Swaps the second and the xths element, where x is encoded with the digit modifiers in base ten.\
Example: `;4  1 2 3 4 -> 1 4 3 2`\
Default is 3, `;` is equivalent to `;3` 

---
## `´ rotu`
3-ary (default)\
Rotates the positions of the first three elements, such that the middle element moves up.\
`´  1 2 3 -> 2 3 1`
### Modifiers
`[0-9]` Rotates the top x elements, such that the middle element moves up, where x is encoded with the digit modifiers in base ten.\
Example: `´5  1 2 3 4 5 -> 2 3 4 5 1`\
Default is 3, `´` is equivalent to `´3 

---
## `` ` rotd ``
3-ary (default)\
Rotates the positions of the first three elements, such that the middle element moves down.\
`` `  1 2 3 -> 3 1 2``
### Modifiers
`[0-9]` Rotates the top x, such that the middle element moves down, where x is encoded with the digit modifiers in base ten.\
Example: `` `5  1 2 3 4 5 -> 5 1 2 3 4``\
Default is 3, `` ` `` is equivalent to `` `3`` 

---
## `" string`
0-ary\
Places a string object on the stack.\
### Modifiers
`[0-9a-zA-Z]` The string is encoded using modifiers and therefore can only contain alphanumeric characters.\
Example: `"Hello  ... -> "Hello" ... `\
With no modifiers it produced the empty string.

---
## `# number`
0-ary\
Places a number object on the stack.\
### Modifiers
`[0-9A-Fxmep]`  The number is encoded using the modifiers in base ten.\
Example: `#6302  ... -> 6302 ... `

Negative numbers can be written using an m instead of the minus sign.\
Example: `#m6302  ... -> -6302 ... `

It supports hexadecimal numbers with the `0x` prefix and `[A-F]`\
Example: `#0xB00B  ... -> 45067 ... ` $"B00B"_16 = 45067_10$

Fractional numbers and scientific notation can be written with `p` for the fractional point and `e` for the exponential.\
Example: `#3p141em3  ... -> 0.0003141 ... `

The `0x` prefix turns `p` from a decimal point to a hexadecimal point and the base of the exponential `e` from 10 to 16.\
Example: `#m0xAp4Ce2  ... -> -2636 ... ` $-("A"_16*16^0 + 4_16*16^-1 + C_16*16^-2) * 16^2= -2636_10$

---
## `! intensity`
1-ary\
Adds intensity information to an object on the stack based on ten point scale 0-9, the meaning of which depends on the object.
### Modifiers
`[0-9]`  Encodes the intensity rating.\
Example: `!9  I belive... -> I am absolutely certain...`\
The default intensity is neutral and sits between 4 and 5. $<=4$ means below neutral and $>=5$ means above neutral, with 0 and 9 being the extremes.

`[A]` Don't bind the first parameter  

---
## `⟟ get`
1-ary\
Takes a string and returns the corresponding value of the context.\
Example: ``⟟  "Edward"... -> Edward...`
### Modifiers
`[A]` Don't bind the first parameter

---
## `⍼ invoke`
n-ary\
signature:`invoke(f,...)`\
Takes a function `f` and then a number of arguments equal to the arity of `f`, calls `f` with the arguments and puts the result back on the stack.

### Modifiers
`[A]` Don't bind the first parmeter (`f`). If `f` is not bound, the arity of `f` need to be specified using the digit modifiers\
``[0-9]`` Encodes the arity of `f`, only necessary if `f` is not bound.\
Default: number deduced from `f`

`[B-Z]` Don't bind some of the other parameters (the arguments for `f`).
### Errors
Error if `f` is not bound and arity of `f` is not specified.\
Error if `f` is bound but there is a mismatch between the the actual arity of `f` and specified by the modifiers.\


---
## `⊏ select`
2-ary \
signature:`select(S,p)`\
Takes a collection `S` and a predicate `p` and returns a collection with all elements of `S` for which `p` is true.


---
## `= equals`
2-ary (default)\
Declares both arguments to be equal
### Modifiers
`[0-9]` Encodes the arity in base ten.\
Example `=4  1 2 3 4 -> 1=2=3=4`\
Default is 2, `=` is equivalent to `=2` 

`[A-Z]`  Don't bind some of the parameters.

---
## `¬ not`
1-ary (default)\
Declares both arguments to be equal
### Modifiers
`[0-9]` Encodes the arity in base ten. Not is applied to all arguments separatly\
Example `¬4  1 2 3 4 -> ¬1 ¬2 ¬3 ¬4`\
Default is 1, `¬` is equivalent to `¬1`

`[A-Z]`  Don't bind some of the parameters.


---
## `∧ and`
2-ary (default)\
Comines both arguments using logical and
### Modifiers
`[0-9]` Encodes the arity in base ten.\
Example `∧4  1 2 3 4 -> 1∧2∧3∧4`\
Default is 2, `∧` is equivalent to `∧2` 

`[A-Z]`  Don't bind some of the parameters.

---

## `∨ or`
2-ary (default)\
Comines both arguments using logical inclusive or
### Modifiers
`[0-9]` Encodes the arity in base ten.\
Example `∨4  1 2 3 4 -> 1∨2∨3∨4`\
Default is 2, `∨` is equivalent to `∨2` 

`[A-Z]`  Don't bind some of the parameters.

---
## `⊻ xor`
2-ary (default)\
Comines both arguments using logical exclusive or
### Modifiers
`[0-9]` Encodes the arity in base ten.\
Example `⊻4  1 2 3 4 -> 1⊻2⊻3⊻4`\
Default is 2, `⊻` is equivalent to `⊻2` 

`[A-Z]`  Don't bind some of the parameters.


---
## `⇔ eqvivalent`
2-ary (default)\
Declares both arguments to be logically equivalent
### Modifiers
`[0-9]` Encodes the arity in base ten.\
Example `⇔4  1 2 3 4 -> 1⇔2⇔3⇔4`\
Default is 2, `⇔` is equivalent to `⇔2` 

`[A-Z]`  Don't bind some of the parameters.

---

## `⇒ implies`
2-ary\
Declares that the first argument logically implies the second.
### Modifiers
`[A-Z]`  Don't bind some of the parameters.


---
## `∩ intersection`
2-ary (default)\
Creates the intersection of two sets.
### Modifiers
`[0-9]` Encodes the arity in base ten.\
Example `∩4  1 2 3 4 -> 1∩2∩3∩4`\
Default is 2, `∩` is equivalent to `∩2` \

`[A-Z]`  Don't bind some of the parameters.


---
## `∪ union`
2-ary (default)\
Creates the union of two sets.
### Modifiers
`[0-9]` Encodes the arity in base ten.\
Example `∪4  1 2 3 4 -> 1∪2∪3∪4`\
Default is 2, `∪` is equivalent to `∪2` 

`[A-Z]`  Don't bind some of the parameters.


---
## `⊂ subset`
2-ary\
Declares both the first argument to be a strict subset of the second.
### Modifiers
`[AB]`  Don't bind some of the parameters.


---
## `⊆ subseteq`
2-ary\
Declares both the first argument to be a subset of the second.
### Modifiers
`[AB]`  Don't bind some of the parameters.


---
## `∁ complemet`
1-ary (default)\
Produces the complement of a set.
### Modifiers
`[0-9]` Encodes the arity in base ten. Complement is applied to all arguments separately.\
Example `∁4  1 2 3 4 -> 1∁ 2∁ 3∁ 4∁`\
Default is 1, `∁` is equivalent to `∁1`

`[A-Z]`  Don't bind some of the parameters.

---
## `→ cause`
2-ary\
Declares that the first argument causes the second.
### Modifiers
`[AB]`  Don't bind some of the parameters.

---

## `⊳ then`
2-ary\
Declares that the first argument happens before the second argument time wise
### Modifiers
`[AB]`  Don't bind some of the parameters.

---

## `⧅ diag`
1-ary\
Diagonalized a 2-ary function `f`, i.e. takes in a function with arity 2 and sets both parameters equal, producing a 1-ary function. It can also take a function of any arity. In this case the `[a-z]` modifiers must be used to disambiguate which parameters of `f` will be diagonalized.
### Modifiers
`[a-z]` Specify which parameters of `f` will be diagonalized. The new parameter will be inserted in the parameter list at the location of the first parameter that was diagonalized.\
Example: `⧅bd  f(w,x,y,z) -> f(w,x=z,y) `

`[A]`  Don't bind `f`.  If `f` is not bound, the arity of `f` need to be specified using the digit modifiers.

`[0-9]` Encodes the arity of `f`, only necessary if `f` is not bound.\
Default: number deduced from `f`

---

## `∀ forall`
1-ary\
Takes an 1-ary predicate `p` and declares that for all possible arguments the parameter of `p` could take, `p` is true, turning the predicate into a proposition. It can also take a predicate of any arity. In this case the `[a-z]` modifiers must be used to disambiguate which parameters of `p` will quantified. Then it returns an predicate without those parameters.
### Modifiers
`[a-z]` Specify which parameters of `p` will be quantified.\
Example: `∀bd  p(w,x,y,z) -> p(w,y) `

`[A]`  Don't bind `p`.  If `p` is not bound, the arity of `p` need to be specified using the digit modifiers.

`[0-9]` Encodes the arity of `p`, only necessary if `p` is not bound.\
Default: number deduced from `p`

---

## `∃ forall`
1-ary\
Takes an 1-ary predicate `p` and declares that there exists an argument the parameter of `p` could take, `p` is true, turning the predicate into a proposition. It can also take a predicate of any arity. In this case the `[a-z]` modifiers must be used to disambiguate which parameters of `p` will quantified. Then it returns an predicate without those parameters.
### Modifiers
`[a-z]` Specify which parameters of `p` will be quantified. \
Example: `∃bd  p(w,x,y,z) -> p(w,y) ` 

`[A]`  Don't bind `p`.  If `p` is not bound, the arity of `p` need to be specified using the digit modifiers.

`[0-9]` Encodes the arity of `p`, only necessary if `p` is not bound.\
Default: number deduced from `p`

---
## `⧉ collect`
n-ary\
Collects the top n elements of the stack into a collection, where n is given by the digit modifiers. Error if n is not given.
### Modifiers
`[0-9]` Encodes the the number of elements to collect in base ten.

---
## `⎀ insert`
n+1-ary\
Take a collection and insert the top n elements of the stack, where n is given by the digit modifiers. Error if n is not given.
### Modifiers
`[0-9]` Encodes the the number of elements to collect in base ten.

`[A]`  Don't bind the first parameter.

---
## `∵ map`
2-ary\
Takes a 1-ary function `f` and a collection `S`  , invokes `f` for each element of `S` and puts the results into a new collection.\
Example: `∵  f(x) {1, 2, 3} -> {f(1), f(2), f(3)}`
### Modifiers
`[0-9]` Encodes the the number of elements to collect in base ten.

`[AB]`  Don't bind some of the parameters.

---

## `/ reduce`
2-ary\
Takes a 2-ary function `f` and a collection `S`
Example: `∵  f(x,y) {1, 2, 3, 4} -> f(f(f(1,2) 3),4)`
### Modifiers
`[AB]`  Don't bind some of the parameters.


----
## `\ scan`
2-ary\
Takes a 2-ary function `f` and a collection `S` then does a scan operation with them. Similar to reduce, but preserves intermediate values.
Example: `∵  f(x,y) {1, 2, 3, 4} -> {1,f(1,2),f(f(1,2) 3),f(f(f(1,2),3),4)}`
### Modifiers
`[AB]`  Don't bind some of the parameters.

---

## `‟ quote`
1-ary\
Used to construct a quote context. Turns an object into a quote object, declaring that the final context is a quote from the input.

---

## `🌐 context`
1-ary
Takes an object or set of objects as a definition for a context to construct. Places that context object on the stack.

---

## `📐 measure`
2-ary\
Takes an object and a measure function and returns the result of measuring the object with the fuction.\
Example: `📐  Edward ilove(x) -> How much I love Edward`

---

## `ℹ IMPORT`

---

## `🔀 SWITCH`

---

## `🗩 STATEMENT`

---

## `❓ QUESTION`

---

## `🅰️ ANSWER`

---

## `® SET`

