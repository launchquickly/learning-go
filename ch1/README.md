# Setting Up Your Go Environment

## Go development set-up

The git-setup.yml ansible playbook located in repo [ansible-playbooks](https://github.com/launchquickly/ansible-playbooks) 
sets up the following for an Ubuntu maching in a manner similar to that described in the book:

- Go development tools
- Go Workspace
- A number of 3rd party utilities, including: goimport; golint, gopls, delve, staticcheck and gotests
- VS Code with the golang.go extension installed

## Code Style

The following resources provide some guidance on what good Go style looks like.
- [Effective Go](https://go.dev/doc/effective_go) - outdated but still a point of reference
- [CodeReviewComments](https://github.com/golang/go/wiki/CodeReviewComments)

Using `go vet` and `golint` are likely starting points for use in code review processes. Later on `golangci-lint` if 
configured in a way that has agreement and understanding can be considered.

## IDE's

GoLand might be something to consider later depending upon experience with VS Code.

The [Go Playground](https://go.dev/play/) is a good way to test out and share simple golang experiments.

## Makefiles

Go developers have adopted `make` as their way of automating build steps.

## Staying Up to Date

This section has a proposal on how to incrementally update the version of Go used.

## Code examples

- [hello.go](/ch1/hello.go) - simple hello world type example to try out `go run`, `go build` and `go fmt` and similar 
commands on
- [Makefile](ch1/Makefile) - simple Makefile example