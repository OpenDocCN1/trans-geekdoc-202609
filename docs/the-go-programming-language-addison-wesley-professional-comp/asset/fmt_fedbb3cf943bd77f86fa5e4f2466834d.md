
![An empty buffered channel.](images/00033.jpeg)

**Figure 8.2.** An empty buffered channel.

A send operation on a buffered channel inserts an element at the back of the queue, and a receive operation removes an element from the front. If the channel is full, the send operation blocks its goroutine until space is made available by another goroutine's receive. Conversely, if the channel is empty, a receive operation blocks until a value is sent by another goroutine.

We can send up to three values on this channel without the goroutine blocking:

```
ch <- "A"
ch <- "B"
ch <- "C"
```

At this point, the channel is full ([Figure 8.3](#part0080.html#id-figures-fullchannel)), and a fourth send statement would block.

![A full buffered channel.](images/00034.jpeg)

**Figure 8.3.** A full buffered channel.

If we receive one value,

```
fmt.Println(<-ch) // "A"
```

the channel is neither full nor empty ([Figure 8.4](#part0080.html#id-figures-nonemptychannel)), so either a send operation or a receive operation could proceed without blocking. In this way, the channel's buffer decouples the sending and receiving goroutines.

![A partially full buffered channel.](images/00035.jpeg)

**Figure 8.4.** A partially full buffered channel.

In the unlikely event that a program needs to know the channel's buffer capacity, it can be obtained by calling the built-in `cap` function:

```
fmt.Println(cap(ch)) // "3"
```

When applied to a channel, the built-in `len` function returns the number of elements currently buffered. Since in a concurrent program this information is likely to be stale as soon as it is retrieved, its value is limited, but it could conceivably be useful during fault diagnosis or performance optimization.

```
fmt.Println(len(ch)) // "2"
```

After two more receive operations the channel is empty again, and a fourth would block:

```
fmt.Println(<-ch) // "B"
fmt.Println(<-ch) // "C"
```

In this example, the send and receive operations were all performed by the same goroutine, but in real programs they are usually executed by different goroutines. Novices are sometimes tempted to use buffered channels within a single goroutine as a queue, lured by their pleasingly simple syntax, but this is a mistake. Channels are deeply connected to goroutine scheduling, and without another goroutine receiving from the channel, a sender—and perhaps the whole program—risks becoming blocked forever. If all you need is a simple queue, make one using a `slice`.

The example below shows an application of a buffered channel. It makes parallel requests to three *mirrors*, that is, equivalent but geographically distributed servers. It sends their responses over a buffered channel, then receives and returns only the first response, which is the quickest one to arrive. Thus `mirroredQuery` returns a result even before the two slower servers have responded. (Incidentally, it's quite normal for several goroutines to send values to the same channel concurrently, as in this example, or to receive from the same channel.)

[Click here to view code image](#part0138_split_021.html#id233pro01_r)

```
func mirroredQuery() string {
    responses := make(chan string, 3)
    go func() { responses <- request("asia.gopl.io") }()
    go func() { responses <- request("europe.gopl.io") }()
    go func() { responses <- request("americas.gopl.io") }()
    return <-responses // return the quickest response
}

func request(hostname string) (response string) { /* ... */ }
```

Had we used an unbuffered channel, the two slower goroutines would have gotten stuck trying to send their responses on a channel from which no goroutine will ever receive. This situation, called a *goroutine leak*, would be a bug. Unlike garbage variables, leaked goroutines are not automatically collected, so it is important to make sure that goroutines terminate themselves when no longer needed.

The choice between unbuffered and buffered channels, and the choice of a buffered channel's capacity, may both affect the correctness of a program. Unbuffered channels give stronger synchronization guarantees because every send operation is synchronized with its corresponding receive; with buffered channels, these operations are decoupled. Also, when we know an upper bound on the number of values that will be sent on a channel, it's not unusual to create a buffered channel of that size and perform all the sends before the first value is received. Failure to allocate sufficient buffer capacity would cause the program to deadlock.

Channel buffering may also affect program performance. Imagine three cooks in a cake shop, one baking, one icing, and one inscribing each cake before passing it on to the next cook in the assembly line. In a kitchen with little space, each cook that has finished a cake must wait for the next cook to become ready to accept it; this rendezvous is analogous to communication over an unbuffered channel.

If there is space for one cake between each cook, a cook may place a finished cake there and immediately start work on the next; this is analogous to a buffered channel with capacity 1. So long as the cooks work at about the same rate on average, most of these handovers proceed quickly, smoothing out transient differences in their respective rates. More space between cooks—larger buffers—can smooth out bigger transient variations in their rates without stalling the assembly line, such as happens when one cook takes a short break, then later rushes to catch up.

On the other hand, if an earlier stage of the assembly line is consistently faster than the following stage, the buffer between them will spend most of its time full. Conversely, if the later stage is faster, the buffer will usually be empty. A buffer provides no benefit in this case.

The assembly line metaphor is a useful one for channels and goroutines. For example, if the second stage is more elaborate, a single cook may not be able to keep up with the supply from the first cook or meet the demand from the third. To solve the problem, we could hire another cook to help the second, performing the same task but working independently. This is analogous to creating another goroutine communicating over the same channels.

We don't have space to show it here, but the `gopl.io/ch8/cake` package simulates this cake shop, with several parameters you can vary. It includes benchmarks ([§11.4](#part0108.html#id-benchmarkfunctions)) for a few of the scenarios described above.

## 8.5 Looping in Parallel

In this section, we'll explore some common concurrency patterns for executing all the iterations of a loop in parallel. We'll consider the problem of producing thumbnail-size images from a set of full-size ones. The `gopl.io/ch8/thumbnail` package provides an `ImageFile` function that can scale a single image. We won't show its implementation but it can be downloaded from `gopl.io`.

[Click here to view code image](#part0138_split_022.html#id234pro01_r)

`gopl.io/ch8/thumbnail`

```
package thumbnail

// ImageFile reads an image from infile and writes
// a thumbnail-size version of it in the same directory.
// It returns the generated file name, e.g., "foo.thumb.jpg".
func ImageFile(infile string) (string, error)
```

The program below loops over a list of image file names and produces a thumbnail for each one:

[Click here to view code image](#part0138_split_023.html#id235pro01_r)

`gopl.io/ch8/thumbnail`

```
// makeThumbnails makes thumbnails of the specified files.
func makeThumbnails(filenames []string) {
    for _, f := range filenames {
        if _, err := thumbnail.ImageFile(f); err != nil {
            log.Println(err)
        }
    }
}
```
