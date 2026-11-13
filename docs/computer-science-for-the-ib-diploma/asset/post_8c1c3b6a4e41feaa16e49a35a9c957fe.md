
## B2.4.4 Recursion (HL)

Base case: a terminating solution (that is not recursive) to a process.
General case: a process where the recursive call takes place.
Winding: a process occurring when recursive calls are made until the base case is reached.
Unwinding: a process occurring when the base case is reached, and the values are returned to build a solution.

Recursion represents a technique that involves the use of functions, procedures or algorithms calling themselves one or more times until one or more specific conditions are met, at which point the process unwinds itself to produce a solution, by processing the last call to the first.

Characteristics of a recursive algorithm include:

- a method or function that calls itself
- a termination condition or a base case – a termination solution that is not recursive; without a base case, the algorithm will run infinitely
- a general case that calls itself recursively or is defined in terms of itself, and moves towards the base case by changing its state (winding)
- unwinding, which occurs when the algorithm reaches the base case (cascades up until the original problem is solved or, in other words, is processing the results, starting at the last call and building up towards the base case).

Recursive algorithms provide elegant solutions to complex problems, by often using less code and fewer variables than iterative approaches. They allow the programmer to divide complex problems into smaller sub-problems that are more readable and easier to solve. However, if many recursive calls are made, there is a heavy use of the stack, a process that is memory intensive and could potentially lead to stack overflow, and the computer running out of memory. If the termination condition is not set correctly, the algorithm might run infinitely, or the system might crash or freeze due to the high number of recursive calls.

Recursion might take longer to execute than other techniques or iterative approaches, as each call takes a specific amount of time, in addition to the time required to build up the final solution.

Recursion can also be challenging to follow sometimes, which can make it difficult for other programmers to maintain, document or modify it.

Recursion can be used:

- to implement sorting algorithms, such as quick sort
- for fractal image creation
- for traversing binary trees or graphs
- for solving mathematical problems, such as factorial functions and towers of Hanoi.

When choosing whether to solve a problem by using a recursive algorithm, ask yourself the following questions:

- Is it possible to identify a base case?
- Is it possible to solve the problem by calling itself or splitting it into smaller instances of the same problem?
- Does it require data structures like graphs, trees or linked lists – data structures that can be seen as repetitive instances of itself?
- Does it require backtracking?
- Is there a mathematical expression that can be translated into a recursive algorithm?
- Are you solving the problem in a more elegant, simpler and logical way by using recursion, without sacrificing too much memory or performance?

## REVIEW QUESTIONS

- 1 Define the term "recursion".
- 2 Compare recursive and iterative algorithms.
- 3 Explain the need for a base case in a recursive program.
- 4 Identify one consequence of not using a base case in a recursive function.
- 5 Identify some advantages and disadvantages of using recursion.
- 6 Explain what steps you would take to debug a recursive function that does not work as expected.

## B2.4.5 Recursive algorithms (HL)

### Factorial of a number

One of the exercises in Section B2.3.4 required you to find the factorial of a number. You were able to solve this problem by using a loop. However, now you understand the concept of recursion, you can easily establish that this problem can be solved by using a recursive algorithm. Starting from the mathematical formula that defines the factorial of n: n! = n * (n-1)!, you can identify that 5! can be defined as 5 * 4! and 4! can be defined as 4 * 3!, and so on, until n = 1, which will return 1. The base case is when n = 1, as 1 will be returned, and the recursive call is when the method calls itself with n - 1 as a parameter. Therefore, the solution to this problem is:

```java
public static int factorial(int n) {
  if (n == 1) {
    return 1;
  }
  else {
    return n * factorial(n - 1);
  }
}
public static void main(String[] args) {
  int fact = factorial(5);
  System.out.println(fact);
}
```

```python
def factorial(n):
  if(n == 1):
    return 1
  else:
    return n * factorial(n - 1)
fact = factorial(5)
print(fact)
```

### Fibonacci sequence

Another application of a recursive method is in solving the Fibonacci sequence.
The Fibonacci sequence looks like this:
0, 1, 1, 2, 3, 5, 8, 13, 21, 34...

### THE FIBONACCI SEQUENCE

Each number is the sum of the two that precede it.

0 1 1 2 3 5 8 13 21
0 + 1 = 1
1 + 1 = 2
1 + 2 = 3
2 + 3 = 5
3 + 5 = 8
5 + 8 = 13
8 + 13 = 21

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_381_0.png)

- Fibonacci sequence
- F₀ = 0
- F₁ = 1
- F₂ = F₁ + F₀
- ...
- Fₙ = Fₙ₋₁ + Fₙ₋₂

To find the sequence for the first n terms, the base cases are identified as being F₀ and F₁, where the returned values would be 0 and 1 and the recursive call: Fₙ₋₁ + Fₙ₋₂.

```java
public static int fib(int n) {
    if (n == 0) {
        return 0;
    } else if (n == 1) {
        return 1;
    } else {
        return fib(n - 1) + fib(n - 2);
    }
}

public static void main(String[] args) {
    Scanner read = new Scanner(System.in);
    System.out.println("Enter a number: ");
    int n = read.nextInt();
    for (int i = 0; i < n; i++) {
        System.out.print(fib(i) + " ");
    }
}
```

```python
def fib(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    else:
        return fib(n - 1) + fib(n - 2)

n = int(input("enter a number: "))
for i in range(n):
    print(fib(i), " ", end="")
```

- Quicksort: a sorting algorithm that repeatedly selects an element as a pivot and partitions the other elements into two sub-arrays (lists): one that includes elements that are smaller than the pivot and the other one that includes elements that are larger than the pivot.

### Quicksort

If the bubble sort and selection sort discussed earlier use an incremental approach, the quicksort is an efficient sorting routine that uses the divide-and-conquer algorithm. The divide-and-conquer principle refers to dividing the problem into two or more identical, smaller sub-problems that can be solved individually, and their solutions combined to produce the solution to the larger problem.

The quicksort algorithm makes use of a pivot element from the data set, against which the other elements are compared, to identify their correct position. The pivot element can be the first element, the last element, a random element or the middle element in the data set. Imagine that the data structure is broken into two partitions (sections): one that contains elements smaller than the pivot and one that contains elements larger than the pivot.

A way to construct the quicksort algorithm is by implementing the following logic:

- Set the pivot as the middle element.
- Start at each end of the list by using a left pointer and a right pointer.
- Move the values smaller than the pivot to the left partition.
- Move the values larger than the pivot to the right partition.
- Recursively apply the same principle for the left partition until all elements are sorted.
- Recursively apply the same principle for the right partition until all elements are sorted.

```java
public static void quickSort(int start, int finish, int[] numbers) {
    if (start >= finish) {
        return;
    }

    int left = start;
    int right = finish;
    int pivot = numbers[(start + finish) / 2];
    System.out.print("start: " + start + " finish: " + finish + " left: " + left + " right: " + right + " pivot: " + pivot);
    while (left < right) {
        while (numbers[left] < pivot) {
            left = left + 1;
            System.out.println("left: " + left);
        }
        while (numbers[right] > pivot) {
            right = right - 1;
            System.out.println("right: " + right);
        }
        if (left <= right) {
            int temp = numbers[left];
            numbers[left] = numbers[right];
            numbers[right] = temp;
            left = left + 1;
            right = right - 1;
            System.out.println();
        }
    }
}
