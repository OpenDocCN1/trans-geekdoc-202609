Before sorting = [Bob: 31 John: 42 Michael: 17 Jenny: 26]
After sorting = [Michael: 17 Jenny: 26 Bob: 31 John: 42]

In Program we have declared a struct called We have defined the String() method in Student to print Student objects in a beautified way. Then, we have created a new type of Student slice, i.e., ByMarks and we have defined all three methods of interface on ByMarks type as follows:

It returns the length of the slice.

It swaps ith index element with jth index element.

It has logic to find which element is less between the ith index element and jth.

In the main function, we have a slice of Student with four elements. When we print students variable, it prints in the sequence in which these elements were inserted. In the next line, we are sorting the students variable by passing the sort.Sort() function. We have typecasted to the ByMarks type before passing it to the sort.Sort() function.

The above is unnecessarily complicated for sorting. The Len and Swap methods are unnecessary because the Sort function should have an internal logic to find the length of the slice and swap elements. The sort package has a function to overcome this complexity. We can use the Slice function of the sort package. We