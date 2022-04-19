# Writing Tests

## The Basics of Testing

- `testing` package in standard library provides support for writing tests
- *go test* tool run the tests and generates reports
- Go tests are placed in the same directory and package as production code
- Every test is written in a file whose name ends with *_test.go*
- Test functions start with the word *Test* and take a single parameter
    `t *testing T`
- Naming convention is to include the name of the function being tested
after *Test*  e.g. 
    - for exported functions TestAddNumbers
    - for unexported functions Test_addNumbers

## Reporting Test Failures

Test marked as failed but continues to run:
- `Error` 
- `Errorf` - additional formatting options

Test stops processing:
- `Fatal` 
- `Fatalf` - additional formatting options

## Setting Up and Tearing Down

`TestMain` - used to set up before tests are run and clean up after
    - only invoked once, not per test
    - only allowed one per package

`Cleanup` method can be used to clean up temporary resources created
by a single test. As can in most case `defer`.

## Storing Sample Test Data

- Create a subdirectory called *testdata* in the relevant package
- Use relative file references

## Caching Test Results

## Testing Your Public API

- keep your source code in the same directory as the production code
- name your package `packagename_test`

## Use go-cmp to Compare Test Results

[go-cmp](https://github.com/google/go-cmp)
- `cmp.Diff` - compares 2 instances of a compound type
- `cmp.Comparer` - creates a custome comparator

## Table Tests

- parameterised, data driven tests

## Checking Your Code Coverage

```bash
go test -cover                          // run code coverage
go test -cover -coverprofile=c.out      // save coverage info to a file
go tool cover -html=c.out               // identify where coverage is missing
```

## Benchmarks

Go's testing framework has built in benchmarking support.

Benchmarks are functions in your test files that start with *Benchmark* and
take a single parameter `b *testing.B`.

If benchmarking reveals a performance or memory problem the next step is to
investigate it. A good starting point on profiling with Go is:
[Profiling Go programs with pprof](https://jvns.ca/blog/2017/09/24/profiling-go-with-pprof/)

## Stubs in Go

## httptest

The Go standard library includes `net/http/httptest` package to make it easier
to stub HTTP services.

## Integration Tests and Build Tags

*build tags* can be used to control when code is compiled. This can be used for
splitting tests into groups. 

```go
// +build integration
```

Tests without build tags run all the time. Tests with build tags are run 
similar to:

```bash
go tst -tags integration -v ./..
```

## Finding Concurrency Problems with the Race Checker
