# Composite Types

## Arrays

- arrays are rarely used as the length of an array is considered part of the type of the array
and are too restrictive for general use

## Slices

Length is not part of the type of a slice.

```
var x = []int{10, 20, 30}
var y []int  // assigned to nil
```

### Functions for working on slices

- `len`
- `append`
- `cap` - used to check the remaining capacity is sufficient, or needs to grow
- `make` - used to specify type, length, and optionally capacity
- `copy` - creat a slice from an array

### Declaring a slice

- if using as a buffer then specify a nonzero length
- otherwise use `make` with a zero value and a specified capacity
- alternative (but not recommended) is create it with exact size

### Converting Arrays to Slices

```
x := 4[int]{5, 6, 7, 8}
y := x[:2]              // will have memory-sharing with original array values
```

- `copy` creates a slice that is independent from the original array

## Maps

## Using Maps as Sets

## Structs

- Groups related data you want to pass to functions
- Are comparable if composed of comparable types (`==`, `!=`)
- Order of declaration is significant for:
    -  initialisation if using comma-separated list of values form
    -  converting between structs
- struct can be declared in an anonymous fashion
- structs can be converted to another struct if field name and order match

```
type person struct {
    age     int
    name    string
    pet     string
}

var aidan person

dara := {}

aoife := {
    14,
    "Aoife",
    "hamster,
}

fionn := {
    age: 14,
    name: "Fionn",
}

pet := struct {
    kind    string
    name    string
} {
    kind: "dog",
    name: "Tiba",
}
```