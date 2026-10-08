# Appendix G. PHP STYLE GUIDE

This is a sample style guide based on the one used by the FreeTrade project <http://www.working-dogs.com/freetrade>.

# Comments

Every file should start with a comment block describing its purpose, version, author, and a copyright message. The comment block should be a block comment in the style below.

```
/
** File: test
** Description: This is a test program
** Version: 1.0
** Created: 1/1/2000
** Author: Leon Atkinson
** Email: leon@clearink.com
**
** Copyright (c) 2000 Your Group. All rights reserved.
/
```

Every function should have a block comment specifying name, input/output, and what the function does. 

```
/
** Function: doAdd
** Input: INTEGER a, INTEGER b
** Output: INTEGER
** Description: Adds two integers
/
function doAdd($a, $b)
{
    return(a+b);
}
```

Ideally, while, if, for or similar block of code should be preceded by a comment explaining what happens in the block. Sometimes this is unnecessary. 

```
// get input from user char by char
while(getInput($inputChar))
```