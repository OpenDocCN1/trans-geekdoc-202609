Variable scope is a fundamental concept in programming that determines where a variable can be used in a PHP script. Understanding the scope of variables is essential for writing well-structured code, avoiding logic errors and ensuring that our programs run smoothly.

In PHP, variables can have different scopes depending on their location in the script. Some variables can be accessed from anywhere in the script, while others are restricted to specific parts of the code.

In this section, we'll explore the different types of variable scope in PHP, how they're defined and used, and best practices for handling them effectively. We'll also look at common pitfalls associated with variable scoping and how to avoid them.

Let's start by taking a look at the main concepts behind variable scoping in PHP and how they affect the way we write our code.

# Global Scope

In PHP, variables declared outside any function have global scope. This means they can be accessed from anywhere in the PHP script, both inside and outside functions.

When a variable is declared outside any function, it automatically becomes a global variable. For example :

```
<?php
$global_variable = "I am a global variable";
function display_global_variable() {
```