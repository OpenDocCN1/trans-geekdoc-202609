Now I absolutely know the algOne function owns the construction of the bytes.Buffer value I still don't know why the input variable has allocated, especially since it doesn't exist after the algOne function returns.

I need to look at the escape analysis report for more information.

# Listing 102

```
/stream.go:83:26: &bytes.Buffer(...) escapes to heap:
/stream.go:83:26: flow = -RO = &(storage for &bytes.Buffer(...)):
/stream.go:83:26: from &bytes.Buffer(...) (spill) at /stream.go:83:26
/stream.go:83:26: from = -RO; (assign-pair) at /stream.go:83:26
/stream.go:83:26: flow = input:
/stream.go:83:26: from input := (*bytes.Buffer) ~RO) (assign) at
/stream.go:83:8: io.r = input:
/stream.go:83:26: from input = (interface-converted) at
/stream.go:113:28: from io.r, io.buf = input, buf[:end] (assign-pair)
at at /stream.go:113:28: flow: (heap) = io.r:
/stream.go:83:26: from io.ReadLeast(io.r, io.buf, len(io.buf)) (call
parameter) at /stream.go:113:28
```

This section of the report has the final view. It's sharing information about the construction of the bytes.Buffer on line 83 where the function was inlined.

# Listing 1023

```
flow: io.r = input:
from input (interface-converted) at /stream.go:113:28
from io.r, io.buf = input, buf[:end] (assign-pair) at /stream.go:113:28
```

An interface conversation at line 113 seems to be the reason. What the code is on line 113?

# Listing 1024

```
113 if n, err := io.ReadFull(input, buf[:end]); err != nil {
114   output.Write(buf[:n])
115   return
116 }
```

It's the call to io.ReadFull and I can see the input variable is being passed into the function as the first parameter. Passing a value down the stack doesn't create an allocation so's different from this call? I need to look at the io.ReadFull

# Listing 1025

```
func ReadFull(r Reader, buf []byte) (n int, err error) {
  return ReadAtLeast(r, buf, len(buf))
}
```