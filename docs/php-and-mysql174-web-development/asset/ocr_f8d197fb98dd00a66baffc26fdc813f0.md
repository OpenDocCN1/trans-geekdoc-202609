# Other Useful Features

Some PHP functions and features do not fit into any particular category. This chapter explains these features.

Key topics covered in this chapter include

+   - Evaluating strings with eval()
- Terminating execution with die and exit
- Serializing variables and objects
- Getting information about the PHP environment
- Temporarily altering the runtime environment
- Highlighting source code
- Using PHP on the command line

Many of the examples you'll see in this chapter are brief code snippets that you can use as the basis of larger code elements in your applications.

# Evaluating Strings: eval()

The function eval() evaluates a string as PHP code. For example,
eval("echo 'Hello World!';");
takes the contents of the string and executes it.
echo "Hello World";

At first glance, this function may not seem all useful, but in fact eval() can be useful in a variety of cases. For example, you might want to store blocks of code in a database, retrieve them, and then evaluate them at a later point. You also might want to generate code in a loop and then use eval() to execute it.