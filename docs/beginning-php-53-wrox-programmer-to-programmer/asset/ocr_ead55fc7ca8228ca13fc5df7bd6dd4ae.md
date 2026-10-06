# Appendix A: Solutions to Exercises

# Chapter 8

# Exercise 1 Solution

To get the Calculator class to store two values, you need to create properties to hold them, and add a constructor that allows the calling code to store the values when creating a new Calculator object. Then it's simply a case of writing four methods to perform the relevant calculations on the values and return the results:

```
<!DOCTYPE html PUBLIC "//W3C//DTD HTML 1.0 Strict//EN"
"http://www.w3.org/TR/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml="en" lang="en">
<head>
<title>A simple Calculator class</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h2>A simple Calculator class</h2>
</body>
</html>

<?php

class Calculator {
    private $_val1, $_val2;

    public function __construct($val1, $val2) {
        $this->_val1 = $val1;
        $this->_val2 = $val2;
    }

    public function add() {
        return $this->_val1 + $this->_val2;
    }

    public function subtract() {
        return $this->_val1 - $this->_val2;
    }

    public function multiply() {
        return $this->_val1 * $this->_val2;
    }

    public function divide() {
        return $this->_val1 / $this->_val2;
    }
}
```