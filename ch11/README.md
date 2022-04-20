# The Standard Library

## `io` and Friends

2 main interfaces defined in `io` package:
- `io.Reader` - `Read` method
- `io.Writer` - `Write` method

- `io.Copy` - for copying from an `io.Reader` to an `io.Writer`
- `io.MultiReader` - reads from multiple `io.Reader` instances, one after the 
other
- `io.LimitReader` - reads up to a specified number of bytes
- `io.MulitWriter` - writes to multiple `io.Writer` intstances at the same
time
- `io.Closer` - used for types that need to cleanup on completion
- `io.Seeker` - for random access to a resource

`io` package specifies a number of ways of combining the 4 main interfaces:
- `io.ReadCloser`
- `io.ReadSeeker`
- `io.ReadWriterCloser`
- `io.ReadWriteSeeker`
- `io.ReadWriter`
- `io.WriteCloser`
- `io.WriteSeeker`

To make your codes intent clear use these to specify what your functions expects
to do with the data, rather than just using `os.File`, or similar. It also makes
functions more general purpose and compatible with these interfaces if you are
writing your own data sources and sinks.

The `ioutil` package provides some simple utilities.

## `time`

- `time.Duration` - represents a period of time
- `time.Time` - represents a moment in time

## `encoding/json`

### Use Struct Tags to Add Metadata

We can specify the rules for processing our JSON with *struct tags*, strings 
that are written after the field in a struct.

### Unmarshalling and Marshalling

- `json.Unmarshal` - convert a slice of bytes into a struct
- `json.Marshal` - write a struct back to JSON, stored as a slice of bytes

### JSON, Readers, and Writers

- `json.Decoder`
- `json.Encoder`

### Encoding and Decoding JSON Streams

### Custom JSON Parsing

## `net/http`

- `http.Client` - make and receive HTTP requests and responses
- `http.Server` - listens for HTTP requests
- `http.Handler` - handles requests

### Middleware

Go handles cross-cutting concerns with the *middleware pattern*. Rather than
using a special type, the middleware pattern uses a function that takes in 
an `http.Handler` instance and returns an `http.Handler`. Usually, the
returned handler is a closure that is converted to a `http.HandlerFunc`.