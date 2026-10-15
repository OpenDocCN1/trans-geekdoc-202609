# 5.1 Concept of slices

Slice is a segment of an array that can be resized and hence, it is more flexible compared to arrays. Like arrays, slices are indexable and have a length. A slice is a lightweight structure that wraps and represents a portion of an array. Slices are created using the make function.

A slice is a variable-length sequence which stores elements of a similar type, and it’s not allowed to store different types of elements in the same slice. The first index position in a slice is always 0 and the last one is (length of slice − 1).