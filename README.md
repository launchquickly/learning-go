# learning-go

Notes and code examples created whilst following the [Learing Go](https://www.oreilly.com/library/view/learning-go/9781492077206/) 
book. 

This book by Jon Bodner aims to teach "An Idiomatic Approach to Real-World Go Programming".

## Chapters

1. [Setting Up Your Go Environment](/ch1/README.md)
   - Go development set-up
   - Code Style
   - IDE's
   - Makefiles
   - Staying Up to Date
   - Code examples
1. [Primitive Types and Declarations](/ch2/README.md)
   - Literals
   - Choosing Integer types
   - Floating point
   - `var` Versus `:=`
   - Using `const`
   - Naming Variables and Constants
1. [Composite Types](/ch3/README.md)
   - Arrays
   - Slices
   - Maps
   - Using Maps as Sets
   - Structs
1. [Blocks, Shadows, and Control Structures](/ch4/README.md)
   - Blocks
   - Shadowing Variables
   - Detecting Shadowed Variables
   - `if`
   - `for`, Four Ways
   - The `for`-`range` Statement
   - Choosing the Right `for` statement
   - `switch`
   - Blank Switches
   - Choosing Between `if` and `switch`
1. Functions
   - Multiple Return Values
   - Ignored Returned Values
   - Named Return Values
   - Blank Returns - Never Use These!
   - Functions Are Values
   - Function Type Declarations
   - Anonymous Functions
   - Closures
   - Passing Functions as Parameters
   - Returning Functions from Functions
   - `defer`
   - Go Is Call By Value
1. Pointers
   - A Quick Pointer Primer
   - Pointer syntax
   - Pointers Indicate Mutable Parameters
   - Pointers Are a Last Resort
   - Pointer Passing Performance
   - The Zero Value Versus No Value
   - The Difference Between Maps and Slices
   - Slices as Buffers
   - Reducing the Garbage Collector's Workload
1. Types, Methods, and interfaces
   - Methods
   - Pointer Receivers and Value Receivers
   - Code Your Methods for `nil` instances
   - Methods Are Functions Too
   - Functions Versus Methods
   - Types Are Executable Documentation
   - `iota` is for Enumeration - Sometimes
   - Use Embedding for Composition
   - Embedding Is Not Inheritance
   - A Quick Lesson on Interfaces
   - Interfaces Are Type-Safe Duck Typing
   - Embedding and Interfaces
   - Accept Interfaces, Return Structs
   - Interfaces and `nil`
   - The Empty Interface Says Nothing
   - Type Assertions and Type Switches
   - Use Type Assertions and Type Switches Sparingly
   - Function Types Are a Bridge to Interfaces
   - Implicit Interfaces Make Dependency Injection Easier
1. Errors
   - Use Strings for Simple Errors
   - Sentinel Errors
   - Errors Are Values
   - Wrapping Errors
   - Wrapping Errors with `defer`
   - `panic` and `recover`
   - Getting a Stack Trace from an Error
   - References
1. Modules, Packages, and Imports
   - Repositories, Modules, and Packages
   - go.mod
   - Building Packages
   - Package Comments and godoc
   - The `internal` package
   - The `init` Function: Avoid if Possible
   - Circular Dependencies
   - Gracefully Renaming and Reorganising Your API
   - Working with Modules
   - Publishing Your Module
   - Versioning Your Module
   - Module Proxy Servers
   - References
1. Writing Tests
   - The Basics of Testing
   - Reporting Test Failures
   - Setting Up and Tearing Down
   - Storing Sample Test Data
   - Caching Test Results
   - Testing Your Public API
   - Use go-cmp to Compare Test Results
   - Table Tests
   - Checking Your Code Coverage
   - Benchmarks
   - Stubs in Go
   - httptest
   - Integration Tests and Build Tags
   - Finding Concurrency Problems with the Race Checker

## References

- [Learing Go](https://www.oreilly.com/library/view/learning-go/9781492077206/)
- https://github.com/learning-go-book - code examples, exercises, etc
- [Go Wiki](https://github.com/golang/go/wiki/)