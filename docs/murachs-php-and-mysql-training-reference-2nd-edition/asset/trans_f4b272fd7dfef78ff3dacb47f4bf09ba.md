

## 如何编写属性

图14-3展示了如何编写类的属性。首先，你编写访问修饰符，后跟属性名和一个可选的初始值。初始值必须是标量值、标量值数组或NULL值。*标量值*是字面量数字、字符串或布尔值。

当你声明属性时，首先要编写访问修饰符来控制其可见性。如果省略访问修饰符，属性默认为public。然而，为了使代码更具可读性，通常认为始终编写访问修饰符是一种良好实践。

在大多数情况下，你应该为属性使用private修饰符，如第一个示例所示。这样，你就创建了一个*私有属性*，类外部的代码无法直接访问它。

在某些情况下，你可能希望使用public修饰符，如第二个示例所示。这样，你就创建了一个*公有属性*，类外部的代码可以直接访问它。请注意，这个公有属性还包含一个空字符串的默认值。

如果你使用了本章后面描述的继承，你可能希望为属性使用protected修饰符，如第三个示例所示。这将创建一个*受保护属性*，其工作方式类似于私有属性。你将在本章后面了解私有属性和受保护属性之间的区别。

虽然通常每个属性单独占一行，但你也可以在同一行编写多个属性，如第四个示例所示。这里，五个私有属性通过逗号分隔每个属性名，写在同一行。

### 如何编写属性

### 语法

```php
[ public | protected | private ] $propertyName [ = initialValue ];
```

### 一个私有属性

```php
private $firstName;
```

### 一个带默认值的公有属性

```php
public $comment = '';
```

### 一个受保护属性

```php
protected $counter;
```

### 同一行上的五个属性

```php
private $category, $id, $name, $description, $price;
```

### 说明

- *公有属性*可以被类外部的代码直接访问。
- *私有*和*受保护*属性不能被类外部的代码直接访问。
- 默认情况下，属性是公有的。因此，如果省略访问修饰符，属性就是公有的。
- 要为属性编写初始值，你必须提供标量值、标量值数组或NULL。*标量值*是字面量数字、字符串或布尔值。
- 要在同一行编写多个属性，你可以用逗号分隔属性名。

图14-3 如何编写属性

## 如何编写构造函数和析构函数

图14-4展示了如何编写*构造函数方法*，或简称*构造函数*。构造函数是一种特殊方法，当从类创建新对象时会自动执行。要编写构造函数方法，你需要编写public关键字和function关键字，后跟特殊函数名__construct（带有两个下划线）、一对圆括号和一个代码块。在圆括号内，你可以编写该方法的参数列表，每个参数用逗号分隔。

如果你没有为类编写构造函数方法，该类会自动提供一个不包含任何参数的默认构造函数，如第一个示例所示。在这种情况下，你可以从该类创建对象，但不能向该类传递任何参数。因此，你需要使用类的set方法来设置对象的属性。

当你编写构造函数时，通常的做法是编写为对象属性提供初始值的参数，如第二个示例所示。这里，Category类的构造函数接受两个参数，并用它们来初始化一个新的Category对象的属性。

一个PHP类只能有一个构造函数方法。因此，如果你需要向构造函数传递可变数量的参数，可以使用你在第13章学到的处理可变长度参数列表的技术。例如，在第三个示例中，Category类的构造函数为两个参数都提供了默认值。因此，从Category类创建对象的代码可以向构造函数传递零个、一个或两个参数。如果代码不传递任何值，两个属性都会被设置为NULL。

在类内部，你可以使用名为$this的特殊变量来引用当前对象。此外，你可以使用*对象访问运算符*（->）来访问对象的属性和方法。在本图中，第二个和第三个示例使用$this变量来访问当前Category对象的ID和name属性，最后一个示例调用了数据库连接对象的close方法。

*析构函数方法*，或简称*析构函数*，在对象不再可用时自动执行。这可能发生在程序执行到达函数或脚本末尾时。也可能发生在代码使用unset函数删除对对象的引用时。

析构函数通常用于在对象被删除之前释放资源，如文件句柄和数据库连接。然而，本书展示了如何使用PDO对象连接数据库，这些对象具有关闭数据库连接的析构函数。因此，如果你使用PDO进行数据库连接，就不需要为数据访问对象编写析构函数。

如果你需要编写析构函数，最后一个示例展示了如何编写。这里，析构函数调用数据库连接对象的close方法来关闭数据库连接。请注意，析构函数的语法与构造函数的语法类似。但是，你不能为析构函数编写任何参数。

### 如何编写构造函数方法

### 语法

```php
public function __construct([parameterList]) {
    // Statements to execute
}
```

### 默认构造函数

```php
public function __construct() { }
```

### Category类的构造函数

```php
public function __construct($id, $name) {
    $this->id = $id;
    $this->name = $name;
}
```

### 带默认值的Category类构造函数

```php
public function __construct($id = NULL, $name = NULL) {
    $this->id = $id;
    $this->name = $name;
}
```

### 如何编写析构函数方法

### 语法

```php
public function __destruct() {
    // Statements to execute
}
```

### 数据库类的析构函数

```php
public function __destruct() {
    $this->dbConnection->close();
}
```

### 说明

- *构造函数方法*，或简称*构造函数*，是一种特殊方法，当从类创建新对象时执行。它通常初始化对象的属性。
- *析构函数方法*，或简称*析构函数*，是一种特殊方法，当对象不再可用时执行。换句话说，当没有变量引用该对象时执行。这种类型的方法不能包含任何参数。
- 在类内部，名为$this的特殊变量存储对当前对象的引用。因此，它允许你访问当前对象的属性和方法。
- *对象访问运算符*（->）提供对对象属性和方法的访问。当你编写对象访问运算符时，两个字符之间不能有空格。

图14-4 如何编写构造函数和析构函数

## 如何编写方法

### 语法

```php
[public | private | protected] function functionName ([parameterList]) {
    // Statements to execute
}
```

### 一个公有方法

```php
public function getSummary() {
    $maxLength = 25;
    $summary = $this->description;
    if (strlen($summary) > $maxLength) {
        $summary = substr($summary, 0, $maxLength - 3) . '...';
    }
    return $summary;
}
```

### 一个私有方法

```php
private function internationalizePrice($country = 'US') {
    switch ($country) {
        case 'US':
            return '$' . number_format($this->price, 2);
        case 'DE':
            return number_format($this->price, 2, ',', '.') . ' DM';
        default:
            return number_format($this->price, 2);
    }
}
```

### 一个访问当前对象属性的方法

```php
public function showDescription() {
    echo $this->description;
}
```

### 一个调用当前对象方法的方法

```php
public function showPrice($country = 'US') {
    echo $this->internationalizePrice($country);
}
```

### 说明

- 要在类中编写方法，你需要编写一个访问修饰符关键字，后跟function关键字、方法名、一对圆括号中的可选参数列表，以及要执行的代码块。
- 默认情况下，方法是公有的。因此，如果省略访问修饰符，方法就是公有的。然而，为了使代码更加一致和可读，通常认为为所有方法编写访问修饰符是一种良好实践。

