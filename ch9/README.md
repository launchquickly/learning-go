# Modules, Packages, and Imports

## Repositories, Modules, and Packages

- repository - where the source code of a project is version controlled
- module - root of a Go library or application, stored in a repository
- modules - consist of one or more packages, which give the module organisation
and structure
    - really it should be one module per repository

## go.mod

MODULE_PATH is:
- globally unique name that identifies your module
- case-sensitive
    - do not use uppercase letters

```bash
go mod init MODULE_PATH
```

## Building Packages

### Imports and Exports

Go uses *capitalisation* to determine if a package-level identifier is visible
outside of the package where it is declared.

### Creating and Accessing a Package

[Example structure](https://github.com/learning-go-book/package_example)

While you can use a relative path to import a dependent package within the same
module, don't do this. Absolute import paths clarify what you are importing
and make it easier to refactor your code.

### Naming Packages

Having the package name as part of the name used to refer to items in the 
package has some implications:
- the package name should be descriptive e.g. Not `util`
- instead create a package name that describes its functionality
    - **bad** `util.ExtractNames` and `util.FormatNames` 
    - **good** `extract.Names` and `format.Names`

### How to Organise Your Module

- When your module is small, keep all your code in a single package
    - delay organisation
- For bigger codebases:
    - `cmd` directory with a directory within for each binary built from
    the module - `main` will be the package name
    - `pkg` directory contains other Go code
        - within `pkg` organise code to limit dependencies between packages

### Overriding a Package's Name

## Package Comments and godoc

## The `internal` package

Restricts the exported identifiers in that package and subpackages to
- the direct parent packag of `internal`
- sibling packages of `internal`

## The `init` Function: Avoid if Possible

## Circular Dependencies

## Gracefully Renaming and Reorganising Your API

To avoid backward-breaking change, don't remove the original identifiers, 
provide an alternate name instead
- for functons or methods - declare a function or method tha calls the original
- for constants - declare a new constant with the same type and value
- to rename or move an exported type, you use an *alias*

```go
type Bar = Foo
```

## Working with Modules

### Importing Third-Party Code

## Publishing Your Module

## Versioning Your Module

## Module Proxy Servers

### Specifying a Proxy Server

### Private Repositories

## References

- [How Do You Structure Your Go Apps](https://www.youtube.com/watch?v=oL6JBUk6tj0)