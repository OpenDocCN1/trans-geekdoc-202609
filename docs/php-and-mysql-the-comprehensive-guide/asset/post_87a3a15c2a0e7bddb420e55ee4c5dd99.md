
This is always impractical if you only want to intercept one method. In such a case, you have to work with a somewhat inelegant case differentiation and check the name of the method, as in the following example. Figure 11.29 shows the result.

```php
<?php
class Computer {
public function __call($name, $parameter) {
if ($name == "drives") {
echo "Drives:<br />";
foreach ($parameter as $element) {
echo $element ."<br />";
}
}
}
}
$MyComputer = new Computer();
$MyComputer->fans("CPU", "Main");
$MyComputer->drives("C", "D", "E");
?>
```

### Listing 11.39 Check the Method Names Using Case Differentiation ("call_case.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_341_0.png)

### Figure 11.29 Only the "drives()" Method Is Processed

### __get()

__get(name) is the counterpart to __call(), but for properties. The method receives the name of the property as a parameter for all properties that are read out but are not provided in the class or are not accessible due to visibility (see Figure 11.30).

```php
<?php
class Computer {
//public $CPU = "The CPU";
public function __get($property) {
echo("$property is not set");
}
}
$MyComputer = new Computer();
echo $MyComputer->CPU;
?>
```

### Listing 11.40 "__get()" ("get.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_342_0.png)

### Figure 11.30 The "CPU" Property Is Not Set in the Method

**Tip**
In practice, you mainly need this method to intercept property calls that do not result in an error message.

### __set()

__set(name, value) receives the name of the undefined property and the value to which the property is to be set as parameters. You could of course indicate that the value cannot be specified because the property is not provided—but it could also be used to simply set the property and give it the value. In this case the class itself needs an attribute #[AllowDynamicProperties]. Otherwise the dynamic creation of the property is deprecated. The reason behind this is, that dynamic creation of properties results in a more difficulty to understand code if it is not well documented.

```php
<?php
#[AllowDynamicProperties] class Computer {
public function __get($property) {
echo("$property is not set");
}
public function __set($property, $value) {
$this->$property = $value; }
}
$MyComputer = new Computer();
$MyComputer->CPU = "4 GHZ";
echo $MyComputer->CPU;
?>
```

### Listing 11.41 "__set()" ("set.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_343_0.png)

### Figure 11.31 Setting a Property Dynamically

## 11.3.11 Traits

The purpose of traits is to provide methods that can be reused without directly defining their own class or class hierarchies. A trait is defined in a similar way to a class, using the `trait` keyword. The functions and (somewhat more rarely in practice) properties are defined in it:

```php
trait Converter {
private function mb2gb($mb) {
$gb = $mb / 1024;
return $gb;
}
}
```

This trait can then be used in the class with the `use` keyword:

```php
class Computer {
use Converter;
}
```

> **Note**
> 
> You can also use several traits within a class. To do this, simply write them in a comma-separated list after the `use` keyword.

Depending on its visibility, the method is then accessible inside or outside the class. The following listing contains the complete code, and Figure 11.32 shows the output.

```php
<?php
trait Converter {
private function mb2gb($mb) {
$gb = $mb / 1024;
return $gb;
}
}

class Computer {
use Converter;

public $RAM = "1024";
public function ramcheck() {
    $gb = $this->mb2gb($this->RAM);
    return "Computer has " . $gb . ' GB RAM';
}
}
class Laptop extends Computer {
    public $RAM = "4096";
}
$MyLaptop = new Laptop();
echo $MyLaptop->ramcheck();
?>
```

### Listing 11.42 Use of a Trait ("traits.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_344_0.png)

### Figure 11.32 The Method of the Trait Provides the Appropriate Conversion

> **Note**
> If you define several methods with the same name within a class structure, the overwriting sequence is as follows: priority is always given to the method that is defined directly in the respective class. This is followed by the trait that is used in the class. At the end of this ranking is a method from an inheriting class.

The methods in traits can be used quite flexibly, and both their names and their visibility can be changed. The former is particularly necessary if there could be name conflicts with several traits or methods in the class.

To change the name and visibility, there are two keywords that are placed in curly brackets after the use statement; if there are two traits with the same methods, then `instead of` decides which trait should be used. `as` allows you to specify an alias, a different name, for a method and to change the visibility—or to do only one of the two.

The following example shows two traits with identical `mb2gb()` methods. In the `Computer` class, it is then specified that the method from the `converter` trait is used for the identical methods. In addition, the visibility is increased to `protected` so that the method can be used in the inheriting class, `Laptop`. We make the method of the same name from the `Helpers` trait publicly accessible and assign the `convertRam()` alias. Figure 11.33 shows the output.

```php
<?php
trait Converter {
    private function mb2gb($mb) {
        $gb = $mb / 1024;
        return $gb;
    }
}

trait Helpers {
    private function mb2gb($mb) {
        $gb = $mb / 1024;
        return $gb . " Gigabyte";
    }
}

class Computer {
    use Converter, Helpers
    {
        Converter::mb2gb insteadof Helpers;
        Converter::mb2gb as protected;
        Helpers::mb2gb as public convertRam;
    }

    public $RAM = "1024";
}

class Laptop extends Computer {
    public $RAM = "4096";
    public function ramcheck() {
        $gb = $this->mb2gb($this->RAM);
        return "Computer has " . $gb . ' GB RAM';
    }
}

$MyLaptop = new Laptop();
echo $MyLaptop->ramcheck() . '<br />';
echo $MyLaptop->convertRam('2048');
?>
```

### Listing 11.43 Trait with Methods of the Same Name ("traits_methods_change.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_345_0.png)

### Figure 11.33 The Output Is Controlled by Two Trait Methods

## 11.4 Helpful and Useful Information

This section contains small but useful little helpers that take some of the work out of more complex requirements. You will also find extensions such as iterators and the Standard PHP Library (SPL).

### 11.4.1 Error Level

One useful option in PHP is to set up interception of errors. However, it is important to know that the error levels—the basic error types—have changed frequently in PHP.

In PHP 5.0, there was a new E_STRICT error level. However, it was not initially included in E_ALL. It was then "integrated" into E_ALL in PHP 5.4 so that E_STRICT errors were also thrown at the E_ALL error level. In PHP 7, E_STRICT was again completely removed, and the corresponding errors were split into the other error levels. E_ALL has been the standard since PHP 8.

The following example also shows the changes over time. In PHP 5.3, a new error level was added: E_DEPRECATED. It was primarily intended as support for modernization. This meant that all errors for functions that were officially no longer recommended were output. An example in OOP was call_user_method(). Like all error levels, E_DEPRECATED can be created at the level of php.ini or at the level of a script file. The example sets the error level to the maximum level using the error_reporting() function for PHP 5.3.

```php
<?php
error_reporting(E_ALL | E_STRICT);
class Computer {
    public function shutdown($seconds) {
        echo "Computer will shut down in $seconds seconds";
    }
}

$duration = 12;
$MyComputer = new Computer();

call_user_method("shutdown", $MyComputer, $duration);
?>
```

### Listing 11.44 Error Level as of PHP 5.3 ("php53_error_level.php")

In PHP 5.3, the call of call_user_method() is therefore known as E_DEPRECATED and is output as a corresponding error (see Figure 11.34). Since PHP 7, this assignment no longer exists. Accordingly, a "normal" error occurs here—a fatal error—because the corresponding obsolete method is no longer known.
