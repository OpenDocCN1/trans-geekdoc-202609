
![](img/8be06d78925d0d5a2d2ade851e9bad63_46_0.png)

The cost of copying a string is the same regardless of the size of a string, a two word copy.

## 3.5 Iterating Over Collections

Go provides two different semantics for iterating over a collection. I can iterate using value semantics or pointer semantics.

Listing 3.8

```go
// Value Semantic Iteration
for i, fruit := range strings {
    println(i, fruit)
}

// Pointer Semantic Iteration
for i := range strings {
    println(i, strings[i])
}
```

When using value semantic iteration, two things happen. First, the collection I'm iterating over is copied and I iterate over the copy. In the case of an array, the copy could be expensive since the entire array is copied. In the case of a slice, there is no real cost since only the internal slice value is copied and not the backing array. Second, I get a copy of each element iterated on.

When using pointer semantic iteration, I iterate over the original collection and I access each element associated with the collection directly.

## 3.6 Value Semantic Iteration

Given the following code and output.

Listing 3.9

```go
strings := [5]string("Apple", "Orange", "Banana", "Grape", "Plum")
for i, fruit := range strings {
    println(i, fruit)
}
```

Output:
0 Apple
1 Orange
2 Banana
3 Grape
4 Plum

The strings variable is an array of 5 strings. The loop iterates over each string in the collection and displays the index position and the string value. Since this is value semantic iteration, the range is iterating over its own shallow copy of the array and on each iteration the fruit variable is a copy of each string (the two word data structure).

Notice how the fruit variable is passed to the print function using semantics. The print function gets its own copy of the string value. By the time the string is passed to the print function, there are 4 copies of the string value (array, shallow copy, fruit variable and the print function's copy). All 4 copies are sharing the same backing array of bytes.

# Figure 3.4

![](img/8be06d78925d0d5a2d2ade851e9bad63_47_0.png)

Making copies of the string value is important because it prevents the string value from ever escaping to the heap. This eliminates non-productive allocation on the heap.

## 3.7 Pointer Semantic Iteration

Given the following code and output.

Listing 3.10

```go
strings := [5]string("Apple", "Orange", "Banana", "Grape", "Plum")
for i := range strings {
    println(i,strings[i])
}
```

Output:
0 Apple
1 Orange
2 Banana
3 Grape
4 Plum

Once again, the strings variable is an array of 5 strings. The loop iterates over each string in the collection and displays the index position and the string value. Since this is pointer semantic iteration, the for range is iterating over the strings array directly and on each iteration, the string value for each index position is accessed directly for the print call.

## 3.8 Data Semantic Guideline For Built-In Types

As a guideline, if the data I'm working with is a numeric, string, or bool, then use value semantics to move the data around my program. This includes declaring fields on a struct type.

Listing 3.11

```go
func Foo(x int, y string, z bool) (int, string, bool) {



type Foo struct {
    X int
    Y string
    Z bool
}
```

One reason I might take an exception and use pointer semantics is if I need the semantics of NULL (absence of value). Then using pointers of these types is an option, but document this if it's not obvious.

The nice thing about value semantics for these types is that I'm guaranteed that each function is operating on its own copy. This means writes to this data are isolated to that function. This helps with integrity and identifying bugs related to data corruption.

## 3.9 Different Type Arrays

It's interesting to see what the compiler provides as an error when assigning arrays of the same types that are of different lengths.

Listing 3.12

```go
var five [5]int
four := [4]int{10, 20, 30, 40}

five := four

Compiler Error:
cannot use four (type [4]int) as type [5]int in assignment
```

Here I declare an array of 4 and 5 integers initialized to its zero value state. Then try to assign them to each other and the compiler says, "cannot use four ([4]int) as type [5]int in assignment".

It's important to be clear what the compiler is saying. It's saying that an array of 4 integers and an array of 5 integers represent data of different types. The size of an array is part of its type information. In Go, the size of an array has to be known at compile time.

## 3.10 Contiguous Memory Construction

I want to prove that an array provides a contiguous layout of memory.

Listing 3.13

```go
five := [5]string("Annie", "Betty", "Charley", "Doug", "Bill")

for i, v := range five {
	fmt.Printf("Value[%s]\taddress[%p]\tIndexAddr[%p]\n", 
	v, &v[i])
}
```

Output:
Value[Annie]   Address[0xc000050250] IndexAddr[0xc000052180]
Value[Betty]   Address[0xc000050250] IndexAddr[0xc000052190]
Value[Charley] Address[0xc000050250] IndexAddr[0xc00005218a]
Value[Doug]    Address[0xc000050250] IndexAddr[0xc00005218b]
Value[Bill]    Address[0xc000050250] IndexAddr[0xc00005218c]
