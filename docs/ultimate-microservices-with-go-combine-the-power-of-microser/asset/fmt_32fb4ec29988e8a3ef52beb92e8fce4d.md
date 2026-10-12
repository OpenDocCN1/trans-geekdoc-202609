
Let’s highlight the fact that a goroutine leak manifests as a memory leak. A goroutine in the background holds variables that aren’t being released from memory. There are two primary ways to detect goroutine leaks:

*   **Profiling**: We will discuss profiling in more detail in *[Chapter 10, Next Steps in Production](#c10.xhtml)*. Generally, while profiling and analyzing the code, we can check for non-terminated goroutines using the Go profile (`pprof`) or `gops`.

*   **Tests**: The best but most exhausting way is to write unit tests that reveal goroutine leaks. We aim to cover all the situations where a goroutine leak can happen. The tests inherently check at the end of the test if any goroutines are still running in the background. Go allows us to see how many goroutines run in the background using `runtime.NumGoroutine()`. We can also use an external package like `uber-go/goleak`.

# Fan In Fan Out Pattern

Fan In Fan Out is a popular pattern that helps us handle multiple sources converted into a single stream (fan-in) or input from one source being streamed into multiple pipelines (fan-out). In Go, if we need multiple functions to read from the same channel until the channel is closed - fan out. A single function that can read from multiple inputs (sources) until all the input channels are closed - fan-in.

# Fan Out

We should use the fan-out pattern when we want to distribute the work among a group of workers to perform optimization by parallelism to resources like CPU and I/O.

```
func generator(numbers []int) <-chan int {
    out := make(chan int)
    go func() {
        for _, num := range numbers {
            out <- num
        }
        close(out)
    }()
    return out
}

func businessLogic(num int) int {
    return num * 2
}

func main() {
    data := []int{1, 2, 3, 4, 5, 6}
    var wg sync.WaitGroup
    ch1 := generator(data[0:3])
    ch2 := generator(data[3:])
    wg.Add(2)
    go func() {
        for num := range ch1 {
            println(businessLogic(num))
        }
        wg.Done()
    }()
    go func() {
        for num := range ch2 {
            println(businessLogic(num))
        }
        wg.Done()
    }()
    wg.Wait()
}
```

In the preceding example, we have a `data` variable (the source), but we want to parallelize the process of that data. We decided to split the work among two workers. The first thing we did was to split the data into two. Then, we called the `generator` function. The `generator` function’s purpose is to accept input, send all the input into a channel called `out`, and then return that channel. After calling the `generator` function twice, we used `WaitGroup` to wait for all the workers to finish their work. Finally, we executed two goroutines (workers). Each worker performed some business logic and then finished.

# Fan In

We should use the fan-in pattern to process multiple inputs (sources) into a single function. We will do it by merging multiple channels into one. The process of combining multiple channels into a single channel is called multiplexing. The single channel will be closed only when all the input channels will be closed. We will examine the multiplexing process by a function called `merge`.

```
func merge(sourcesCh …<-chan int) <-chan int {
    var wg sync.WaitGroup
    wg.Add(len(sourcesCh))
    out := make(chan int)
    outputFunc := func(sourceCh <-chan int) {
        for num := range sourceCh {
            out <- num
        }
        wg.Done()
    }
    for _, sourceCh := range sourcesCh {
        go outputFunc(sourceCh)
    }
    go func() {
        wg.Wait()
        close(out)
    }()
    return out
}

func generator(numbers []int) <-chan int {
    out := make(chan int)
    go func() {
        for _, num := range numbers {
            out <- num
        }
        close(out)
    }()
    return out
}

func main() {
    data := []int{1, 2, 3, 4, 5, 6}
    ch1 := generator(data[0:3])
    ch2 := generator(data[3:])
    ch := merge(ch1, ch2)
    for num := range ch {
        println(num)
    }
}
```

The `generator` function is the same as we saw in the example of the fan-out pattern. We first declare the single output channel called `out` in the `merge` function. Second, we create a `WaitGroup` to determine when all the multiple source channels are being closed. After they are closed, we will use `Wait()` and close the output (`out`) channel. Then, we created a function (`outputFunc`) that accepts the source channel and sends all the data from that source channel to the output channel (`out`). Finally, we iterate onto all the source channels and execute the goroutine, called the `outputFunc`.

We now have a single channel to iterate safely in the `main` function until the `merge` function closes the channel.

# Conclusion

In this chapter, we talked in detail about concurrency in Go. It is one of the most important topics in Go, and it is crucial to understand it well to write code. In the previous two chapters, we discussed the Go basics topic to have a deep knowledge of how Go works, which is imperative to build a microservices architecture with Go. Throughout these chapters, we had a glimpse of how to leverage Go knowledge into building microservices architecture.

In the next chapter, we will go over the fundamentals elements for building microservices architecture.

# References

*   [https://stackoverflow.com/questions/4844637/what-is-the-difference-between-concurrency-parallelism-and-asynchronous-methods#:~:text=Concurrency%20is%20when%20the%20execution,though%20related%20in%20some%20contexts](https://stackoverflow.com/questions/4844637/what-is-the-difference-between-concurrency-parallelism-and-asynchronous-methods#:~:text=Concurrency%20is%20when%20the%20execution,though%20related%20in%20some%20contexts)
*   [https://pkg.go.dev/sync](https://pkg.go.dev/sync)
*   [https://pkg.go.dev/golang.org/x/sync/errgroup](https://pkg.go.dev/golang.org/x/sync/errgroup)
*   [https://www.uber.com/en-JO/blog/leakprof-featherlight-in-production-goroutine-leak-detection/#:~:text=A%20possible%20solution%20to%20prevent,a%20buffer%20size%20of%201](https://www.uber.com/en-JO/blog/leakprof-featherlight-in-production-goroutine-leak-detection/#:~:text=A%20possible%20solution%20to%20prevent,a%20buffer%20size%20of%201)
*   [https://github.com/uber-go/goleak](https://github.com/uber-go/goleak)

# CHAPTER 6

# Core Elements of Microservices

# Introduction

After we cover all the essential knowledge related to the Go programming language, we will combine it with the core elements of microservices architecture. You are probably asking yourself what are those “*core elements*”; microservices architecture is an **approach**, not a destination. Therefore, the core elements are tech industry methodologies, design patterns, and technologies. All of those elements together will compose an entire system. There isn’t a recipe that tells us how to physique out an architecture. There are many constraints, product requirements (which can drag engineering requirements), and assumptions — each system has its unique structure. However, all these systems have elements in common. This chapter presents those elements, when they can become beneficial, their advantages/disadvantages, and when to use/avoid them. We won’t be delving into every single element; instead, the objective is to provide a framework outlining the boundaries of each element.

We will not cover all the existing elements for microservices. Instead, we will go through the leading ones. Here are elements we won’t cover in this chapter:

*   **Saga Pattern**: Allows us to manage distributed transactions in a microservices architecture by breaking them into smaller, isolated steps, each with its compensating transaction to handle potential failures.
*   **Aggregator Pattern**: Reduces data from multiple services to simplify the data for other services that wish to pull it.
*   **Decomposition Pattern**: Helps us break monolithic into microservices.
