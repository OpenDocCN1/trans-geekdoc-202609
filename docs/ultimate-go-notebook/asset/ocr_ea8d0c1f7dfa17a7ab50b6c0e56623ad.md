# Listing 12.19

```
$ go build
```

```
$ time /trace > t.out
2021/05/13 14:07:11 Searching 4000 files, found president 28000 times.
./trace > t.out 8.09s user 1.75s system 834% cpu 1.179 total
$ time /trace > t.out
2021/05/13 14:07:13 Searching 4000 files, found president 28000 times.
./trace > t.out 8.13s user 1.76s system 935% cpu 1.057 total
```

Surprisingly, this pooling version is slower than the fan-out by ~400ms. Time to look at the trace and gather the numbers.

# Figure 12.12

![](bbox=[0.119, 0.298, 0.905, 0.626])

On the surface this trace looks better with the number of Goroutines, the heap, and utilizing the full cpu capacity of the machine.

# Figure 12.13

![](bbox=[0.119, 0.731, 0.905, 0.913])