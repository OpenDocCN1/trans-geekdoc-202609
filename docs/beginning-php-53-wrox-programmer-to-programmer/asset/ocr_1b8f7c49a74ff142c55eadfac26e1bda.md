# Chapter 7: Functions

Recursion is another technique that you can use if you need to work on a set of values. Generally speaking, it's usually easier to iteration than recursion; however, in certain situations recursion makes more sense. Practically any loop can be converted to recursion instead, and vice-versa.

Here's a quick overview of how recursion function operates:

+   - The recursive function is called by the calling code
- If the base, or condition, is met, the function does any processing required, then exits
- Otherwise, the function does any processing required, then calls itself to continue the recursion

Of course, you have to make sure that the base case is eventually reached, otherwise the function will keep calling itself indefinitely (causing an infinite loop).

# Try It Out Creating the Fibonacci Sequence with Recursion

Chapter 4 showed how to use looping to create the Fibonacci sequence of numbers. The following script is similar to that shown in Chapter 4, except it uses a recursive function to generate each value, rather than computing it.

```
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN">
<html xmlns="http://www.w3.org/TR/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Fibonacci sequence using recursion</title>
<link rel="stylesheet" type="text/css" href="common.css" />
<style>
th { text-align: left; background-color: #999; }
th, td { padding: 0.4em; }
tr.alt td { background: #ddd; }
</style>
</head>
<body>
<h2>Fibonacci sequence using recursion</h2>
<table cellspacing="0" border="0" style="width:20em; border: 1px solid #666;">
<tr>

<th>Sequence</th>

<th>Value</th>
</tr>
</tr>
</table>

<?php
$iterations = 10;
```

![](bbox=[0.142, 0.943, 0.952, 0.963])