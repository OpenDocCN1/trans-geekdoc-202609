print (word[i])

# String Immutability

Strings are an example of immutable data type. In other words, they cannot be modified once they are created.

What really goes on behind the scene is that Python defines a different string inside the computer memory and references that string rather than the previous one.

name = ‘superman'

![](bbox=[0.119, 0.281, 0.568, 0.323])

name = ‘wonder woman'

![](bbox=[0.119, 0.401, 0.568, 0.471])

In other words, it’s impossible to modify single characters within a string by applying notation. You may trigger an exception.
word = "Superman"
word[0] = "X"

# # Changing a String

To make changes to a string you will require to create a new String variable. This new variable can store the modified version of the string.
For instance, let’s take the following programming challenge:

"Write a program that replaces all vowels in a String with the underscore character."

At first, you may assume that you could simply apply String indexing to modify the characters in question. For instance:
word = "hello"
word[1] = "_"
word[4] = "_"

But strings are immutable, this will not work!
Instead, you need to define a new variable to store the changes and