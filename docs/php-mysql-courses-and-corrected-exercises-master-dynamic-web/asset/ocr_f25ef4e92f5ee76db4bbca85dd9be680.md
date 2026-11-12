| $_myvariable | $*variable |
|---|---|
| $myvariable1 | $myvariable+ |
| MASTER2 | |
| $_32monlastname | |

# # Assignment by value and assignment by reference

In PHP programming, when assigning values to variables, it's important to understand the concepts of assignment by value and assignment by reference. These two assignment methods determine how data is manipulated and shared between variables in a PHP script.

# ## Assignment by value :

When a variable is assigned by value, a copy of the source variable's value is created and assigned to the target variable. This means that the two variables have separate values stored in different memory locations. Any changes made to the target variable do not affect the source variable, and vice versa. This allows independent manipulation of data between variables.

# ### Example: