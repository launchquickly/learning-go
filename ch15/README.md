# A Look at the Future: Generics in Go

## Introducing Generics in Go

```go
type Stack[T any] struct {
    vals []T
}

func (s *Stack[T]) Push(val T) {
    ...
}
```
- `any` is equivalent to `interface{}`
- `comparable` can be used where we need to compare values in generic code
e.g. `[T comparable]`
- generics make zero value handling interesting. The easiest way to get a zero
value for a generic is to simply declare a variable with `var` and return it:

```go
func (s *Stack[T]) Pop() (T, bool) {
    if len(s.vals) == 0 {
        var zero T
        return zero, false
    }
    ...
}
```

## Use Type Lists to Specify Operators

Type lists can be used to specify the types that can be substituted for a type 
parameter.

## Generic Functions Abstract Algorithms

## Type Lists Limit Constants and Implementations

## Things That Are Left Out

## Idiomatic Go and Generics

- use of `float64` to represent any numeric type can end
- `interface{}` to represent any possible value in a data structure or function
paramater is no longer necessary
- you can handle different slice types with a single function

It is not yet clear how generics will affect performance. 