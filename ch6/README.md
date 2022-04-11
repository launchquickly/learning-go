# Pointers

## A Quick Pointer Primer

> A pointer is a variable that holds the location in memory where a value is
> stored.

Every pointer, no matter what type it is pointing to, is always the same size
in terms of memory allocation.

The zero value for a pointer is `nil`.

### Pointer syntax

- `&` is the *address* operator, that returns the address of the memory
location where the value is stored
- `*` is the *indirection* operator. It precedes a variable of pointer type
and returns the pointed-to value. This is called *dereferencing*.

```go
p := "paul"
pointerToP :- &p
fmt.Println(pointerToP)             // prints memory address
fn := *pointerToP + " Kearney"
fmt.Println(fn)                     // prints Paul Kearney
```

Go gives you the *choice* to use pointers or values for both primitives and
structs. Most of the time you should use a value.

## Pointers Indicate Mutable Parameters

## Pointers Are a Last Resort

The only time you should use pointer parameters to modify a variable is when 
the function expects an interface.

## Pointer Passing Performance

## The Zero Value Versus No Value

## The Difference Between Maps and Slices

Any modifications made to a map that's passed to a function are reflected in 
the original variable that was passed. Because of this, you should **avoid**
using maps for input parameters or return values, especially on public APIs.

Use a struct instead.

Slices passed to a function are more complicated. They can have their contents
modified, but the slice can't be resized. By default, you should assume that a
slice is not modified by a function. Your documentation should specify if it 
modifies the slice's content.

## Slices as Buffers

## Reducing the Garbage Collector's Workload

Go encourages you to use pointers sparingly.