
# 14.2 Escape Analysis Mechanics

## Prelude

As of version 1.17, Go changed the ABI (application binary interface) to implement a new way of passing function input and output arguments using registers instead of the stack. This is enabled for Linux, MacOS, and Windows on the 64-bit x86 architectures. This means that some function arguments won't be copied over the stack, but some may depending on the viability of using registers. This doesn't change any of the semantics described in this post.

## Introduction

In the first post, I taught the basics of pointer mechanics by using an example in which a value was shared down a Goroutine's stack. What did I not show you is what happens when you share a value up the stack. To understand this, you need to learn about another area of memory where values can live: the "heap". With knowledge, you can begin to learn about "escape analysis".

Escape analysis is the process that the compiler uses to determine the placement of values that are created by your program. Specifically, the compiler performs code analysis to determine if a value can be placed on the stack frame for the function constructing it, or if the value must "escape" to the heap. In Go, there is no keyword or function you can use to direct the compiler in this decision. It's only through the convention of how you write your code that can impact this decision.

## Heaps

The heap is the second area of memory, in addition to the stack, used for storing values. The heap is not self-cleaning like the stack, so there is a bigger cost to use this memory. Primarily, the costs are associated with the garbage collector (GC), which must get involved to keep this area clean. When the GC runs, it will use 25% of your available CPU capacity. Plus, it can potentially create microseconds of "stop the world" latency. The benefit of having the GC is that you don't need to worry about managing heap memory, which historically has been complicated and error prone.

Values on the heap constitute memory allocations in Go. These allocations put on the GC because every value on the heap that is no longer referenced by a pointer needs to be removed. The more values that need to be checked and removed, the more work the GC must perform on every run. So, the pacing algorithm is constantly working to balance the size of the heap with the pace it runs.

## Sharing Stacks

In Go, Goroutine is allowed to have a pointer that points to memory on another Goroutine's stack. This is because the stack memory for a Goroutine can be replaced with a new block of memory when the stack has to grow or shrink. If the runtime has to track pointers to other Goroutine stacks, it would be too much to manage and the "stop the world" latency in updating pointers on those stacks would be overwhelming.

Here is an example of a stack that is replaced several times because of growth. Look at the output for lines 2 and 6. You will see the address of the string value inside the stack frame of main changes twice.

Listing 1

```
package main

const size = 4096

func main() {
    s := "HELLO"
    stackCopy(s, 0, [size]int{})
}

func stackCopy(s *string, c int, a [size]int) {
    println(c, s, "*")

    c++
    if c == 10 {
        return
    }

    stackCopy(s, c, a)
}

Output:
0 0xc00011ff68 HELLO
1 0xc00011ff68 HELLO

2 0xc00015ff68 HELLO <-- CHANGED
3 0xc00015ff68 HELLO
4 0xc00015ff68 HELLO
5 0xc00015ff68 HELLO

6 0xc0001dff68 HELLO <-- CHANGED
7 0xc0001dff68 HELLO
8 0xc0001dff68 HELLO
9 0xc0001dff68 HELLO
```

## Escape Mechanics

When a value is shared outside the scope of a function's stack frame, it will be placed (or allocated) on the heap. It's the job of the escape analysis algorithms to find these situations and maintain a level of integrity in the program. The integrity is in making sure that access to any value is always accurate, consistent and efficient.

Look at this example to learn the basic mechanics behind escape analysis.

Listing 2

```
01 package main
02
03 type user struct {
04     name string
05     email string
06 }
007
08 func main() {
09     u1 := createUserV1()
10     u2 := createUserV2()
11
12     println("u1", &u1, "u2", &u2)
13 }
14
15 //go:noinline
16 func createUserV1() user {
17     u := user(
18         name: "Bill",
19         email: "bill@ardanlabs.com"
20     )
21
22     println("V1", &u1)
23     return u
24 }
25
26 //go:noinline
27 func createUserV2() *user {
28     u := user(
29         name: "Bill",
30         email: "bill@ardanlabs.com"
31     )
32
33     println("V2", &u2)
34     return &u2
35 }
```

I am using the go:noinline directive to prevent the compiler from inlining these functions directly in main. Inlining would erase the function calls and in listing 3, you can see the construction of a user value performed on lines 17 through 20. Then on line 23, a copy of the user value is passed up the stack and back to the caller. After the function returns, the stack looks like this.

Figure 1
img/8be06d78925d0ade251ebad63_282.png

You can see in Figure 1, a user value exists in both frames after the call to createUserV1. In Version 2 of the function, pointer semantics are used on the return.

Listing 4

```
27 func createUserV2() *user {
28   u := user{
29     name: "Bill",
30     email: "bill@ardanlabs.com",
31   }
32
33   println("V2", &u)
34   return &u
35 }
```

I said the function is using pointer semantics on the return because the user value created by this function is shared up the call stack. This means the calling function is receiving a copy of the value. You can see the same struct literal used on lines 28 through 31 to construct a user value, but on line 34 the return is different. Based on this, you might think that the stack looks like this after the call, but this is NOT what is happening.

Figure 2
img/8be06d78925d0ade251ebad63_283.png

If what you see in Figure 2 was really happening you would have an integrity issue. The pointer is pointing down the call stack into memory that is no longer valid. On the next function call by main, that memory being pointed to is going to be re-framed and reinitialized. This is where escape analysis begins to maintain integrity. In this case, the compiler will determine it's not safe to construct the user value inside the stack frame of createUserV2, so instead it will construct the user value on the heap. This will happen immediately during construction on line 28.

## Readability

As you learned in the last post, a function has direct access to the memory inside its frame, through the pointer, but access to memory outside its frame requires indirect access. This means access to values that escape to the heap must be done indirectly through a pointer as well. Remember what the code looks like for createUserV2.

Listing 5

```go
27 func createUserV2() *user {
28 u := user(
29 name: "Bill",
30 email: "bill@ardanlabs.com",
31 )
32
33 println("V2", &u)
34 return &u
35 }
```

The syntax is hiding what is really happening in this code. The variable declared on line 28 represents a value of type user. Construction in Go doesn't tell you whether a value lives in memory; it's not until the return statement on line 34 you know the value will need to escape. This means, even though u represents a value of type user, access to this user value must be happening through a pointer underneath the covers. You could visualize the stack looking like this after the function call.

Figure 3
img/8be06d78925d0ade251ebad63_284.png

The u variable on the stack frame createUserV2 represents a value that is on the heap, not the stack. This means using u to access the value requires pointer access and not what the syntax is suggesting. You might think, why not make u a pointer then, since access to the value it represents requires the use of a pointer anyway?

Listing 6

```go
27 func createUserV2() *user {
28     u := &user(
29         name: "Bill",
30         email: "bill@ardanlabs.com",
31     )
32 
33     println("V2", u)
34     return u
35 }
```

If you do this, you are walking away from an important readability gain you can have in your code. Step away from the entire function for a second and just focus on the return.

Listing 7

```go
34 return u
35 )
```

What does this return tell you? All that it says is that a copy of u is being passed up the call stack. However, what does the return tell you when you use the & operator?

Listing 8

```go
34 return &u
35 )
```

Thanks to the & operator, the return now tells you that u is being shared up the call stack and therefore escaping to the heap. Remember, pointers are for sharing. Replace the & operator for the word "sharing" as you read code. This is very powerful in terms of readability, something you don't want to lose.

Here is another example where constructing heap values using pointer semantics hurts readability.

Listing 9

```go
01 var u *user
02 err := json.Unmarshal([]byte(r), &u)
03 return u, err
```
