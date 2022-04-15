# Types, Methods, and interfaces

In addition to structural literals, you can use any primitive type or compound
type literal to define a concrete type.

```go
type Score int
type Converter func(string)Score
type TeamScores map[string]Score
```

## Methods

Method declarations include the *receiver* specification.

## Pointer Receivers and Value Receivers

For method receivers:

- If your method modifies the receiver, you *must* use a pointer receiver.
- If your method needs to handle `nil` instances then it *must* use a pointer
receiver
- If your method doesn't modify the receiver, you can use a value receiver.

When a type has *any* pointer receiver methods, it is common practice to be 
consistent and for all methods to be pointer receivers.

## Code Your Methods for `nil` instances

## Methods Are Functions Too

## Functions Versus Methods

### Use a method if

- your logic depends on values that are configured at startup or changed while
you program is running, those values should be stored in a struct

### Use a function if

- your logic only depends on the input parameters

## Types Are Executable Documentation

Types make code clearer by providing a name for a concept and describing the 
kind of data that is expected.

e.g. when reading code it is clearer when a method has a parameter type of
`Percentage` as opposed to `int`

## `iota` is for Enumeration - Sometimes

## Use Embedding for Composition

Any fields or methods declared on an embedded field are *promoted* to the
containing struct and can be invoked directly.

```go
type Employee struct {
    Name    string
    ID      string
}

funct (e Employee) Description() string {
    return fmt.Sprintf("%s (%s)", e.Name, e.ID)
}

type Manager struct {
    Employee
    Reports []Employee
}
```

```go
m := Manager {
    Employee: Employee {
        Name:   "Peter Piper",
        ID:     "3454",
    },
    Reports:    []Employee{},
}

fmt.Println(m.ID)               // prints 3454
fmt.Println(m.Description())    // prints Peter Piper (3454)
```

## Embedding Is Not Inheritance

## A Quick Lesson on Interfaces

Interfaces are usually named with "er" endings.
```go
type Stringer interface {
    String() string
}
```

## Interfaces Are Type-Safe Duck Typing

Interfaces are implemented *implicitly*. If the method set for a concrete type
contains all of the methods in the method set for an interface, the concrete
type implements the interface.

> Interfaces specify what callers need. The client code defines the interface
> to specify what functionality it requires.

Using standard interfaces encourages the use of the *decorator pattern*.

> If there's an interface in the standard library that describes what your
> code needs, use it!

## Embedding and Interfaces

## Accept Interfaces, Return Structs

- Better for decoupling as limits dependency on 3rd-party interfaces
- Avoids versioning issues. Adding new methods to interfaces can break existing
code, the same is not true for concrete types

Errors are an exception to this rule.

## Interfaces and `nil`

In order for an interface to be considered `nil` *both* the type and the value
must be `nil`.

`nil` for interfaces indicates whether you can invoke methods on it. If an
interface is `nil` invoking a method on it triggers a panic.

## The Empty Interface Says Nothing

A way to say that a variable could store a value of any type:

```go
var i interface{}
```

## Type Assertions and Type Switches

There are 2 ways to see if a variable of an interface type has a specific
concrete type:

### 1. Type Assertions

Names the concrete type that implemented the interface

```go
i2 := i.(MyInt)
```

If you get the type wrong this will create a panic. For this reason it is
better to use the "comma ok idiom":

```go
i2, ok := i.(MyInt)
if !ok {
    return fmt.Errorf("unexpected type for %v", i)
}
.... // otherwise continue to process i2
```

### 2. Type Switches

```go
....
    switch i := i.(type)
    case nil:
        // i is nil, type is interface{}
    case int:
        // i is of type int
    case MyInt:
        // i is of type MyInt
    case io.Reader:
        // i is of type Reader
    default:
        // no idea, so i is type interface{}
```
It is idiomatic to assign the variable being switched on to a variable of the
same name. Making it one of the few places where **shadowing** is a good idea.

## Use Type Assertions and Type Switches Sparingly

## Function Types Are a Bridge to Interfaces

## Implicit Interfaces Make Dependency Injection Easier

Worked example in the book demonstrates this