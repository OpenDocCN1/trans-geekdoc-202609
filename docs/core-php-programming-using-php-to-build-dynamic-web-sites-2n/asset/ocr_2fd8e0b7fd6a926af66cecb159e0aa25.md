# Chapter 5. ARRAYS

Single-Dimensional Arrays

Indexing Arrays

Initializing Arrays

Multidimensional Arrays

Casting Arrays

Referencing Arrays Inside Strings

Arrays collect values into lists. You refer to an element in an array using an index, which is often an integer but can also be a string. And the value of the element can be text, a number, or even another array. When you build arrays, you get multidimensional arrays. Arrays are used extensively by PHP's built-in functions, and coding would be nearly impossible without them. There are many functions designed simply for manipulating arrays. They are discussed in detail Chapter 9.

# Single-Dimensional Arrays

To refer to an element of an array, you use square brackets. Inside the brackets you put the index of the element, as in Listing 5.1. This construct may be treated exactly like a variable. You may assign a value or pass its value to a function. You do not have to declare anything about the array before you use it. Like variables, any element of an array will be created on the fly. If you refer to an array that does not exist, it will evaluate to zero or an empty string depending on the context.

Single-dimensional arrays are lists of values under a common name. But you might wonder, "Why bother?" $Cities3 and not worry about square brackets. One reason is that it's easy to create variables like "$Cities1, $Cities2" to loop through all values of an array. If you know that all the elements of an array have been added using consecutive numbers, you can use a for loop to get each element. PHP makes it easy to create arrays that work this way; if you leave out an index when assigning an array element, PHP will start at zero and use consecutive integers thereafter. If you run the code in Listing 5.2, you will discover that the four cities have indexes of 0, 1, 2, and 3.

Listing 5.1 Referencing Array Elements