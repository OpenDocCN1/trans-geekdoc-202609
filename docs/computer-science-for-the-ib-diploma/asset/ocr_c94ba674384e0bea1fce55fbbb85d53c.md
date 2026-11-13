# SYLLABUS CONTENT

By the end of this chapter, you should be able to:

+   - B2.4.1 Describe the efficiency of specific algorithms by calculating their Big O notation to analyse their scalability
+   - B2.4.2 Construct and trace algorithms to implement a linear search and a binary search for data retrieval
+   - B2.4.3 Construct and trace algorithms to implement bubble sort and selection sort, evaluating their time and space complexities
+   - B2.4.4 Explain the fundamental concept of recursion and its applications in programming (HL)
+   - B2.4.5 Construct and trace recursive algorithms in a programming language (HL)

# B2.4.1 Big O notation

Complexity analysis of algorithms includes time and space analysis. Time complexity analysis refers to how long an algorithm will take to run or how many steps an algorithm will take to run, while space analysis refers to how much memory space it takes to run the algorithm.

# Time complexity

Consider the following algorithm:

```
```java
for(int i = 0; i<5;i++) {
    System.out.println("hello");
}
```
```

```
```python
for i in range (0,5):
    print("hello")
```
```

How many times will this loop repeat? The variable `i` will take values from 0 to 4 included; therefore, it is simple to say that the algorithm will repeat five times. If we are to replace the 5 with `n`, the algorithm will repeat `n` times and the time complexity will be of the order of `n`. This is written as O(n), which is known as Big O notation. The time it takes to run the algorithm is approximately proportional to `n`. The larger the `n`, the more accurate the approximation; therefore, when calculating the Big O notation, the worst-case analysis is considered (the larger the `n`, the better).

> Big O notation: used to find the upper bound (worst-case scenario or the highest possible amount) of the growth of a function; the longest time or space required to turn the input into output.

```
```java
for(int i = 0; i<n; i++) {
    System.out.println("hello");
}
```
```

```
```python
for i in range (0,n):
    print("hello")
```
```