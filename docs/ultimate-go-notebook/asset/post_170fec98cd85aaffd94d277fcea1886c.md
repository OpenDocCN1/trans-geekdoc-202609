
```go
package handlers

import (
	"encoding/json"
	"net/http"
)

func Routes() {
	http.HandleFunc("/sendjson", sendJSON)
}
func sendJSON(rw http.ResponseWriter, r *http.Request) {
	u := struct {
	Name string
	Email string
	}(
	Name:  "Bill",
	Email: "bill@ardanlabs.com",
	)

	rw.Header().Set("Content-Type", "application/json")
	rw.WriteHeader(200)
	json.NewEncoder(rw).Encode(&u)
}
```

This code declares a new package named handlers and a function named sendJSON that needs to be tested. In this case, the handler function returns a JSON representation of the literal struct with a status of 200.

The Routes function binds the sendJSON handler to the /sendjson route in the default server mux of the http package. This means any calls to http://domain.com/sendjson would be routed to the sendJSON handler function by the mux.

# Listing 7.10

```go
package handlers_test

import (
    "encoding/json"
    "net/http"
    "net/http/httptest"
    "testing"

    "github.com/ardanlabs/gotraining/app/handlers"
)

func init() {
    handlers.Routes()
}

func TestSendJSON(t *testing.T) {
    url := "/sendjson"
    statusCode := 200

    r := httptest.NewRequest("GET", url, nil)
    w := httptest.NewRecorder()
    http.DefaultServeMux.ServeHTTP(w, r)
}
```

The first thing the test does is use the init function to make sure all the routes are loaded in the mux. This is done by calling the handlers.Routes function. A big mistake that is made with these types of tests is forgetting to load the routes.

With the routes loaded, the next step is to construct a request and construct a value that implements the http.ResponseWriter interfaces. The httptest package provides support for both. The httptest.NewRequest constructs the request as a GET for the /sendjson route. The httptest.NewRecorder constructs the concrete value that implements the http.ResponseWriter interfaces and can be directly checked to validate if the web call passed or failed.

The key to running the test is calling the ServeHTTP function from the mux. Since I am using the http.DefaultServerMux in this code, that is where I am making the call to ServeHTTP. Any mux I may choose to use will implement this method. Once I call this method, I am asking the mux to process the request through the route and apply the response in the concrete recorder value.

# Listing 7.11

```go
func TestSendJSON(t *testing.T) {
	if w.Code != 200 {
		t.Log("exp:", statusCode)
		t.Log("got:", w.StatusCode)
		t.Fatal("status codes don't match")
	}

	var u struct {
		Name string
		Email string
	}
	if err := json.NewDecoder(w.Body).Decode(&u); err != nil {
		t.Fatal("unable to decode the response:", err)
	}

	exp := "Bill"
	if u.Name != exp {
		t.Log("exp:", exp)
		t.Log("got:", u.Name)
		t.Fatal("user name does not match")
	}

	exp = "bill@ardanlabs.com"
	if u.Email != exp {
		t.Log("exp:", exp)
		t.Log("got:", u.Email)
		t.Fatal("user name does not match")
	}
}
```

Now, using the recorder value, I can check if the route behaved as expected. First I check that the status code is 200. Then I attempt to unmarshal JSON response back to a concrete type. If that is successful, then I check the values in the Name and Email fields. All that is correct, the test passes.

This test was executed without the need of a network or running the web service.

## 7.5 Basic Sub-Tests

There are times when I want to group a set of tests together under a single test function. I might have a table test where I want to control which data is tested on the command line. It's also possible that I want to run a series of tests in parallel. If I fall into any of these use cases, the sub-testing support in Go is what I I need.

# Listing 7.12

```go
package sample_test

import (
    "net/http"
    "testing"
)

func TestDownload(t *testing.T) {
    tt := []struct {
        name        string
        url         string
        statusCode int
    }{
        {
            "ok",
            "https://www.ardanlabs.com/blog/index.xml",
            http.StatusOK,
        },
        {
            "notfound",
            "http://rss.cnn.com/rss/cnn_topstorie.rss",
            http.StatusNotFound,
        },
    }
    // ...
}
```

This test is going to test the downloading of URLs like I saw with the table test before. The difference here is that the table has a new field called name, which will represent the name of the sub-test I am going to create for each entry. It's important to give each sub-test a name that is unique within the loop so I can run it with the least number of characters to type.

# Listing 7.13

```go
for _, test := range tt {
    test := test
    tf := func(t *testing.T) {
        resp, err := http.Get(test.url)
        if err != nil {
            t.Fatal("unable to get URL: %s", test.url, err)
        }
        defer resp.Body.Close()

        if resp.StatusCode != test.StatusCode {
            t.Log("exp:", test.StatusCode)
            t.Log("got:", resp.StatusCode)
            t.Fatal("status codes don't match")
        }
    }
    t.Run(test.name, tf)
}
```

There are a couple of changes to the code inside the loop from the original table test example. The first line of code inside the loop is creating a new variable that has local scope to the loop. This is done to prevent closure issues. I must make sure each sub-test has its own copy of the data. Then a function is declared and assigned to the tf variable. This function is passed to the call to t.Run at the bottom of the loop. The call to t.Run is how the sub-test is registered by name. Once all the tests are registered, they can be executed together or specified individually on the command line.

# Listing 7.14

```bash
$ go test -v
$ go test -run TestDownload/ok -v
$ go test -run TestDownload/notfound -v
```

This is how I can run all sub-tests or specify any individual sub-test. There is one other cool feature with sub-tests: I can run the tests in parallel using the t.Parallel method.

# Listing 7.15

```go
for _, tt := range tt {
  test := tt
  tf := func(t *testing.T) {
    t.Parallel()
    // ...
  }
  // ...
}
```

By adding the call to t.Parallel() as the first line of code in the function, the testing tool will run all the registered tests in parallel, speeding up execution time.

# Chapter 8: Benchmarking

In this chapter, I will learn how to write benchmarks in Go and use the integrated support provided by the language. I will also learn how to realize that benchmarks lie and I need to be careful when interpreting the results.

## 8.1 Basic Benchmark

At the same time, until I run a benchmark I’m only guessing. There's one thing about Go, it's that I never have to guess. That's how the tooling is. The standard library and the Go tooling has everything I need to write a benchmark. It starts with creating a file with the _test.go naming convention inside the package I want to benchmark, and then adding benchmark functions using the word Benchmark with a capital B for each function.

Listing 8.1

```go
sample_test.go
package sample

import (
	"testing"
)

func BenchmarkDownload(b *testing.B) {}
func BenchmarkUpload(b *testing.B) {}
```

These are examples of benchmark functions I could declare in the sample_test.go file. It's important that the first letter following the word Benchmark in the function starts with a capital letter. If I don’t, the testing tool won’t see the function as a benchmark. The other important piece is that the benchmark function takes a testing.B pointer as the only argument.

Here is a super interesting benchmark to run.

```go
package basic

import (
	"fmt"
	"testing"
)

var gs string

func BenchmarkSprint(b *testing.B) {
	var s string
	for i := 0; i < b.N; i++ {
		s = fmt.Sprintf("hello")
	}
	gs = s
}

func BenchmarkSprintf(b *testing.B) {
	var s string
	for i := 0; i < b.N; i++ {
		s = fmt.Sprintf("hello")
	}
	gs = s
}
```

The premise of this benchmark is to know which version of Sprint is faster, regular or format version. When people are asked to guess, they tend to say the regular version since there is no formatting necessary. These people are always wrong.

```bash
$ go test -bench -benchtime 3s -benchmem
goos: darwin
arch: amd64
pkg: github.com/ardanlabs/gotraining/topics/go/testing/benchmarks/basic
cpu: Intel(R) (TM) i9-9880HK CPU @ 2.40GHz

| | ns/op | B/op | allocs/op |
|---|---|---|---|
| BenchmarkSprint-16 | 56965252 | 55.48 ns/op | 5 B/op | 1 allocs/op |
| BenchmarkSprintf-16 | 80984947 | 42.46 ns/op | 5 B/op | 1 allocs/op |
```

I can see from the results that the format version is faster by 13 nanoseconds per operation. The difference is insignificant, but nonetheless, there is a difference.
