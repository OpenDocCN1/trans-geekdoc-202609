# Listing 2

```
09    println("count:\tValue Of["
```

The use of the ampersand & operator to get the address of a variable's location is not novel, other languages use this operator as well. The output of line 09 should be similar to the output below if you run the code on a 32bit architecture like the playground.

# Listing 3

```
count:    Value Of[ 10 ] Addr Of[ 0x10429fa4 ]
```

# Function Calls

Next on line 12, the main function makes a call into the increment function.

# Listing 4

```
12    increment(count)
```

Making a function call means the Goroutine needs to frame a new section of memory on the stack. However, things are a bit more complicated. To successfully make this call, data is expected to be passed across the frame boundary and placed into the new frame during the transition. Specifically, an integer value is expected to be copied and passed during the call. You can see this requirement by looking at the declaration of the increment function on line 18.

# Listing 5

```
18 func increment(inc int) {
```

If you look at the function call to increment again on line 12, you can see the code is passing the "value" of the count variable. This value will be copied, passed and placed into the new frame for the increment function. Remember, the increment function can only directly read and write to memory within its own frame, so it needs the inc variable to receive, store and access its own copy of the count value being passed.

Just before the code inside the increment function starts executing, the Goroutine's stack (at a very high level) would look like this: