test is repeated three times):

```
$ go test -run=^$ -bench=. -benchmem -count=3 -benchtime=5s
goos: linux
goarch: amd64
BenchmarkEncoder-8    3477318    1692 ns/op    1046 B/op    15 allocs/op
BenchmarkEncoder-8    3435145    1704 ns/op    1048 B/op    15 allocs/op
BenchmarkEncoder-8    3631305    1595 ns/op    1039 B/op    15 allocs/op
BenchmarkMarshal-8    3624570    1616 ns/op    1119 B/op    16 allocs/op
BenchmarkMarshal-8    3549090    1626 ns/op    1123 B/op    16 allocs/op
BenchmarkMarshal-8    3548070    1638 ns/op    1123 B/op    16 allocs/op
```

In these results we can see that json.Marshal() requires ever so slightly more memory (B/op) than json.Encoder, and also makes one extra heap memory allocation (allocs/op).

There’s no obvious observable difference in the average runtime (ns/op) between the two approaches. Perhaps with a larger benchmark sample or a larger data set a difference might become clear, but it’s likely to be in the order of microseconds, rather than anything larger.

# Additional JSON encoding nuances

Encoding things to JSON in Go is mostly quite intuitive. But there are a handful of behaviors which might either catch you out or surprise you when you first encounter them.