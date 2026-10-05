# INTRODUCTION

A function is a block of code which can be called from any point in a script after it has been declared. It is basically a compartmentalized PHP script designed to accomplish a single task. Furthermore, code contained within functions is ignored until the function is called from another part in the script. Functions are useful because they contribute to rapid, reliable, error-reducing coding, and increase legibility by tidying up complicated code sequences.

# 3.1 FUNCTIONS IN PHP

A function is a piece of code in a larger program. The function performs a specific task. The advantages of using functions are:

+   - Reducing duplication of code
- Decomposing complex problems into simpler pieces
- Improving clarity of the code
- Reuse of code
- Information hiding

There are two basic types of functions. Built-in functions and user defined ones. The built-in functions are part of the PHP language. Examples are: phpinfo(), round() or abs(). The user defined functions are created by application programmers to cover their needs. They are created with the function keyword.

# 3.1.1 PHP defining functions

A function is created with the function keyword.
simple.php

```
<?php

function displayVersion() {

    echo "this is PHP " . .phpversion();
    echo "\n";
}
```