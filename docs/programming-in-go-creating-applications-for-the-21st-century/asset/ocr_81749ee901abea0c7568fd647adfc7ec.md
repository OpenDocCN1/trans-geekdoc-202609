# Chapter 5. Procedural Programming

The Boolean expression in the plain for loop syntax (203 ��, ➊ must be of type bool since Go will not automatically convert non-bools. (The Boolean and comparison operators are listed in Table 2.3, 57 ��.)

The second for ... range over a string syntax (203 ��, ➋) gives byte offset indices. For a 7-bit ASCII string, of value "Xabyz", it produces indices 0, 1, 2, 3, 4. For a UTF-8 string, of value "Q�YZ", the indices produced are 0, 1, 3, 5, 8. The first for ... range over a string syntax (203 ��, ➌) is almost always more convenient than the second (203 ��, ➋).

The second for ... range over an array or slice syntax (203 ��, ➎) produces items indexed from 0 to len(slice) - 1 for nonempty slices or arrays. This and the first for ... range over an array or slice syntax (203 ��, ➎) are often useful. These syntaxes in particular explain why for loops (203 ➊) are needed in Go programs.

The for ... range loops over key-value items (203 ��, ⬙) and over map keys (203 ��, ➎) if sorted is required one solution is to use the second syntax (203 ��, ➎) and populate a slice with the statement following the for loop, or—if the break statement—we show an example of this in the previous chapter ($4.3.4, 170 ��.) Another solution is to use an ordered data structure in the first—place or an ordered map. We will see an example of this in the next chapter ($6.5.3. ⬓.)

If any of the syntaxes (203 ��, ⬙) are used on an empty string, array, slice, or map, the loop harmlessly does nothing and the flow of control continues at the following statement.

A for loop can be broken out of any time with a break statement, with control passing to the statement following the for loop, or—the innermost enclosing for, switch, or select statement that has the specified label. It is also possible to make the flow of control return for the loop's condition or range clause to force the next iteration (or of the loop), by using a continue statement.

We have already seen numerous examples of statements in use; these include for range loops (89 ��, 172 ��, and 180 ��), infinite loops (23 �� and 45 ��), and the plain for loop (100 ��) that is needed infrequently in Go since the other loops are often more convenient. And we, of course, see many more for loop examples in the rest of the book, including some later in this chapter; so here we confine ourselves to one example.

Suppose that we have two-dimensional slices (e.g., of type [][]int), and there are two ways to search them to see if they contain a particular value. Both ways can perform the search. Use both the second for ... range over an array or slice syntax (203 ��, ➎).