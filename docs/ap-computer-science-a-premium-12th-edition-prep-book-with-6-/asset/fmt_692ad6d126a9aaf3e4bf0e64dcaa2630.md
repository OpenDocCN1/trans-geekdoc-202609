
(D) `Clown c = list.remove(list.size());`

(E) `list.add(-1, new Clown());`

Refer to the following class for Questions 13 and 14.

![images](images/f014-01.jpg)

[13](#45_Chapter37.xhtml#fn0-13). What output will be produced by invoking `firstTestMethod` for a `Tester` object?

(A) `3 4 5`

(B) `4 5 6`

(C) `5 6 7`

(D) `0 0 0`

(E) No output will be produced. An `ArrayIndexOutOfBoundsException` will be thrown.

[14](#45_Chapter37.xhtml#fn0-14). What output will be produced by invoking `secondTestMethod` for a `Tester` object, assuming that `testArray` contains `3,4,5`?

(A) `3 4 5`

(B) `4 5 6`

(C) `5 6 7`

(D) `0 0 0`

(E) No output will be produced. An `ArrayIndexOutOfBoundsException` will be thrown.

Questions 15–17 refer to the following `Point`, `Quadrilateral`, and `Rectangle` classes.

![images](images/f015-01.jpg)

![images](images/f016-01.jpg)

[15](#45_Chapter37.xhtml#fn0-15). Which of the following statements about the `Point`, `Quadrilateral`, and `Rectangle` classes are false?

I. `Point` is a subclass of `Quadrilateral`.

II. `Point` is a subclass of `Rectangle`.

III. The `Rectangle` class inherits the constructor of `Quadrilateral`.

(A) I only

(B) II only

(C) III only

(D) I and II only

(E) I, II, and III

[16](#45_Chapter37.xhtml#fn0-16). Which represents correct `/* implementation code */` for the `Rectangle` constructor?

I. `super(theLabels);`

II. `super(theLabels, theTopLeft, theBotRight);`

III. `super(theLabels); topLeft = theTopLeft; botRight = theBotRight;`

(A) I only

(B) II only

(C) III only

(D) I and II only

(E) II and III only

[17](#45_Chapter37.xhtml#fn0-17). Refer to the `Parallelogram` and `Square` classes below.

![images](images/f017-01.jpg)

Consider an `ArrayList<Quadrilateral> quadList` whose elements are of type `Rectangle`, `Parallelogram`, or `Square`.

Refer to the following method, `writeAreas`:

![images](images/f017-02.jpg)

What is the effect of executing this method?

(A) The area of each `Quadrilateral` in `quadList` will be printed.

(B) A value of `0` will be printed for each element of `quadList`.

(C) A compile-time error will occur, stating that there is no `getLabels` method in classes `Rectangle`, `Parallelogram`, or `Square`.

(D) A `NullPointerException` will be thrown.

(E) A `ConcurrentModificationException` will occur.

[18](#45_Chapter37.xhtml#fn0-18). Refer to the `doSomething` method below.

![images](images/f018-01.jpg)

Which best describes the **postcondition** for `doSomething`?

(A) Removes from `list` the objects indexed at `i` and `j`

(B) Replaces in `list` the object indexed at `i` with the object indexed at `j`

(C) Replaces in `list` the object indexed at `j` with the object indexed at `i`

(D) Replaces in `list` the objects indexed at `i` and `j` with `temp`

(E) Interchanges in `list` the objects indexed at `i` and `j`

[19](#45_Chapter37.xhtml#fn0-19). Consider the `NegativeReal` class below, which defines a negative real number object.

![images](images/f019-01.jpg)

Here are some rounding examples:

![images](images/f019-02.jpg)

Which `/* implementation */` of `getRounded` produces the desired postcondition?

(A) `return (int) (getValue() - 0.5);`

(B) `return (int) (getValue() + 0.5);`

(C) `return (int) getValue();`

(D) `return (double) (getValue() - 0.5);`

(E) `return (double) getValue();`

[20](#45_Chapter37.xhtml#fn0-20). Consider the following method.

![images](images/f020-01.jpg)

What will be output as a result of the method call `whatsIt(347)`?

(A) `74`

(B) `47`

(C) `734`

(D) `743`

(E) `347`

[21](#45_Chapter37.xhtml#fn0-21). A large list of numbers is to be sorted into ascending order. Assuming that a "data movement" is a swap or reassignment of an element, which of the following is a true statement?

(A) If the array is initially sorted in descending order, then insertion sort will be more efficient than selection sort.

(B) The number of comparisons for selection sort is independent of the initial arrangement of elements.

(C) The number of comparisons for insertion sort is independent of the initial arrangement of elements.

(D) The number of data movements in selection sort depends on the initial arrangement of elements.

(E) The number of data movements in insertion sort is independent of the initial arrangement of elements.

[22](#45_Chapter37.xhtml#fn0-22). Refer to the definitions of `ClassOne` and `ClassTwo` below.

![images](images/f021-01.jpg)

Consider the following declarations in a client class. You may assume that `ClassOne` and `ClassTwo` have no-argument constructors.

`ClassOne c1 = new ClassOne();`

`ClassOne c2 = new ClassTwo();`

Which of the following method calls will cause an error?

I. `c1.methodTwo();`

II. `c2.methodTwo();`

III. `c2.methodOne();`

(A) None

(B) I only

(C) II only

(D) III only

(E) I and II only

[23](#45_Chapter37.xhtml#fn0-23). Consider the code segment

![images](images/f022-01.jpg)

Suppose that the given segment is rewritten in the form

![images](images/f022-02.jpg)

Given that `n` and `k` are integers and that the rewritten code performs the same task as the original code, which of the following could be used as

![images](images/f022-03.jpg)

[24](#45_Chapter37.xhtml#fn0-24). Which of the following will execute *without* throwing an exception?

![images](images/f022-04.jpg)

(A) I only

(B) II only

(C) III only

(D) I and II only

(E) II and III only

[25](#45_Chapter37.xhtml#fn0-25). Three numbers *a*, *b*, and *c* are said to be a *Pythagorean Triple* if and only if the sum of the squares of two of the numbers equals the square of the third. A programmer writes a method `isPythTriple` to test if its three parameters form a Pythagorean Triple:

![images](images/f023-01.jpg)

When the method was tested with known Pythagorean Triples, `isPythTriple` sometimes erroneously returned `false`. What was the most likely cause of the error?

(A) Round-off error was caused by calculations with floating-point numbers.

(B) Type `boolean` was not recognized by an obsolete version of Java.

(C) An overflow error was caused by entering numbers that were too large.

(D) `c` and `d` should have been cast to integers before testing for equality.

(E) Bad test data were selected.

[26](#45_Chapter37.xhtml#fn0-26). Refer to the following class containing the `mystery` method.

![images](images/f023-02.jpg)

Which best describes what the `mystery` method does?

(A) It sums the elements of `arr`.

(B) It sums the products `10*arr[0]` + `10*arr[1]` + ••• + `10*arr[arr.length-1]`.

(C) It builds an integer of the form *d*[1]*d*[2]*d*[3] ... *d[n]*, where *d*[1] = `arr[0]`, *d*[2] = `arr[1]`, ..., *d[n]*[] = `arr[arr.length-1]`.

(D) It builds an integer of the form *d*[1]*d*[2]*d*[3] ... *d[n]*, where *d*[1] = `arr[arr.length-1]`, *d*[2] = `arr[arr.length-2]`, ..., *d[n]*[] = `arr[0]`.

(E) It converts the elements of `arr` to base-10.

Questions 27 and 28 refer to the `search` method in the `Searcher` class below.

![images](images/f024-01.jpg)

[27](#45_Chapter37.xhtml#fn0-27). Which assertion is true just before each execution of the `while` loop?

(A) `arr[first]` < `key` < `arr[last]`

(B) `arr[first]` ≤ `key` ≤ `arr[last]`

(C) `arr[first]` < `key` < `arr[last]` or `key` is not in `arr`

(D) `arr[first]` ≤ `key` ≤ `arr[last]` or `key` is not in `arr`

(E) `key` ≤ `arr[first]` or `key` ≥ `arr[last]` or `key` is not in `arr`

[28](#45_Chapter37.xhtml#fn0-28). Consider the array `a` with values

4, 7, 19, 25, 36, 37, 50, 100, 101, 205, 220, 271, 306, 321

where 4 is `a[0]` and 321 is `a[13]`. Suppose that the `search` method is called with `first` = `0` and `last` = `13` to locate the `key` 205. How many iterations of the `while` loop must be made in order to locate it?

(A) 3

(B) 4

(C) 5

(D) 10

(E) 13

[29](#45_Chapter37.xhtml#fn0-29). Consider the following `RandomList` class.

![images](images/f025-01.jpg)

Which represents correct `/* code to add integer to list */`?

(A) `list[i] = (int) (Math.random() * 101);`

(B) `list.add((int) (Math.random() * 101));`
