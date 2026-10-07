conjunction with running the program.

# Listing 12.4

```
$ go build
$ time ./trace

2021/05/12 09:30:52 Searching 4000 files, found president 28000 times.
./trace 2.63s user 0.18s system 101% cpu 2.763 total
```

I can see that the program took ~2.7 second to process the 4k files. If I was only going to process 4k files, maybe even a few thousand more, I'd say this program is done. However, I would like the ability to process a million files and not have it hours.

I need to figure out a way to speed up this program. I could use a memory profile, but I know this program uses a lot of transient memory and there isn't much I can do about. I could use a cpu profile, but trust me it's going to tell me I am spending most of my time in system calls thanks to the call to os.OpenFile.

The problem with using a profiler here is a profiler can only tell me what is happening. I need to know what is and isn't happening to find a way to speed up this program. When I need to see what is not happening, the trace tooling is a good option.

# 12.2 Generating Traces

Since this program starts and stops within a few seconds, I can use the standard library to create a trace of this program. In general, creating traces for more than a few seconds of run time can be overwhelming since a trace generates a large amount of data. I want to focus on small, targeted traces.

# Listing 12.5

```
import (
    "runtime/trace"                <-- ADDED
)

func main() {
    trace.Start(os.Stdout)             <-- ADDED
    defer trace.Stop()                  <-- ADDED

    docs := make([]string, 4000)
    for i := range docs (
        docs[i] = fmt.Sprintf("newsfeed-%d.xml", i)
    }

    topic := "president"
    n := freq(topic, docs)
    log.Printf("Search %d files, found %d times.", len(docs), topic, n)
}
```

After adding the trace package into the imports, I can use the trace.Start and Stop