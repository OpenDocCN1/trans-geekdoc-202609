
17. **(A)** During execution of the code, polymorphism (dynamic binding) guarantees that the appropriate `area` method for each `quad` in `quadList` will be selected. Choice B is wrong because the overridden method in the appropriate subclass is selected at run time—not the superclass method. Choice C is wrong because each of those subclasses inherit the `getLabels` method of `Quadrilateral`. Choice D would occur if `quadList` had a `null` value; but the precondition states that `quadList` is initialized. Choice E would occur if an attempt were made to alter `quadList` by adding or removing elements in the enhanced `for` loop.

18. **(E)** The algorithm has three steps:

**1.** Store the object at `i` in `temp`.

**2.** Place at location `i` the object at `j`.

**3.** Place `temp` at location `j`.

This has the effect of swapping the objects at `i` and `j`. Notice that choices B and C, while incomplete, are not incorrect. The question, however, asks for the *best* description of the postcondition, which is found in choice E.

19. **(A)** Subtracting 0.5 from a negative real number and then truncating it produces the number correctly rounded to the nearest integer. Note that casting to an `int` truncates a real number. The expression in choice B is correct for rounding a *positive* real number. Choice C won’t round correctly. For example, −3.7 will be rounded to −3 instead of −4. Choices D and E don’t make sense. Why cast to `double` if you’re rounding to the nearest integer?

20. **(E)** The method call `whatsIt(347)` puts on the stack `System.out.print(7)`.

The method call `whatsIt(34)` puts on the stack `System.out.print(4)`.

The method call `whatsIt(3)` is a base case and writes out `3`.

Now the stack is popped from the top, and the `3` that was printed is followed by `4`, then `7`. The result is `347`.

21. **(B)** Recall that insertion sort takes each element in turn and (a) finds its insertion point and (b) moves elements to insert that element in its correct place. Thus, if the array is in reverse sorted order, the insertion point will always be at the front of the array, leading to the maximum number of comparisons and data moves—very inefficient. Therefore choices A, C, and E are false.

Selection sort finds the smallest element in the array and swaps it with `a[0]` and then finds the smallest element in the rest of the array and swaps it with `a[1]`, and so on. Thus, the same number of comparisons and moves will occur, irrespective of the original arrangement of elements in the array. So choice B is true, and choice D is false.

22. **(E)** Method call I fails because `ClassOne` does not have access to the methods of its subclass. Method call II fails because `c2` needs to be cast to `ClassTwo` to be able to access `methodTwo`. Thus, the following would be OK:

```
((ClassTwo) c2).methodTwo();
```

Method call III works because `ClassTwo` inherits `methodOne` from its superclass, `ClassOne`.

23. **(D)** Notice that in the original code, if `n` is 1, `k` is incremented by 1, and if `n` is 4, `k` is incremented by 4. This is equivalent to saying “if `n` is 1 or 4, `k` is incremented by `n`.”

24. **(E)** Segment I will throw a `NullPointerException` when `s.equals...` is invoked, because `s` is a null reference. Segment III looks suspect, but when the `startIndex` parameter of the `substring` method equals `s.length()`, the value returned is the empty string. If, however, `startIndex` > `s.length()`, a `StringIndexOutOfBoundsException` is thrown.

25. **(A)** Since results of calculations with floating-point numbers are not always represented exactly (roundoff error), direct tests for equality are not reliable. Instead of the boolean expression `d == c`, a test should be done to check whether the difference of `d` and `c` is within some acceptable tolerance interval. (See the Box on comparing floating-point numbers, [p. 69](#47_Chapter39.xhtml#page_69).)

26. **(C)** If `arr` has elements `2`, `3`, `5`, the values of `value` are

![images](images/f046-02.jpg)

27. **(D)** In the binary search algorithm the interval containing `key` is repeatedly narrowed down by splitting it in half. For each iteration of the `while` loop, if `key` is in the list, `arr[first]` ≤ `key` ≤ `arr[last]`. Note that (i) the endpoints of the interval must be included, and (ii) `key` is not necessarily in the list.

28. **(B)**

![images](images/f047-01.jpg)

29. **(A)** The data structure is an array, not an `ArrayList`, so you cannot use the `add` method for inserting elements into the list. This eliminates choices B and D. Choice C gets integers from 0 to 99. The expression to return a random integer from `0` to `k-1` inclusive is

![images](images/f047-02.jpg)

Thus, to get integers from 0 to 100 requires `k` to be 101, which eliminates choice C. Choice E fails because it gets integers from 1 to 100.

30. **(A)** Suppose `str1` is `strawberry` and `str2` is `cat`. Then `insert(str1, str2, 5)` will return the following pieces, concatenated:

![images](images/f047-03.jpg)

Recall that `s.substring(k, m)` (a method of `String`) returns a substring of `s` starting at position `k` and ending at position `m-1`. String `str1` must be split into two parts, `first` and `last`. Then `str2` will be inserted between them. Since `str2` is inserted starting at position `5` (the `“b”`), `first` = `straw`, namely `str1.substring(0,pos)`. (Start at `0` and take all the characters up to and including location `pos-1`, which is `4`.) Notice that `last`, the second substring of `str1`, must start at the index for `“b”`, which is `pos`, the index at which `str2` was inserted. The expression `str1.substring(pos)` returns the substring of `str1` that starts at `pos` and continues to the end of the string, which was required. Note that you don’t need any “special case” tests. In the cases where `str2` is inserted at the front of `str1` (i.e., `pos` is `0`) or the back of `str1` (i.e., `pos` is `str1.length()`), the code for the general case works.

31. **(A)** Method `changeMatrix` examines each element and changes it to its absolute value if its row number equals its column number. The only two elements that satisfy the condition `r == c` are `mat[0][0]` and `mat[1][1]`. Thus, `-1` is changed to `1` and `-4` is changed to `4`, resulting in the matrix in choice A.

32. **(C)** Composition is the *has-a* relationship. A `PlayerGroup` *has-a* `Player` (several of them, in fact). By contrast, inheritance (choice D) is the *is-a* relationship, which doesn’t apply here. None of the choices A, B, or E apply in this example: Procedural abstraction is the use of separate methods to encapsulate each task (see [p. 198](#51_Chapter43.xhtml#page_198)); data encapsulation is combining the data and methods of an object in a class so that the data can be hidden (see [p. 93](#48_Chapter40.xhtml#page_93)); and `PlayerGroup` and `Player` are clearly dependent on each other since `PlayerGroup` contains several `Player` objects (see [p. 197](#51_Chapter43.xhtml#page_197)).

33. **(E)** All of these data structures are reasonable. They all represent 20 bingo numbers in a convenient way and provide easy mechanisms for crossing off numbers and recognizing a winning card. Notice that data structure II provides a very quick way of searching for a number on the card. For example, if 48 is called, `bingoCard[48]` is inspected. If it is `true`, then it was one of the 20 original numbers on the card and gets crossed out. If `false`, 48 was not on that player’s card. Data structures I and II require a linear search to find any given number that is called. (Note: There is no assumption that the array is sorted, which would allow a more efficient binary search.)

34. **(D)** A `NullPointerException` is thrown whenever an attempt is made to invoke a method with an object that hasn’t been created with `new`. Choice A doesn’t make sense: To test the `Caller` constructor requires a statement of the form

![images](images/f048-01.jpg)
