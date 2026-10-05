# 36

# LANGUAGE FUNDAMENTALS

write anything into any existing variable or create a new one. It returns 'noupdate error when any attempt to write is:

```
a: 1

noupdate
```

In Chapter 5 we will see another way to replicate read-only mode dynamically when desired, by using reval function.

# Console dimension

The option -c rows columns sets the console size in terms of rows and columns. The default setup -c 25 80. In the case q is invoked through the HTTP protocol, the dimension of the display can be set using the capital "C", i.e.-C rows columns.

# Error trap

The option -e B with B binary variables sets the error trapping in the console. The error trapping is crucial for code debugging, which we will cover in Chapter 5.

# Garbage collection

The option -g b sets the garbage collection mode. q has two memory modes: the deferred mode, -g 0, and the immediate mode, -g 1. The deferred mode, where the memory is returned to the operating system when q is instructed to do so by running .q gc function or when memory allocation fails. The immediate mode is returning the memory to the operating system when it is not referenced any more. The trade-off is that immediate mode allows for more continuous memory management but with some overhead.

On the other hand, the deferred mode gives us control over when it happens. Notice that running .q gc explicitly attempts to coalesce coalesced memory blocks and, therefore, be more expensive - also return memory - when, especially in a process with a very fragmented heap, which usually happens when there are many listed created. Depending on the trade required memory to be free and performance-critical code, we may want to choose the appropriate tool for the appropriate scenario. For example, we would not add frequent calls to .q gc on a time-sensitive event processing (CEP) process, but by doing so during a quiet period or after q always returns unreference memory to the heap, so the g flag or explicitly running .q gc are useful when wanting to return memory back to the OS, recommended when having multiple processes or other applications computing for the same memory on.

# Logs

The option -l sets the logging of the session. The log can be enabled by setting:

```
>q fileName -1
```