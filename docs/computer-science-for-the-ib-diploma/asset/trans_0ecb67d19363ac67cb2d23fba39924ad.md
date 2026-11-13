
## 编程练习

### 1 图书馆系统

创建一个简单的图书馆系统，其中每本书可以是可用或已借出状态。实现方法来管理每本书的状态并跟踪图书馆中书籍的总数。

```java
class Book {
    private static int bookCount = 0;
    private String title;
    private boolean isBorrowed;

    public Book(String title) {
        this.title = title;
        this.isBorrowed = false;
        bookCount++;
    }

    public void borrow() {
        if (!isBorrowed) {
            isBorrowed = true;
            System.out.println(title + " has been borrowed.");
        } else {
            System.out.println(title + " is already borrowed.");
        }
    }

    public void returnBook() {
        // Implement logic to mark the book as not borrowed
    }

    public static int getBookCount() {
        return bookCount;
    }

    public String toString() {
        return title + " - " + (isBorrowed ? "Borrowed" : "Available");
    }
}

public class Library {
    public static void main(String[] args) {
        Book[] books = new Book[5];
        books[0] = new Book("Java Fundamentals");
        books[1] = new Book("The Art of Computer Programming");
        // Add more books and implement borrowing logic
    }
}
```

- a 完成 returnBook 方法。
- b 实例化更多书籍并模拟借阅和归还书籍。
- c 打印所有书籍的状态和书籍总数。

### 2 简单库存系统

创建一个商店的基本库存管理系统。每个产品都有 ID、名称、价格和数量。实现添加产品、更新库存数量和列出所有产品的功能。

```java
class Product {
    private static int nextProductId = 100;
    private int productId;
    private String name;
    private double price;
    private int quantity;

    public Product(String name, double price, int quantity) {
        this.productId = nextProductId++;
        this.name = name;
        this.price = price;
        this.quantity = quantity;
    }

    public void updateQuantity(int amount) {
        // Implement logic to update product quantity
    }

    @Override
    public String toString() {
        return "Product{" +
                "productId=" + productId +
                ", name='" + name + '\'' +
                ", price=" + price +
                ", quantity=" + quantity +
                '}';
    }
}

class Inventory {
    private Product[] products;
    private int size;

    public Inventory(int capacity) {
        products = new Product[capacity];
        size = 0;
    }

    public boolean addProduct(Product product) {
        if (size < products.length) {
            products[size] = product;
            size++;
            return true;
        }
        return false;
    }

    public void listProducts() {
        for (Product product : products) {
            if (product != null) {
                System.out.println(product);
            }
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Inventory inventory = new Inventory(100);
        inventory.addProduct(new Product("Laptop", 999.99, 10));
        inventory.addProduct(new Product("Smartphone", 499.99, 20));
        // Update quantities and list inventory
    }
}
```

- a. 在 Product 类中实现 updateQuantity 方法以调整产品的库存。
- b. 测试添加产品、更新数量和列出所有产品，以确保库存正确显示。

## B3.2 多类 OOP 基础 (HL)

### 教学大纲内容

- B3.2.1 解释并应用 OOP 中继承的概念以促进代码重用
- B3.2.2 构建代码来建模多态及其各种形式，例如方法重写
- B3.2.3 解释 OOP 中抽象的概念
- B3.2.4 解释组合和聚合在类关系中的作用
- B3.2.5 解释 OOP 中常用的设计模式

### B3.2.1 继承和代码重用

> **知识论**
> 我们组织或分类知识的方式如何影响我们所知道的内容？
> 将 OOP 中的知识分类为对象、类和继承会影响问题的处理和解决方式。

> **继承**：一个类将现有类的副本作为其所有内部方法和变量的起点。随后可以根据需要对其进行重写和扩展，以提供额外功能。

借鉴生物学，继承是一个旨在简化复杂项目中代码重用的概念。它通过允许构建一个从另一个现有类派生（继承）现有功能和属性的类来实现这一点。一旦派生，您只需应用所需的自定义修改即可。派生类被称为“子类”或“子类别”，而原始类被称为“父类”或“超类”。

考虑为咖啡店编写 OOP 应用程序。该业务可能有一个忠诚度计划，需要在系统中存储客户详细信息。它还可能需要存储员工信息以便支付他们的工资。虽然客户和员工在程序中具有非常不同的功能，但也存在一些共同点，例如姓名和联系信息。继承允许程序员将这些共同点放入名为 Person 的父类中，而将专门功能放入 Customer 和 Employee 类中。Person 中包含的通用代码不需要重复；它会自动可用于任何从中派生的子类。

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_426_0.png)

在此场景中，Person 类将包含负责任何人的姓名、电话号码、电子邮件和地址的编程代码。Customer 类从 Person 继承这些基本属性和函数，然后通过添加会员号、客户累积的积分及其

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_427_0.png)

使用 UML 的继承

注册日期。Employee 类同样继承 Person 的基本属性和函数，并通过添加薪水和银行账户详细信息以及关于单个员工主管的信息来扩展它们。

使用 UML 绘制时，此继承关系通过从派生类指向父类的 "is-a" 箭头表示。

下面的代码块说明了如何在代码中创建这三个类。请特别注意：

- 在 Python 中：
  - 继承关系的调用通过在类定义中使用括号来实现，例如 class Customer (Person) 创建一个名为 Customer 的类，从 Person 继承
  - 必须仍然调用超类的构造函数；这必须是子类构造函数的第一行，通过 super().__init__() 实现
- 在 Java 中：
  - 继承关系的调用通过在类定义中使用 extends 关键字来实现，例如 class Customer extends Person 创建一个名为 Customer 的类，从 Person 继承
  - 必须仍然调用超类的构造函数；这必须是子类构造函数的第一行，通过 super() 实现
  - protected 访问修饰符将允许子类直接访问在超类中定义的实例变量。

```python
class Person:
    def __init__(self, name, phone, email, address):
        self.name = name
        self.phone = phone
        self.email = email
        self.address = address

    def __str__(self):
        return "Person: "+self.name

class Customer(Person): # The parenthesis indicates Customer inherits Person
    def __init__(self, name, phone, email, address, membership, points, signup):
        # Call the constructor of the parent class
        super().__init__(name, phone, email, address)
        # Define other instance variables specific to this child class
        self.membership = membership
        self.points = points
        self.signup = signup

    def __str__(self):
        return "Customer: "+self.name+" has "+str(self.points)+" points."
```
