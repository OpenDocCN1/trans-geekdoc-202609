# Listing 10.27

```
$ go test -bench -benchtime 3s -benchmem -memprofile p.out -gcflags -m=2

goos: darwin
arch: amd64
pkg: github.com/ardlanabs/gotraining/topics/profiling/memcpu
-cpu: Intel(R) Core(TM) i5-9980HC CPU @ 2.40GHz

BenchmarkAlgorithm-one   3658340    975.3 ns/op    5 B/op    1 allocs/op
BenchmarkAlgorithm-two   9730435    377.6 ns/op    0 B/op    0 allocs/op
```

PASS
ok

Sure enough I am down to 1 allocation worth 5 bytes. Where this is last 5 bytes allocating from? Use the list command to see the line number and inspect the escape analysis report.

# Listing 10.28

```
$ go tool pprof -noinlines p.out
```

```
(pprof) list algOne
20MB      20MB      100% of Total
      ...
      83:
      84: // The number of bytes we are looking for.
      85: size := len(buf)
      86:
      87: // Declare the buffers we need to process the
20MB      20MB      88: buf := make([]byte, size)
      89: end := size - 1
      90:
      91: // Read in an initial number of bytes we need
      92: if n, err := input.Read(buf[:end]); err != nil
      93: output.Write(buf[:n])
```

The final allocation is on line 88 to construction of the slice value.

# Listing 10.29

```
/.stream.go:88:13 make([]byte, size) escapes to heap:
./.stream.go:88:13 flow: (heap) = &storage(for make([]byte, size)):
./.stream.go:88:13 from make([]byte, size) (non-constant size) at
./.stream.go:88:13
```

The report is stating "non-constant size" which means the compiler doesn't know the size of the backing array at compile time. This can be fixed if I hard code the value of 5 on the call to make. If I ever search for a 5 byte string, I'll have no problems with this change. Hahaha!