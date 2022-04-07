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
```
  "Greeting and\n\"Salutations\""
```
- Raw
```
  `Greetings and
   "Salutations"`
```

## Choosing Integer types

- If working with a binary file format or network protocol that has int specific size align with this
- If writing a library function that should work with integer types, write a pair of functions for `int64` and `uint64` - **generics may have changed this advice**
- Otherwise use `int`

## Floating point

Similar to other programming languages do not use them to represent money or any other value that must have an exact decimal representation.