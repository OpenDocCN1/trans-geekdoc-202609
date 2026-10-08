# #3 Using Arrays

This chapter shows you how to use an important programming construct: arrays. The variables used in the previous chapters were scalar variables, which store a single value. An array is a variable that stores a set or sequence of values. One array can hold many elements, and each element can hold a single value, such as text or numbers, or another array. An array containing other arrays is known as a *multidimensional array*.

PHP supports arrays with both numerical and string indexes. You are probably familiar with numerically indexed arrays if you've used any other programming language, but you might not have seen arrays using string indexes before, although you may have seen similar things like hashes, maps, or dictionaries elsewhere. Rather than each element having a numeric index, you can use words or other meaningful information.

In this chapter, you continue developing the Bob's Auto Parts example using arrays to work more easily with repetitive information such as customer orders. Likewise, you write shorter code to do some of the things you did with files in the preceding chapter.

Key topics covered in this chapter include

+   - Numerically indexed arrays
- Non-numerically indexed arrays
- Array operators
- Multidimensional arrays
- Array sorting
- Array functions

# ## What Is an Array?

You learned about scalar variables in Chapter 1, "PHP Crash Course." A scalar variable is a named location in which to store a value; similarly, an array is a named place to store a *set of* values, thereby allowing you to group variables.