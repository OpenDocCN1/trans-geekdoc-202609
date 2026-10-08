
Either version obtains a directory listing and stores it in $out. It can be echoed to the browser or dealt with in any other way.

There are other ways of executing commands on the server. We cover them in Chapter 17, "Interacting with the File System and the Server."

## Array Operators

There are a number of array operators. The array element ([]) enable you to access array elements. You can also use the => operator in some contexts. These operators are covered in Chapter 3.

You also have access to a number of other array operators. We cover them in detail in Chapter 3 as well, but we included them here in Table 1.6 for completeness.

Table 1.6 PHP's Array Operators

| Operator | Name | Use | Result |
| --- | --- | --- | --- |
| + | Union | $a + $b | Returns an array containing everything in $a and $b |
| == | Equality | $a == $b | Returns true if $a and $b have the same key and value pairs |
| === | Identity | $a === $b | Returns true if $a and $b have the same key and value pairs in the same order and of the type |
| != | Inequality | $a != $b | Returns true if $a and $b are not equal |
| <> | Inequality | $a <> $b | Returns true if $a and $b$ are not equal |
| !== | Non-identity | $a !== $b | Returns true if $a and $b$ are not identical |

You will notice that all array operators in Table 1.6 have equivalent operators that work on scalar variables. As long as you remember + performs addition on scalar types and union on arrays—even if you have no interest in the set arithmetic that behavior—the behaviors should make sense. You cannot use compare arrays to scalar types.

## The Type Operator

There is one type: instanceof. This operator is used in object-oriented programming, but it is mentioned here for completeness. (Object-oriented programming is covered in Chapter 6.)

The instanceof operator allows you to check whether an object is an instance of a particular class, as in this example:

```php
class sampleClass {};
$myObject = new sampleClass();
if ($myObject instanceof sampleClass) {
  echo "MyObject is an instance of sampleClass";
```

## Working Out the Form Totals

Now that you know how to use PHP's operators, you are ready to work out the totals and tax on Bob's order form. To do this, add the following code to the bottom of your PHP script:

```php
$totalqty = 0;
$totalqty = $tireqty + $oilqty + $sparkqty;
echo $item->Items ordered: ".$totalqty.".<br />";
$totalamount = 0.00;
```

```php
define('TIREPRICE', 100);
define('OILPRICE', 10);
define('SPARKPRICE', 4);
```

```php
$totalamount = $tireqty * TIREPRICE
+ $oilqty * OILPRICE
+ $sparkqty * SPARKPRICE;
```

```php
echo "Subtotal: ".number_format($totalamount,2)."<br />";
```

```php
$taxrate = 0.10; // local sales tax is 10%
$totalamount = $totalamount * (1 + $taxrate);
echo "Total including tax: ".number_format($totalamount
```

If you refresh the page in your browser window, you should see output similar to Figure 1.5.
As you can see, this piece of code uses several operators. It uses the addition (+) and multiplication (*) to work out the amounts and the string concatenation operator (.) to set up the output to the browser.

![](img/654520c37415debd4290b9b4aa2c03f2_67_0.png)

Figure 1.5 The totals of the customer's order have been calculated, formatted, and displayed

## Understanding Precedence and Associativity

It also uses the number_format () to format the totals as strings with two decimal places. This is a function from PHP's Math library.

If you look closely at the calculations, you might ask why the calculations were performed in the order they were. For example, consider this statement:

```php
$totalamount = $tireqty * TIREPRICE
 + $oilqty * OILPRICE
 + $sparkqty * SPARKPRICE;
```

The total amount seems to be correct, but why were the multiplications performed before the answers? The answer lies in the precedence of the operators—that is, the order in which they are evaluated.

## Understanding Precedence and Associativity

In general, operators have a set precedence, or order, in which they are evaluated. Operators also have associativity, which is the order in which operators of the same precedence are evaluated. This order is generally left to right (called left for short), right to left (called right for short), or not relevant.

Table 1.7 shows operator precedence and associativity in PHP. In this table, operators with the lowest precedence are at the top, and precedence increases as you go down the table.

Table 1.7 Operator Precedence in PHP

| Associativity | Operators |
| --- | --- |
| left | Or |
| left | Xor |
| left | And |
| right | Print |
| left | = += - *= = / % = && | ^ <= <= >> |
| left | ? |
| left | || |
| left | && |
| left | | |
| left | ^ |
| left | & |
| n/a | == != === !== |

## Chapter 1 PHP Crash Course

## Associativity Operators

| Associativity | Operators |
| --- | --- |
| n/a | < <= > >= |
| left | << >> |
| left | + - |
| left | * / % |
| right | ! |
| n/a | Instanceof |
| right | - (int) (float) (string) (array) (object) (bool) @ |
| n/a | ++ |
| right | [] |
| n/a | clone new |
| n/a | () |

Notice we haven't yet covered the operator with the highest precedence: plain old parentheses. The effect of using parentheses is to raise the precedence of whatever is contained within them. This is how you can deliberately manipulate or work around the precedence when you need to.

Remember this part of the example:

```php
$totalamount = $totalamount * (1 + $taxrate);
```

If you had written

```php
$totalamount = $totalamount * 1 + $taxrate;
```

## Using Handling Functions

Before we leave the world of variables and operators, let's look at PHP's variable handling functions. PHP provides a library of functions that enable you to manipulate and test variables in different ways.

### Testing and Setting Variable Types

Most of the variable functions are related to the type. The two most general are gettype() and settype(). They have the following prototypes; that is, what arguments expect and what they return:

```php
string gettype(mixed var);
bool settype(mixed var, string type);
```

To use gettype(), you pass a variable. It determines the type and returns a string the type name: bool, int, double (for floats, confusingly, for historical records), string array, resource, or NULL. It returns unknown type if it is not one the standard types.

To use settype(), you pass a variable for which you want to change the type and a string containing the new type for that variable from the previous list.

> Note
> This book and the php.net documentation reference to the data type "mixed". There is no such type, because PHP is so flexible with type handling, functions can take many (or any) data types as argument. Arguments for many types are permitted are shown with the pseudo-type "mixed".

You can use these functions as follows:

```php
$a = 56;
echo gettype($a).'<br />';
settype($a, 'float');
echo gettype($a).'<br />';
```

When settype() is called the first time, the type of $a is integer. After the call to settype(), the type is changed to float, which is reported as double. (Be aware of this difference).

PHP also provides some type-checking functions. Each takes a variable as an argument and returns true or false. The functions are

- is_array()Checks whether the variable is an array
- is_double(), is_float(), is_real() (All the same function)—Checks the variable is a float
- is_long(), is_int(), is_integer() (All the same function)—Checks the variable is an integer
