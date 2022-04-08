# Blocks, Shadows, and Control Structures

## Blocks

Each place where a declaration occurs is called a *block*.

## Shadowing Variables

A shadowing variable is a variable that has the same name as a variable
in a containing block. For as long as the shadowing variable exists, 
you cannot access a shadowed variable.

## Detecting Shadowed Variables

The `shadow` linter utility can be used to identify these cases. [Makefile](/ch1/Makefile)
includes an example of how it can be incorporated into the build process.

## `if`

Go lets you create variables that are available only where they are needed:

```go
if n := rand.Intn(10); n == 0 {
    fmt.Println("That's too low")
} else if n > 5 {
    fmt.Println("That's too big: ", n)
} else {
    fmt.Println("That's a good number: ", n)
}
```

## `for`, Four Ways

1. A complete, C-style `for`
1. A condition-only `for`
1. An infinite `for`
1. `for`-`range`

- `break` and `continue` are available, including with labels. 

> Go encourages short `if` statements bodies, as left-aligned as possible.
> Using a `continue` statement makes it easier to understand what's going on.

```go
for i :- 1 i <= 100; i++ {
    if i%3 == 0 && i%5 == 0 {
        fmt.Println("FizzBuzz")
        continue;
    }
    if i%3 == 0 {
        fmt.Println("Fizz")
        continue;
    }
    if i%5 == 0 {
        fmt.Println("Buzz")
        continue;
    }
    fmt.Println(i)
}
```

### The `for`-`range` Statement

Is used to iterate over elements in some of Go's built-in types.

```go
evenVals := []int{2, 4, 6, 8, 10, 12}
for i, v := range evenVals {
    fmt.Println(i, v)
}
```

Where `i` is the position of the loop and `v` the value at the position.
`k` is often used when iterating through a map.

If you don't need to access `i` in the loop you can replace it with `_`,
Similarly if you don't need to access `v` you can leave it out.

The for-range value is a copy, so modifying it will not modify the value in the 
compound type.

### Choosing the Right `for` statement

- Most of the time you will use the `for`-`range` statement as it avoids a lot of
boilerplate code.
- The complete `for` loop is best used when you aren't iterating from the first 
element to the last element.

## `switch`

You can switch on any type that can be compared with `==`.

By default, cases in `switch` statements do **not** fall through. This does mean
that **empty* cases will do nothing. You can use labels in switch statements too.

```go 
words := []string{"a", "cow", "smile", "gopher"}
for _, word := range words {
    switch size := len(word); size {
        case 1, 2, 3, 4:
            fmt.Println(word, "is a short word!")
        case 5:
            fmt.Println(word, "is exactly the right length")
        case 6,7:
        default:
            fmt.Println(word, "is a long word!")
    }
}
```

## Blank Switches

You can write a `switch` statement that does not specify the value you are 
comparing against. This is called a *blank switch*. A blank switch allows
you to use any boolean comparison for each case.

```go
    ...
    switch wordLen := len(word); {
    case wordLen < 5:
        fmt.Println(word, "is a short word!")
    case wordLen > 10:
        fmt.Println(word, "is a long word!")
    default:
      ...
    }
    ...
```

## Choosing Between `if` and `switch`

A `switch` statement indicates ther is some relationship between the values or
comparisons in each case.

> Favour blank `switch` statements over `if`/`else` chains when you have multiple
> related cases. Using a `switch` makes the comparisons more visible and 
> reinforces that they are a related set of concerns.