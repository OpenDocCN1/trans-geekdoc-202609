# Listing 8.4

```
var gs string

func BenchmarkSprint(b *testing.B) {
    var gs string

    for i := 0; i < b.N; i++ {
        s = fmt.Sprint("hello")
    }

    gs = s
}
```

At the core of every benchmark is the loop from i to b. Inside this loop is where the code to be benchmarked is placed. To understand the loop, I need to understand a setting called -benchtime.

The -benchtime represents the total amount of time to spin the loop before providing a result. This is where things gets interesting because I can't spin a loop based on time, only on a number of iterations. The number of iterations required to match the -benchtime needs to be identified.

 the correct b.N to match the -benchtime is accomplished through some trial and error. At the very beginning of running the benchmark, the tooling will set the value of b.N to 1 and run the loop. Then it will multiply the value of b.N by 100 until it gets close to the -benchtime. Then the algorithm can fix on a working b.N.

# Listing 8.5

```
var gs string
var a []int

func BenchmarkSprint(b *testing.B) {
    var gs string

    a = append(a, b.N)
    for i := 0; i < b.N; i++ {
        s = fmt.Sprint("hello")
    }

    if len(a) > 4 {
        fmt.Println(a)
    }

    gs = s
}
```

I added the ability to capture the value of b.N on every call to the benchmark function. Knowing that in case it will take 5 calls to find the right b.N, that is when I output the the contents of the slice.