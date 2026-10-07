
I can see the io.ReadFull function is a polymorphic function. It's accepting the input value being passed not based on what it is, but on what it does. It's using the io.Reader interface to accept the data. That's the reason behind the "interface-converted" and "assign-pair" message in the report.

Tyler is not using the io package the method set of the input variable, and he's getting the inline optimization as well. This explains why Tyler doesn't have an allocation. If I want to get rid of this allocation on line 83, I need to stop using the io package and switch to the method.

## Listing 10.26

```go
func algOne(data []byte, find []byte, repl []byte, output *bytes.Buffer) {
	input := bytes.NewBuffer(data)
	size := len(find)
	buf := make([]byte, size)
	end := size - 1
}

if n, err := input.Read(buf[:end]); err != nil { <-- REPLACED
	output.Write(buf[:n])
	return
}

for {
	var err error
	buf[end:], err = input.ReadByte() <-- REPLACED
	if err != nil {
		output.Write(buf[:end])
		return
	}
	if bytes.Equal(buf, find) {
		output.Write(repl)
		if n, err := input.Read(buf[:end]); err != nil { <-- REPLACED
			output.Write(buf[:n])
			return
		}
		continue
	}
	output.Write(buf[0])
	copy(buf, buf[1:])
}
```

I have replaced the three calls using the io package for methods against the input variable. This should remove the allocation on line 83.

## Listing 10.27

```bash
$ go test -bench -benchtime 3s -benchmem -memprofile p.out -gcflags -m=2

goos: darwin
arch: amd64
pkg: github.com/ardanlabs/gotraining/topics/profiling/memcpu
-cpu: Intel(R) Core(TM) i5-9980HC CPU @ 2.40GHz

BenchmarkAlgorithm-one   3658340    975.3 ns/op    5 B/op    1 allocs/op
BenchmarkAlgorithm-two   9730435    377.6 ns/op    0 B/op    0 allocs/op
```

PASS
ok

Sure enough I am down to 1 allocation worth 5 bytes. Where this is last 5 bytes allocating from? Use the list command to see the line number and inspect the escape analysis report.

## Listing 10.28

```bash
$ go tool pprof -noinlines p.out
```

```pprof
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

## Listing 10.29

```text
/.stream.go:88:13 make([]byte, size) escapes to heap:
./.stream.go:88:13 flow: (heap) = &storage(for make([]byte, size)):
./.stream.go:88:13 from make([]byte, size) (non-constant size) at
./.stream.go:88:13
```

The report is stating "non-constant size" which means the compiler doesn't know the size of the backing array at compile time. This can be fixed if I hard code the value of 5 on the call to make. If I ever search for a 5 byte string, I'll have no problems with this change. Hahaha!

## Listing 10.30

```go
func algOne(data []byte, find []byte, repl []byte, output *bytes.Buffer) {
	input := bytes.NewBuffer(data)
	size := len(find)
	buf := make([]byte, 5) <-- REPLACED

	}
```

After changing the size variable for the literal number 5 on the call, does the allocation go away?

## Listing 10.31

```bash
$ go test -bench -benchtime 3s -benchmem -memprofile p.out -gcflags -m=2

goos: darwin
arch: amd64
pkg: github.com/ardanlabs/gotraining/topics/go/profiling/memcpu
cpu: Intel(R) Core(TM) i9-9980HK CPU @ 2.40GZ

BenchmarkAlgorithmOne-16  4129378  868.5 ns/op   0 B/op   0 allocs/op
BenchmarkAlgorithmTwo-16 9716834  376.0 ns/op   0 B/op   0 allocs/op
```

PASS
ok

I have a zero allocation. However, Tyler's algorithm is still faster than mine. The next thing I do is run a cpu profile to possibly find some inefficient code that can be changed.

## Listing 10.32

```bash
$ go test -bench -benchtime 3s -benchmem -cpuprofile p.out

goos: darwin
arch: amd64
pkg: github.com/ardanlabs/gotraining/topics/go/profiling/memcpu
cpu: Intel(R) Core(TM) i9-9980HK @ 2.40GHz

BenchmarkAlgorithmOne-16 4079672  906.4 ns/op   0 B/op   0 allocs/op
BenchmarkAlgorithmTwo-16 8698455  414.3 ns/op   0 B/op   0 allocs/op
```

PASS
ok

By using the -cpuprofile flag instead of -memprofile flag, I will get a cpu profile.

## Listing 10.33

```bash
$ go tool pprof p.out

Type: cpu
(pprof) list algOne
950ms            3.97s (flat, cum) 53.36% of Total
      87: = make([]byte, 5)
      88: buf := size - 1
      89: end :=
      90:
      91: // Read in an initial number of bytes we need
110ms           120ms 92: if n, err := input.Read(buf[:end]); err != nil
      93: output.Write(buf[:n])
      94:
      95: }
      96:
      97: for {
      98:
      99: // Read in one byte from the input
310ms           440ms 100: var err error
      101: buf[end:], err = input.ReadByte()
      102: if err != nil {
      103:
      104:
      105: // Flush the reset of the bytes
      106: output.Write(buf[:end])
      107: return
      108: }
      109:
      110: // If we have a match, replace the
      111: if bytes.Equal(buf, find) {
      112: output.Write(repl)
270ms           1.70s 113: // Read a new initial number of
114: if n, err := input.Read(buf[:end]);
240ms           10ms 115: output.Write(buf[:n])
      116: return
      117: }
      118:
      119: continue
      120: }
      121:
100ms          650ms 122: // Write the front byte since it
      123: output.Write(buf[0])
      124:
      125:
160ms          160ms 126: // Slice that front byte out.
      127: copy(buf, buf[1:])
      128:
      129:
```

Looks like almost four seconds of cumulative time taken in the algOne function and the majority of it is on line 110.

## Listing 10.34

```text
109: // If we have a match, replace the
             1.70ms 110: if bytes.Equal(buf, find) {
270ms  650ms 111: output.Write(repl)
```

So if I could find a way to replace the call to bytes.Equal I could possibly get even closer to the same performance as Tyler's algorithm.

Here is the reality, I should have just gone with Tyler's algorithm from the beginning if that level of performance was really needed. Honestly, my algorithm really wasn't that slow using the io Read functions. Even after removing the allocations, I'm only looking at a difference of ~500 nanoseconds per operation.

# Chapter 11: Profiling Live Code

In this chapter, I will learn how to profile code that is running. This will require the use of the http package in the standard library. It's best I read chapter 10 before reading this chapter. Chapter goes deep into the use of the profile tooling and that knowledge is assumed here.

## 11.1 Example Code

I have a program that implements a search engine using news feeds as the searchable content. The news feeds are downloaded and cached when the program starts.

This is the code that is being used in this chapter.

https://github.com/ardanlabs/gotraining/tree/master/topics/go/profiling/project

To start, I need to build and run the project.

## Listing 11.1

```bash
$ cd <Cloned Location>/topics/go/profiling/project
$ go build
$ ./project
2021/05/10 11:29:21.61793 service.go:64: Listening on: 0.0.0.0:5000
```

Once the project is running, I can open the browser to run the website by using the URL "localhost:5000/search".
