# Functions

## Multiple Return Values

By convention, the `error` is always the last (or only) value returned from a
function.

## Ignored Returned Values

Use `_`.

## Named Return Values

## Blank Returns - Never Use These!

If your function returns values, *never* use a blank return. It makes it 
difficult to work out what is actually returned.

## Functions Are Values

## Function Type Declarations

It can be useful to give something a name if you are going to refer to it,
multiple times.

```go
type ofFuncType func(int, int) int
```

## Anonymous Functions

Mostly useful for `defer` statements, or launching goroutines.

## Closures

Closures are functions declared inside of other functions. This allows the
function declared inside to access and modify variables declared in the 
outer function.

Using closures also limits a function's scope and reduce the number of 
declarations at the package level.

## Passing Functions as Parameters

> Passing functions as parameters to other functions is often useful
> for performing different operations on the same kind of data.

## Returning Functions from Functions

## `defer`

Used to automatically release resources. Teh code within `defer` closures
runs *after* the return statement.

The best reason to use named return values is to allow access to the `defer`
function

```go
func DoSomething(...) (err error) {
    ...
    defer func() {
        if err == byk {
            err = tx.Commit()
        }
        if err != nil {
            tx.Rollback()
        }
    }()
    ...
}
```

## Go Is Call By Value

This is for primitives and structs.

Maps and slices exhibit slightly different behaviour. This is because
they are implemented with pointers.

> Every type in Go is a value type. It's just sometimes the value is a pointer.