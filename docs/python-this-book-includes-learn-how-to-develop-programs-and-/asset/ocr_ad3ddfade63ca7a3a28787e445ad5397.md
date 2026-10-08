return total
# Access the global variable
print('this is the initialized value ' + str(init))
# (Try to) access the local variable
print('this is the sum ' + str(total))
nYou will notice that you'll get a NameError that shows the name ‘total’ isn’t
defined when you attempt to display the local variable total that was defined
within the function body. On the flipside, the init variable can be displayed
without any issues.

# Anonymous Functions within Python

Anonymous functions also known as lambda because they use lambda.
Example:
double = lambda x: x*2
double(5)

The special thing about this function is that it doesn’t have a name like the
previous examples you’ve come across in the first part of this chapter.
You use lambda functions when you want a nameless function for short term
purposes. Specific contexts where this is relevant when you’re dealing
with filter(), map(), and reduce():
 functools import reduce
my_list = [1,2,3,4,5,6,7,8,9,10]
# Use lambda function with `filter`
filtered_list = list(filter(lambda x: (x*2 > 10), my_list))
# Use lambda function with `map`
mapped_list = list(map(lambda x: x*2, my_list))
# Use lambda function with `reduce`
reduced_list = reduce(lambda x, y: x+y, my_list)
print(filtered_list)
print(mapped_list)
print(reduced_list)

# The Main ( ) Function

If you’ve programmed with another language such as Java, you’ll agree that
the main function is needed to run functions. As you’ve seen in the previous
example, this function is not a must for Python. However, if you use a main
() function within your Python program, it can be handy to organize your
code logically.
It’s easy to define a main () function and call it the same way you’ve done