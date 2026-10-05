
进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

## Loop Form

```html
<html><head><title>loop form</title></head><body><form action="loop.php" method="post"><p> Value for X starting point: <input type="text" name="xmin" size="20"><p> Value for maximum value of X:<input type="text" name="xmax" size="20"><p>Increment step for each value of X:<input type="text" name="xstep" size="20"><p><input type ="submit" name="submit"></form></body></html>
```

The PHP code is as follows:

```php
<?php$x =$_POST['xmin'];$y =$_POST['xmax'];$z =$_POST['xstep'];for($x=$x;$x<$y;$x=$x+$z)print "$x<br>";?>
```

The webpage will look as follows:

![](images/00014.jpeg)

The following PHP code demonstrates the while loop.

```php
<?php$x=0;while ($x<10){$x=$x+1;print"$x";}?>
```

The `while` loop has the initial point outside the `while` loop and the increment steps within its statement body.

The loop continues until condition is not true. The output of this 1...10.

The following code demonstrates the `do...while` loop.

```php
<?php$x=0;do{$x=$x+1;print"$x";}while ($x<10);?>
```

The output will be the same as the `while` loop. 1...10.

In addition to the `break` statement in PHP there is an `Exit` and `die` statement. The `break` statement was seen in the `switch`.

Instead of exiting the current structure, the `Exit` and `die` language constructs terminate the execution of the PHP script.

All PHP code after the instance of either `Exit` or `die` will never be executed. HTML code after the use of these two constructs will not be send to the web browser.

The `die` construct will be used frequently in code that accesses files and databases. `Exit` is used often with the `header()` function.

# Chapter 4. Arrays

An Array was mentioned as a variable type in the beginning of the book. An array can consist of numbers and or strings. The array is given a name similar to a variable and the it has the ability to hold more than one value.

Example: An array can be made to include a list of cars as shown below.

`$car1 = ' Toyota';`

`$car2 = 'GM';`

`$car3 = 'Ford';`

`$car4 = 'Nissan';`

Array variable naming is as follows:

1\. Start with a `$` sign.
2\. Continue with a letter or underscore.
3\. Finish with any combination of letters or numbers or the underscore.

An array variable has an index system. An array stands out from other variables with the presence of the `[]` brackets. Thus, `$car[]` is an array variable.

The `$car[3]` stands for a specific element of the array at index position 3.

To create an array in PHP using the cars example do as follows:

`$car = array ('Toyota', 'GM' , 'Ford' , 'Nissan');`

The indexes are automatically assigned by PHP server. Here the model Toyota is indexed at 0. Array indexation automatically starts with 0. This can be changed if needed.

In the car array example, we can specifically put the model Toyota at index position 1 by doing the following.

`$car = array(1=> 'Toyota', 2=>'GM' , 3=>'Ford', 4=>'Nissan');`

For most purposes leaving the PHP server to index the values in the default manner will be sufficient.

```php
<?phpprint"This script will print an array of cars";$car = array ('Toyota', 'GM' , 'Ford' , 'Nissan');print "$car <p>";print_r($car);?>
```

The output from running this code will be as follows:

![](images/00015.jpeg)

The output above tells the following:

1\. Array values cannot be printed using the `print()` function used in the previous chapters.
2\. Array values can be printed using the `print_r()` function instead.
3\. When using the `print_r()` function the array prints out with its index position shown in number format.

There is no requirement that index positions should be numbers. Words can be used. Let us modify the above PHP code to illustrate this.

```php
<?phpprint"This script will print an array of cars";$car = array ('Yaris'=>'Toyota', 'Spark'=>'GM' , 'Escort'=>'Ford' ,'Pathfinder'=> 'Nissan'); print_r($car); ?>
```

The output of this code will be as follows:

![](images/00016.jpeg)

The output is more descriptive as the models are attached to the various car companies in this output. The models have become the index values. In the default setting for an array the elements of the array are referred to by the index number as follows: `$car[2]`.

The `range()` function can be used to create an array of items based on a range of values. For example:

`$num = range(1,20);`

`$alp = range('a', 't');`

The `range` function will allow for steps such as:

`$num = range(1,20,2);`

The `var_dump()` function when used with an array the values and structure of the array will be shown. Let us look at a code that will demonstrate these two functions next.

```php
<?phpprint"This script will print an array of cars";$car = array ('Yaris'=>'Toyota', 'Spark'=>'GM’, 'Escort'=>'Ford' ,'Pathfinder'=> 'Nissan');var_dump($car);print"<br>";$num= range(10,20,2);print"<br>";$alp= range('a','z',2);print_r($num);print"<br>";print_r($alp);?>
```

The output will be as follows:

![](images/00017.jpeg)

An array whose keys are numbers is called an indexed array and those with keys that are strings is called associative array. These two types have been illustrated in the two examples above.

It is possible to add more elements to an array. In the above two examples the car array was used. Once an array is defined in PHP it is possible to add more elements by using the equal to sign and the name of the array with the `[]` brackets.

Example:

`$car[] ='Mazda';`

`$car[] ='Hyundai';`

If a key is not specified in the brackets, then each new entry or element of the array will be appended to the existing list. If a key is mentioned in the brackets any value at that key index will be removed and the new element added to that location.

```php
<?phpprint"This script will print an array of cars";$car = array ('Toyota', 'GM' , 'Ford' , 'Nissan');$car[] = 'Mazda';$car[] ='Hyundai';print_r($car);?>
```

![](images/00018.jpeg)

The output will add the new car companies to end of the list as shown above. Let us modify the above script as follows.

```php
<?phpprint"This script will print an array of cars";$car = array ('Toyota', 'GM' , 'Ford' , 'Nissan');$num1= count($car);print "The original array has $num1 elements.<p>";$car[] = 'Mazda';$car[] ='Hyundai';print_r($car);$num2 =count($car);print"<p>The new array has $num2 elements. <br>";?>
```

The output of the code is as follows.

![](images/00019.jpeg)

The additional function in the above code is `count()` which is used to count the number of elements in the `car[]` array.

To delete an individual element from an array use the `unset()` function.

For example:

`unset($car[4]);`

`unset($xyz['name']);`

If applied to the entire array the whole array will be deleted. To reset an array- that is to empty it without deleting the array variable altogether) use the `array()` function.

For example:

`$car =array();`

Let us look at the following code.

```php
<?phpprint"This script will print an array of cars";$car = array ('Toyota', 'GM' , 'Ford' , 'Nissan');unset($car[2]);print_r($car);?>
```

![](images/00020.jpeg)

The value at index value 2 is now deleted.

PHP has a function to merge two arrays. The function `array_merge($array1,$array2)` can be used for this purpose. The names of the two arrays have to be entered into the brackets of the function.

For Example:

`$car1[] =('Toyota','GM','Ford');`

`$car2[] =('Nissan','Mazda','VW','Hyundai');`

Writing the code in the following manner will merge the two arrays.

```php
<?phpprint"This script will print an array of cars";$car1[] =('Toyota','GM','Ford');$car2[] =('Nissan','Mazda','VW','Hyundai');$car3 =array_merge($car1,$car2);print_r($car3);?>
```

The above merge of two arrays can also be achieved by writing as follows.

`$car3 = $car1 + $car2;`

There is only one way to retrieve an array element that is by indicating the key index value. If all elements of an array has to be printed a loop will be needed.

For example:
