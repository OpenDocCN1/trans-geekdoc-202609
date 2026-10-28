

## 如何防止方法被重写

### 包含 final 方法的类

```php
class Person {
    // Other properties and methods not shown here

    final public function getFirstName() {
        return $this->firstName;
    }
}
```

### 尝试重写 final 方法并导致致命错误的子类

```php
class Employee extends Person {
    // Other properties and methods not shown here

    // This method attempts to override a final method - fatal error
    public function getFirstName() {
        return ucwords($this->firstName);
    }
}
```

## 如何防止类被继承

### 一个 final 类

```php
final class Employee extends Person {
    // Properties and methods for class
}
```

### 尝试继承 final 类并导致致命错误的类

```php
class PartTime extends Employee {
    // Properties and methods for class
}
```

### 说明

- *final 方法*不能被子类中的方法重写。因此，所有子类都必须使用该方法的 final 版本。
- *final 类*不能被子类继承。

图 14-16 如何创建 final 类和 final 方法

## 如何创建接口

### 语法

```php
interface interfaceName {
    const constantName = constantValue;
    public function methodName( parameterList );
}
```

### 用于显示对象的接口

```php
interface Showable {
    public function show();
}
```

### 要求实现两个测试方法的接口

```php
interface Testable {
    public function test1($value1);
    public function test2($value1, $value2);
}
```

### 提供两个常量的接口

```php
interface EyeColor {
    const GREEN = 1;
    const BLUE = 2;
    const BROWN = 3;
}
```

### 继承一个类并实现一个接口的类

```php
class Employee extends Person implements Showable {
    // The constructor and the get and set methods are the same
    // as the Person class in figure 14-13

    // Implement the Showable interface
    public function show() {
        echo 'First Name: ' . $this->getFirstName() . '<br>';
        echo 'Last Name: ' . $this->getLastName() . '<br>';
        echo 'SSN: ' . $this->ssn . '<br>';
        echo 'Hire Date: ' . $this->hireDate . '<br>';
    }
}
```

### 实现三个接口的类声明

```php
class Customer extends Person implements Showable, Testable, EyeColor {...}
```

### 说明

- *接口*定义一组可以由类*实现*的公共方法。接口不提供实现这些方法的任何代码，但会提供方法名和参数列表。
- 接口中的所有方法都必须是公共的，并且不能是静态的。
- 实现接口的类必须为接口定义的每个方法提供实现。
- 接口可以定义可供实现该接口的任何类使用的类常量。
- 虽然一个类只能继承一个类，但它可以实现多个接口。

图 14-17 如何使用接口

## 观点

面向对象编程提供了许多好处。它促进了代码复用，并使测试、调试和维护代码变得更加容易。这些好处可以加快开发进度，尤其是在大型项目中。此外，由于面向对象技术允许你将代码组织为多个可作为独立模块运行的类，因此多个程序员在同一项目中协作也变得更加容易。

## 术语

|  |  |
|---|---|
| 面向对象编程 | 静态方法 |
| 类 | 类方法 |
| 对象 | 克隆对象 |
| 属性 | 浅拷贝 |
| 方法 | 内省 |
| 封装 | 反射 |
| 数据隐藏 | 继承 |
| 标量值 | 子类 |
| 公有属性 | 派生类 |
| 私有属性 | 子类 |
| 受保护属性 | 超类 |
| 构造方法 | 基类 |
| 构造函数 | 父类 |
| 析构方法 | 继承类 |
| 析构函数 | 扩展类 |
| 对象访问运算符 | 重写方法 |
| 实例 | 抽象类 |
| 实例化 | 抽象方法 |
| 对象链 | 具体类 |
| 类常量 | final 方法 |
| 作用域解析运算符 | final 类 |
| Paamayim Nekudotayim | 多重继承 |
| 静态属性 | 接口 |
| 类属性 |  |

## 总结

- 使用*面向对象编程*时，*类*定义了每种*对象*类型的*属性*和*方法*。然后，你可以使用这些属性和方法从类创建对象。
- *构造方法*（或简称*构造函数*）是类中用于从类创建对象的特殊方法。*析构方法*是在对象不再可供使用时执行的特殊方法。
- 对象是类的*实例*。从类创建对象的过程有时被称为*实例化*。
- *公有属性*可以被类外部的代码直接访问。*私有属性*和*受保护属性*不能被类外部的代码直接访问。
- *方法*是在类中编码的函数。可以从对象访问它。
- *对象访问运算符*（`->`）提供对对象属性和方法的访问。
- *类常量*是隶属于类的常量值，而不是隶属于从该类创建的对象。要访问类常量，你可以编写类名，后跟双冒号，这被称为*作用域解析运算符*。
- *静态属性或静态方法*是隶属于类的属性或方法，而不是隶属于从该类创建的对象。因此，这些属性和方法也被称为*类属性*和*类方法*。
- 要创建对对象的第二个引用，可以使用等号（`=`）运算符。要创建对象的副本（或*克隆*），必须使用 clone 运算符。
- 当你创建对象的副本时，PHP 会进行*浅拷贝*。这意味着 PHP 不会创建原始对象内嵌套对象的副本。
- 编写检查对象的代码被称为*内省*或*反射*。
- *继承*提供了一种基于现有类创建新类的方法。新类*继承*现有类的属性和方法。
- 继承自某个类的类被称为*子类*、*派生类*或*子类*。被另一个类继承的类被称为*超类*、*基类*或*父类*。
- 子类可以通过添加新的属性和方法来*扩展*超类。它还可以用自己的方法版本*重写*超类中的方法。
- *抽象类*是不能用来创建对象的类。*抽象方法*是规定了方法的名称和参数，但没有提供实现该方法的代码块的方法。
- *具体类*是可以用来创建对象的类。
- *final 方法*不能被子类中的方法重写。*final 类*不能被子类继承。
- *接口*定义了一组可以由类*实现*的公共方法。接口不提供实现这些方法的任何代码，但会提供方法名和参数列表。

## 练习 14-1 —— 修改 Product Manager 应用

在本练习中，你将修改并增强本章所述的 Product Manager 应用。此外，你还将修改并增强使用与 Product Manager 应用相同模型的 Product Catalog 应用。

### 打开并测试应用

1. 运行存储在 ex_starts/ch14_ex1 目录中的应用程序。
2. 通过添加和删除产品来测试该应用。
3. 打开此应用的 product_manager/index.php 文件并查看代码。然后，打开此应用的 model/category.php 和 model/product.php 文件并查看代码。

### 使用 set 方法在对象中设置数据

4. 修改 Category 类的构造函数，使其具有零个参数并将属性设置为默认值。
5. 修改应用中所有创建 Category 对象的代码，使其使用 set 方法在对象中设置数据。
6. 修改 Product 类的构造函数，使其具有零个参数并将所有属性设置为默认值。
7. 修改应用中所有创建 Product 对象的代码，使其使用 set 方法在对象中设置数据。
8. 通过添加和删除产品来测试该应用。

### 使用常规方法代替静态方法

9. 修改 CategoryDB 类，使其使用常规方法而不是静态方法。
10. 修改所有使用 CategoryDB 类的代码，使其创建 CategoryDB 对象并从该对象调用常规方法。
11. 修改 ProductDB 类，使其使用常规方法而不是静态方法。
12. 修改所有使用 ProductDB 类的代码，使其创建 ProductDB 对象并从该对象调用常规方法。
13. 通过添加和删除产品来测试该应用。

### 修改 Product Catalog 应用

14. 打开此应用的 product_catalog/index.php 文件并查看其代码。
15. 修改所有这些代码，使其能够与新模型正确配合使用。
16. 通过查看每个类别中至少一个产品来测试该应用。

