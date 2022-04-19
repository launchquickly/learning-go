# The Context

Servers need a way to handle metadata on individual requests, broadly:
1. metadata that is required to correctly process the request
1. metadata on when to stop processing the request

Go uses a construct called the *context* to solve the request metadata problem.

> Contexts are used to pass information into deeper layers of the code. They 
> are **never** used to pass information out of deeper layers to higher layers.

## What Is the Context?

- a context is simply an instance that meets the `context.Context` interface
- by convention the context is explicitly passed as the first parameter of a
function
- it is usually called `ctx`
- the `context` package contains several factory functions for creating and
wrapping contexts
- `context.Background` - used when there isn't an existing context, such as
an entry point to a command-line program
- `context.TODO` is a placeholder in your code and shouldn't make it to 
production
- When writing an HTTP server, you use a different pattern for acquiring
and passing the context
    - `Context` returns the `context.Context` associated with the request
    - `WithContext` takes a `context.Context` and returns a new `http.Request`
    with the old request state combined with the supplied `context.Context`

## Cancellation

- `context.WithCancel` function creates a cancellable context and returns
    - `context.Context` - child context that wraps the parent context
    - `context.CancelFunc`- function that can cancel the context
    - you **must** call the cancel function. `defer` can be used to ensure it
    is eventually called
        - if not called then your program will leak resources

## Timers

The context provides a way to control how long a request runs.

- `context.WithTimeout` - to specify the duration when the context cancels
- `context.WithDeadline` - to specify the time when the context cancels

## Handling Context Cancellation in Your Own Code

## Values

A context can provide a way t pass per-request metadata through your program.

This should only be used where it is not possible to pass the data explicitly.

- `context.WithValue` - stores a key and its associated value
- `context.Context.Value` - retrieves a value by key

The values stored in the context can be any type there is an idiomtatic pattern
to guarantee the key's uniqueness:

```go
type userKey int        // unexported key type
const key userKey = 1   // unexported constant
```

- using unexported type and const avoids any chance of collision
- if you need to put multiple values in the context sue the `iota` pattern
- build an API to place and read the value from the context:
    - `ContextWith`ValueName to place the value in the context, 
    e.g. ContextWithUser
    - ValueName`FromContext` to read the value, e.g. UserFromContext
- make the API public only code outside the package uses them

In most cases you want to extract the value from the context and pass it to
your business logic explicitly.

There are however some situations where it's better to keep a value in the 
context. For instance a tracking GUID is not part of your business state
and passing it explicitly through your code adds additional parameters
to your business logic functions for no value.