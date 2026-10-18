
```go
    Hash("6368616e676520746869732070617373", key)
}
}

func BenchmarkHash20(b *testing.B) {
    for n := 0; n < b.N; n++ {
        key := "12345678901234567890"
        Hash("6368616e676520746869732070617373", key)
    }
}
```

This defines two tests for keys of differing lengths (10) and (20) characters. You can then run the benchmarks as follows:

```text
$ go test -bench=.
goos: linux
goarch: amd64
pkg: github.com/alexellis/bench-comp
BenchmarkHash10-8          816800             1314 ns/op
BenchmarkHash20-8          876960             1347 ns/op
PASS
ok    github.com/alexellis/bench-comp    2.288s
```

Benchmarking can also be useful for comparing the performance Go code on a certain CPU. Arm CPUs have traditionally lacked optimizations for cryptography, so this benchmark should run much slower on a Raspberry Pi.

## Go doesn’t ship your tests

In addition, it may feel unnatural to leave files named `addition_test.go` in the middle of your package. Rest assured that the Go compiler and linker will not ship your test files in any binaries it produces.

Here is an example of finding the production vs test code in the net/http package we used in the previous Golang basics tutorial.

```text
$ go list -f={{.GoFiles}} net/http
[client.go cookie.go doc.go filetransport.go fs.go h2_bundle.go header.go http.go jar.go
↪  method.go request.go response.go server.go sniff.go status.go transfer.go transport.go]

$ go list -f={{.TestGoFiles}} net/http
[cookie_test.go export_test.go filetransport_test.go header_test.go http_test.go
↪  proxy_test.go range_test.go readrequest_test.go requestwrite_test.go response_test.go
↪  responsewrite_test.go transfer_test.go transport_internal_test.go]
```

## Stress testing your tests

Your tests can also be run more than once, I’ve found this to show up issues with race conditions or shared state in code that I’ve written.

Simply add `-test.count=100` to run your tests 100 times.

At times, you’ll also see the tests refuse to run because the results are (cached). In this instance, adding `-test.count=1` can get around that problem.

## Running tests in parallel

It may appear that your unit tests run well and in a deterministic order, but often when they are run in parallel problems can be found before they hit production. This is because when we test our code locally, it’s usually with a lower load, or serially. On a production system, we may have many users doing things in parallel.

You may also have a suite of tests that are slow to run, in that case running in parallel may save time. 10x tests that take 1s to complete could run in 10 seconds serially, or in 1 second if run with a parallelism of 10.

Consider this example:

```go
package main

import (
    "testing"
    "time"
)

func Test_Slow1(t *testing.T) {
    time.Sleep(1 * time.Second)
}

func Test_Slow2(t *testing.T) {
    time.Sleep(1 * time.Second)
}

func Test_Slow3(t *testing.T) {
    time.Sleep(1 * time.Second)
}

func Test_Slow4(t *testing.T) {
    time.Sleep(1 * time.Second)
}

func Test_Slow5(t *testing.T) {
    time.Sleep(1 * time.Second)
}
```

```
$ go test ./ -v
=== RUN   Test_Slow1
--- PASS: Test_Slow1 (1.00s)
=== RUN   Test_Slow2
--- PASS: Test_Slow2 (1.01s)
=== RUN   Test_Slow3
--- PASS: Test_Slow3 (1.00s)
=== RUN   Test_Slow4
--- PASS: Test_Slow4 (1.01s)
=== RUN   Test_Slow5
--- PASS: Test_Slow5 (1.00s)
PASS
ok      github.com/alexellis/go-slow   5.343s
```

To run the tests in parallel, t.Parallel() has to be added to the test function, then the -test.parallel=N parameter has to be passed in along with it.

```go
package main

import (
    "testing"
    "time"
)
```

```go
func Test_Slow1(t *testing.T) {
    t.Parallel()
    time.Sleep(1 * time.Second)
}

func Test_Slow2(t *testing.T) {
    t.Parallel()
    time.Sleep(1 * time.Second)
}

func Test_Slow3(t *testing.T) {
    t.Parallel()
    time.Sleep(1 * time.Second)
}

func Test_Slow4(t *testing.T) {
    t.Parallel()
    time.Sleep(1 * time.Second)
}

func Test_Slow5(t *testing.T) {
    t.Parallel()
    time.Sleep(1 * time.Second)
}
```

Then run:

```
$ go test -v . -test.count=1 \
    -test.parallel 5
=== RUN   Test_Slow1
=== PAUSE Test_Slow1
=== RUN   Test_Slow2
=== PAUSE Test_Slow2
=== RUN   Test_Slow3
=== PAUSE Test_Slow3
=== RUN   Test_Slow4
=== PAUSE Test_Slow4
=== RUN   Test_Slow5
=== PAUSE Test_Slow5
=== CONT  Test_Slow1
=== CONT  Test_Slow5
=== CONT  Test_Slow4
=== CONT  Test_Slow2
=== CONT  Test_Slow3
--- PASS: Test_Slow3 (1.00s)
--- PASS: Test_Slow1 (1.00s)
--- PASS: Test_Slow5 (1.00s)
--- PASS: Test_Slow4 (1.00s)
--- PASS: Test_Slow2 (1.00s)
PASS
ok      github.com/alexellis/go-slow   1.342s
```

This test could also have been written as a test table.

```go
package main

import (
    "testing"
    "time"
)

func Test_Slow1(t *testing.T) {
    t.Parallel()
    cases := []struct {
        Name     string
        Duration time.Duration
    }{
        {Name: "Case 1", Duration: time.Second * 1},
        {Name: "Case 2", Duration: time.Second * 1},
        {Name: "Case 3", Duration: time.Second * 1},
        {Name: "Case 4", Duration: time.Second * 1},
        {Name: "Case 5", Duration: time.Second * 1},
    }

    for _, c := range cases {
        tc := c
        t.Run(tc.Name, func(t *testing.T) {
            t.Parallel()
            t.Logf("%s sleeping..", tc.Name)
            sleepFn(tc.Duration)
            t.Logf("%s slept", tc.Name)
        })
    }
}

func sleepFn(duration time.Duration) {
    time.Sleep(duration)
}
```

Note the use of the tc variable which captures the value of the test case into the t.Run closure.

As a bonus, it's more readable and it took marginally less time.

```
$ go test -v . -parallel 5
=== RUN   Test_Slow1
=== PAUSE Test_Slow1
=== CONT  Test_Slow1
=== RUN   Test_Slow1/Case_1
=== PAUSE Test_Slow1/Case_1
=== RUN   Test_Slow1/Case_2
=== PAUSE Test_Slow1/Case_2
=== RUN   Test_Slow1/Case_3
=== PAUSE Test_Slow1/Case_3
=== RUN   Test_Slow1/Case_4
=== PAUSE Test_Slow1/Case_4
=== RUN   Test_Slow1/Case_5
=== PAUSE Test_Slow1/Case_5
=== CONT  Test_Slow1/Case_1
=== CONT  Test_Slow1/Case_4
```

```
main_test.go:25: Case 4 sleeping..
=== CONT  Test_Slow1/Case_5
    main_test.go:25: Case 5 sleeping..
=== CONT  Test_Slow1/Case_3
    main_test.go:25: Case 3 sleeping..
=== CONT  Test_Slow1/Case_2
    main_test.go:25: Case 2 sleeping..
=== CONT  Test_Slow1/Case_1
    main_test.go:25: Case 1 sleeping..
    main_test.go:27: Case 1 slept
=== CONT  Test_Slow1/Case_2
    main_test.go:27: Case 2 slept
=== CONT  Test_Slow1/Case_5
    main_test.go:27: Case 5 slept
=== CONT  Test_Slow1/Case_4
    main_test.go:27: Case 4 slept
=== CONT  Test_Slow1/Case_3
    main_test.go:27: Case 3 slept
--- PASS: Test_Slow1 (0.00s)
    --- PASS: Test_Slow1/Case_2 (1.01s)
    --- PASS: Test_Slow1/Case_1 (1.01s)
    --- PASS: Test_Slow1/Case_5 (1.01s)
    --- PASS: Test_Slow1/Case_4 (1.01s)
    --- PASS: Test_Slow1/Case_3 (1.01s)
PASS
ok      github.com/alexellis/go-slow   1.260s
```

So we went from just over 5 seconds to just under 1.5 seconds. This may seem marginal, but if you have lots of tests or run them often, it can be more efficient.

## Compile the tests to a binary

Something that I learned only after using Go for several years, was that the tests can be compiled to a binary, just like your CLI or HTTP server can be.

Why would this be useful?

One scenario is if you have tests that run against external resources, such as a validator or certifier tool. You can version, release, and distribute that without losing the capabilities of go test.

Let's try an example?

```
$ git clone https://github.com/alexellis/go-execute
$ cd go-execute
```

Then test it the “normal” way:

```
$ go test -v ./...
=== RUN   TestExec_WithShell
--- PASS: TestExec_WithShell (0.00s)
=== RUN   TestExec_CatTransformString
--- PASS: TestExec_CatTransformString (0.00s)
=== RUN   TestExec_CatWC
--- PASS: TestExec_CatWC (0.00s)
=== RUN   TestExec_WithEnvVars
--- PASS: TestExec_WithEnvVars (0.00s)
=== RUN   TestExec_WithEnvVarsInheritedFromParent
```
