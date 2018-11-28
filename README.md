# ECMAScript Placeholder Syntax

This proposal is for the new operator `*`. This operator is syntactic sugar for creating an anonymous function
which applies its arguments to the expression given.

## Examples
calling a prototype method:
```javascript
const lowercase = ['a','b','c']

// with placeholder syntax
const uppercase = lowercase.map(*.toUpperCase())
// without placeholder syntax
const uppercase =lowercase.map(string => string.toUpperCase())
```

passing to another expression:
```javascript
const phrases = ['hello', 'world']

// with placeholder syntax
phrases.forEach(console.log(*))
// transforms into
phrases.forEach(phrase => console.log(phrase))
```

multiple arguments:
```javascript
const numbers = [1,3,10,5]

// with placeholder syntax
const sum = numbers.reduce(* + *)
// without placeholder syntax
const sum = numbers.reduce((acc, val) => acc + val)
```

## Motivation
This proposal is simple to understand, and will cut down lines of code that do not add any more information to
the user. In addition to that, this cuts down on naming variables, which can become a pain point when larger
codebases need every variable to be explicit.

This syntax already exists in [Scala](https://docs.scala-lang.org/cheatsheets/#functions)

## Limitations
The `*` operator can only be used in the same scope that arguments are passed to a function.

## Unknowns
- Can type libraries like Flow and Typescript handle this syntax, which has to be equivalent to un-typed anonymous functions?
- does this clash with the multiply operator?
