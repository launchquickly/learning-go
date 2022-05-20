# Concurrency in Go

## When to Use Concurrency

> concurrency is not parallelism

- Use concurrency when you want to combine data from multiple operations that
can operate independently
- concurrency isn't worth using if the process that's running concurrently 
doesn't take a lot of time

## Goroutines

Goroutines are lightweight processes managed by the Go runtime. Benefits over
operating system managed threads and processes include:
 - creation is faster than thread creation
 - initial stack sizes are smaller meaning they can be more memory efficient
 - switching between goroutines is faster than switching between threads
 - the scheduler is able to optimise its decisions

 A goroutine is launched by placing the `go` keyword before a function
 invocation. Any values returned by the function are ignored.

 It is customary to lauch them with a closure that wraps the business logic.
 The closure taking care of the concurrent bookeeping

 ```go
func process(val int) int {
    ...
}

func runThingConcurrently(in <-chan int, out chan<- int) {
    go func() {
        for val :- range in {
            result := process(val)
            out <- result
        }
    }
}
 ```

 ## Channels

Channels are a built-in *reference* type:

```go
ch := make(chan int)
```

 ### Reading, Writing, and Buffering

 ```go
a := <-ch   // read a value from channel and assign to a
ch <- b     // write b to the channel
 ```

 - values are only read once, even if there are multiple goroutines reading from
 the same channel