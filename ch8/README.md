# Errors

Go handles errors by returning a value of type `error` as the last return value
for a function.

When a function executes as expected `nil` is returned for the error parameter.
Otherwise an `error` value is returned instead.

Creating a new error from a string:
```go
    ...
    return 0, 0, errors.New("denominator is 0)
```

Error messages:
- should not be capitalized
- should not end with punctation
- should not end with a new line
- usually other return values are set to their zero values when non-nil error is returned
    - Sentinel errors being the expection

`error` is a built-in interface taht defines a single method:

```go
type error interface {
    Error() string
}
```

## Use Strings for Simple Errors

- `errors.New` - takes a string and returns an error
- `errors.Errorf` - allows use of formatting verbs of `fmt.Printf` to create an error

## Sentinel Errors

Sentinel errors are used to indicate that you cannot start or continue processing.
They are one of the few variables that are declared at package level.

`==` is used to test for sentinel errors, e.g.

```go
    if err == zip.ErrorFormat {
        ...
    }
```

Think carefully before defining one as it becomes part of your public API. Better
to reuse existing.

Any use of one should be documented on a function

## Errors Are Values

Defining our own `errors` includes additional information for logging or `error`
handling. e.g. status codes or similar.

Still return `error` as the return type for error results as
- you can return different types of `errors`
- allows callers of the function to choose not to depend on a specific error type

> When using custom errors, never define a variable to be of the type of your
> custom error. Either explicitly return `nil` when no error occurs or define
> the variable to be of type `error`.

## Wrapping Errors

## `Is` and `As`

Use `errors.Is` to check if the returned `error`or any errors that it wrap
match a specific sentinel error instance:

```go
    ...
    if err != nil {
        if errors.Is(err, os.ErrNotExist) {
        ...
        }
    }
```

Use `errors.As` to check if the returned `error`or any errors that it wrap
match a specific type.

For custom errors you define you *may* want to consider implementing the
`Is` and/or `As` methods.

## Wrapping Errors with `defer`

This can simplify your code where you end-up wrapping multiple errors with the
same message.

## `panic` and `recover`

When a panic happens the current function exits immediately and any `defer`s
attached start to run, and so on up the call chain.

You can create your own panics using the `panic` function. 

`recover` can be used from within a `defer` to check if a panic has happened.
Once `recover` happens execution continues as normal.

Both `panic` and `recover` should be used very sparingly. One situation to use
`recover` is when creating a 3rd party library you should not let panics
escape the boundaries of your public API. `recover` can be used to convert
`panic` into an `error` and let the calling code decide what to do.

## Getting a Stack Trace from an Error

## References

- [Don’t just check errors, handle them gracefully](https://dave.cheney.net/2016/04/27/dont-just-check-errors-handle-them-gracefully)