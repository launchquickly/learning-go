# Primitive Types and Declarations

Go should be written:

>> in a way that makes your intentions clear.

## Literals

- Integer
  - allows you to put underscors in the middle e.g. 1_000_000
- Floating point
  - similarly allow underscores e.g. 5.000_1
- Rune
- String
  - Two kinds: 
     1. Interpreted
     2. Raw
- Complex numbers - rarely used

String literal examples that are equivalent:
- Interpreted
```go
  "Greeting and\n\"Salutations\""
```
- Raw
```go
  `Greetings and
   "Salutations"`
```

## Choosing Integer types

- If working with a binary file format or network protocol that has int specific size align with this
- If writing a library function that should work with integer types, write a pair of functions for `int64` and `uint64` - **generics may have changed this advice**
- Otherwise use `int`

## Floating point

Similar to other programming languages do not use them to represent money or any other value that must have an exact decimal representation.

## var Versus :=

If declaring multiple variables at once , you can wrap them in a **declaration list**:

```go
var (
  x     int
  y         = 20
  d, e      = 40, "hello"
)
```

Within a function, you can use `:=` to replace `var`, both the below statements do the same thing:

```go
var x = 10
x := 10
```

### Which style to use

- within a function use `:-`
  - except when initializing to its zero value, use `var x int` or similar
  - some cases involving untyped constants and similar
- outside a function user `var`
- if declaring multiple package level variables use a **declaration list**

> Avoid declaring variables outside of functions because they complicate data flow analysis

## Using const

Constants are a way to give names to literals. They do not support a value calculated at runtime.

Constants can be typed or untyped. Generally leaving a constant untyped gives more flexibility. e.g.

```go
const x = 10

var y int = x
var z float64 = x
```

not

```go
const x float64 = 10
```

## Naming Variables and Constants

- `_` is a valid character in a variable name but seldom used as Go doesn't use snake case, but camel case 
- constants in Go should **not** be uppercased as Go uses the case of the first level to determine package or public access
- favour short names, e.g. `k` and `v` for key and value.