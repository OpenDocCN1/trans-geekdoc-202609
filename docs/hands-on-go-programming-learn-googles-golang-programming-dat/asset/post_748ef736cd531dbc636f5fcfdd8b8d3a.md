
## 10.3.2 Arithmetic operator

Those who are coming from a C/C++ background would expect arithmetic operators on pointers. But for the sake of simplicity, the arithmetic operators are not allowed on pointers in the Go language. The arithmetic operators on pointers may lead to an illegal address which is very dangerous.

In the C family languages, the pointer arithmetic is very useful when iterating over an array because it is very fast. However, the hardware and compiler are so advanced nowadays that iterating arrays using indices is more efficient than using pointer arithmetic. So, there is no need for the pointer arithmetic to perform a fast iteration over the array.

## 10.4 Pointers on composite types

We have seen pointers on basic data types. Now, we will see the pointer in composite data types like array and slice

### 10.4.1.1 Declaration

There are two ways of creating a pointer to an array: by using the var keyword and by using the := operator.

### Declaration using the var keyword

[Program 10.9](#) declares a pointer to the array using the var keyword:

### Program 10.9

```go
package main

import "fmt"

func main() {
	var arr1 *[5]int
	var arr2 = [5]int{1, 2, 3, 4, 5}
	arr1 = &arr2
	fmt.Println((*arr1)[0])
}
```

The following will be the output for the above program:

```text
1
```

In **Program** we have declared a pointer to an array variable, using an asterisk We have declared the array of i.e., Then, we have assigned the address arr2 to We have printed the zeroth element of We can see in the output that the zeroth element arr1 is 1 because we have assigned arr2 to arr1 and arr2 has value 1 at the zeroth array location. Please note that we have used an asterisk to access the value on pointer array as

It is not necessary to use an asterisk to access elements on the pointer array. We can access an element of the pointer array, the same as an array variable. It looks very clear. **Program 10.10** accesses the pointer array element without using an asterisk:

### Program 10.10

```go
package main

import "fmt"

func main() {
var arr1 *[5]int
var arr2 = [5]int{1, 2, 3, 4, 5}
arr1 = &arr2
fmt.Println(arr1[0])
}
```

The following will be the output for the above program:

```text
1
```

The output Program 10.10 is similar to Program The code is almost similar except for one change, i.e., we are accessing the pointer array element without using an asterisk. It is just not It looks very clear and more readable.

When a pointer array is declared using the var keyword but has not assigned any address of the array and we try to access any element of the pointer array, the program will panic. This is demonstrated in Program

### Program 10.11

```
package main

import "fmt"

func main() {
var arr1 *[5]int
fmt.Println(arr1[0])
}
```

The following will be the error in the above program:

### Error 10.3

```
panic: runtime error: invalid memory address or nil pointer dereference
[signal SIGSEGV: segmentation violation code=0x1 addr=0x0 pc=0x109d09f]

goroutine 1 [running]:
```

main.main()
/Users/prithvipalsingh/go/src/workspace/main.go:7 +0x1f
exit status 2

In Program we have declared the pointer array but we have not assigned the address of the any array. When we run, it panics because we tried to get the zeroth element of the pointer array but there is no underlying array that exists.

### Declaration using := operator

Program 10.12 creates the pointer array using the := operator:

### Program 10.12

```go
package main

import "fmt"

func main() {
var arr2 = [5]int{1, 2, 3, 4, 5}
arr1 := &arr2
fmt.Println("Zeroth element of arr1:", arr1[0])
}
```

The following will be the output for the above program:

Zeroth element of arr1: 1

## 10.4.1.2 Pointer array as a function argument

We can pass a pointer array as a function argument. When we modify any element of the pointer array in calling the function, then that change will be reflected in the caller function. In Program we will modify one array index in the calling function and the new value will be available in the caller function:

### Program 10.13

```
package main

import "fmt"

func main() {
arr := [5]int{10, 20, 30, 40, 50}
modify(&arr)
fmt.Println("Array Elements", arr)
}

func modify(arr *[5]int) {
arr[0] = 100
}
```

The following will be the output for the above program:

Array Elements [100 20 30 40 50]

In Program we have initialized the array of int with size We have passed the address of the array into the modify function. In the modify function, we have changed the zeroth element of the array and assigned 100 to it. In the main function, we have printed the array. It prints the array elements mentioned in the output of Program You can see that the zeroth element of the array is 100 in the main function as well. This means that modification has been done in the calling function which is visible in the caller function.

Note: It is not a good practice to send the address array to the function. We should create a slice from the array with the default indexes and pass the slice in the function.

When we create a slice from the array with default indexes, the start index will be zero and the last index will be the length of the array minus 1. This means that it will create a slice with the whole array, and the underlying data structure of that slice will be an original array. Any modification to the slice will reflect in the original array.

### Program 10.14

```
package main
import "fmt"

func main() {
arr := [5]int{10, 20, 30, 40, 50}
modify(arr[:])
```

```
fmt.Println("Slice Elements", arr)
}
```

```
func modify(arr []int) {
arr[0] = 100
}
```

The following will be the output for the above program:

**Slice Elements [100 20 30 40 50]**

In Program we have defined a function, with the slice as an argument. The modify function modifies the zeroth element of slice and assigns In the main function, we have declared an array with the default value. In the next line, we have called the modify function. Please note that we have created a slice from the array (using and passed to the function. Finally, we have printed the array. We can see in the output of Program 10.14 that the zeroth element of the array has

## 10.4.2 Pointer to slice

We can create a pointer to the slice, but why do we need a pointer to the slice? We have already seen in Section 9.4.1.3 that if we modify any element of the slice, it will be visible to the caller function. So what is the use of a pointer to a slice?

A pointer to a slice is very frequently used in standard or custom libraries. Let us understand the importance of the pointer to a slice in Golang. As we know, slice is a dynamic data structure. We can append as many elements to a slice as we need. We have seen in Program 10.14 that when we modify an existing element of the slice in the calling function, it reflects in the caller function. But, when we append new elements to the slice in the calling, it does not reflect in the caller function. Let us see this in Program

### Program 10.15

```
package main

import "fmt"

func main() {
 s1 := []int{10, 20, 30, 40, 50}
 modify(s1)
 fmt.Println("Slice Elements", s1)
}
```

```
func modify(s1 []int) {
s1[0] = 100
s1 = append(s1, 60)
s1 = append(s1, 70)
}
```

The following will be the output for the above program:

# Slice Elements [100 20 30 40 50]

In Program we have modified the modify function. Apart from modifying the zeroth element of the slice, we are appending 60 and 70 to the slice. In the main function, we are calling the modify function and printing the slice in the next line. Please note that in the output of Program the appended values are not printed. Only the zeroth element is changed. This concludes that when the new element is appended to the slice in the calling function, the appended values are not reflected in the caller function.

As slice is a dynamic data structure, it is very important that when the calling function adds new values to the slice, it should be reflected in the caller function as well otherwise, there is no use of adding new value in the slice. This can be achieved using a pointer to the slice.

### Program 10.16

```
package main
```
