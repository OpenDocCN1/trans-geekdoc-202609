# Defining Functions

The initiation of a function in PHP is marked by the `function` keyword, succeeded by a distinctive function name and a pair of parentheses. These parentheses may encompass parameters, serving as placeholders for the data fed into the function when it's invoked. Encased within curly braces `{}`, the function body executes the designated code. The convention for naming functions mirrors that for variables, advocating for descriptive and intelligible names that enhance the code's clarity.

Parameters imbue functions with adaptability, permitting the passage of diverse data into the function for processing. The specification of default values for parameters augments the function's versatility, offering predefined behavior when arguments are not explicitly provided.

# Scope of Functions

The scope concept relates to the accessibility of variables and functions within a script. Functions in PHP possess their own local scope, meaning variables declared inside a function are accessible solely within that function's context and are non-existent post-execution. This segregation of variables to their respective functions underscores the principle of function scope, safeguarding against unintended interactions between the function's internals and the global scope or other functions.

Variables situated outside any function belong to the global scope and are not inherently accessible within functions unless explicitly brought into context using the `global` keyword or the `$GLOBALS` array. This clear demarcation between local and global scopes is pivotal in managing data flow within functions and across the application.