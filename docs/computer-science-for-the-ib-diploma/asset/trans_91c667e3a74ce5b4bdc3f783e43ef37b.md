
静态变量和方法不需要创建实例即可存在。它们由解释器 / 编译器在定义类时于运行时创建。这就是为什么 Java 中的 main 函数定义为静态，因为它需要在代码本身创建任何对象之前存在并被执行。

由于静态成员不依赖于对象已被实例化，这意味着静态方法不能访问对象中的实例变量。这也意味着，每当已实例化的对象使用静态变量或方法时，所有对象访问的是同一个共享变量或方法，而不是各自的实例。因此，如果某个对象更改了静态变量的值，该更改对所有其他对象都可见。你可以将静态变量视为与该类所有对象共享的全局变量。当某物需要在类内的所有对象之间共享，或者特定变量不依赖于实例存在时，静态变量非常有用。

因此，“非静态”一词指的是你迄今为止在对象中定义的普通实例变量。每个对象都会为这些变量创建自己的唯一实例，因此当一个对象使用它们时，不会影响另一个对象中对应变量所存储的值。

在代码中引用静态变量和方法时，最佳做是用类名作为前缀，例如 ClassName.variableName（请参阅下方 BankAccount 中的示例）。

## 使用静态变量跟踪 ID 值

使用静态变量的常见场景之一是确保类的每个对象都有一个唯一的 ID 号。示例可能是超市应用程序的产品编号。

```
class Product:
    next_product_id = 0 # define a static variable
    def __init__(self, name):
        self.name = name
        self.product_id = Product.next_product_id
        Product.next_product_id += 1
    def __str__(self):
        return "Product "+str(self.product_id)+": "+self.name
if __name__ == "__main__":
    products = [
        Product("Bread"),
        Product("Milk"),
        Product("Apples"),
        Product("Icecream")
    ]
for i in range(0, len(products)):
    print(products[i])
```

## Java

```
class Product {
  private static int nextProductID = 0; // define a static
  // variable
  private String name;
  private int productID;
  Product(String name) {
    this.name = name;
    this.productID = Product.nextProductID;
    Product.nextProductID++;
  }
  public String toString() {
    return "Product " +Integer.toString(this.productID)+": "+this.name;
  }
}
class Main {
  public static void main(String[] args) {
    Product[] products = new Product[4];
    products[0] = new Product("Bread");
    products[1] = new Product("Milk");
    products[2] = new Product("Apples");
    products[3] = new Product("Icecream");
    for (int i=0; i<products.length; i++) {
      System.out.println( products[i] );
    }
  }
}
```

## 使用静态变量跟踪数组中的项目数量（仅限 Java）

在 Java 中，静态变量的另一种常见用途是跟踪数组中填充的项目数量。由于数组大小固定，可以使用静态变量来确保将下一项放置在下一个空位置。在 Python 中这不太是问题，因为静态数组并不真正存在，而列表结构的大小是动态的。

此问题的替代方案包括：

- 在循环中使用 if 语句测试 null
- 使用 ArrayList，因为它大小可动态调整。

下面是一个示例：

```
Java
class Thing {
    private String name;
    Thing(String name) {
        this.name = name;
    }
    public String toString() {
        return this.name;
    }
}

class CollectionOfThings {
    private static int nextThing = 0; // static variable
    private Thing[] things;
    CollectionOfThings() {
        things = new Thing[100]; // Create an array of 100
        // null Things
        CollectionOfThings.nextThing = 0;
    }

    public void add(Thing t) {
        things[CollectionOfThings.nextThing] = t;
        CollectionOfThings.nextThing++;
    }

    public void remove(Thing t) {
        boolean found = false;
        for (int i=0; i<CollectionOfThings.nextThing-1; i++) {
            if (things[i].equals(t)) {
                found = true;
            }
        }
        if (found) {
            things[i] = things[i+1];
            CollectionOfThings.nextThing--;
        }
    }

    public void printAll() {
        for (int i=0; i<CollectionOfThings.nextThing; i++) {
            System.out.println(things[i]);
        }
    }
}
```

> **小贴士！**
>
> 请记住，static 表示类的一个共享项，而不是单个实例。仅对所有对象共有的事物（如公司名称）使用 static，而对特定于实例的属性（如员工编号）使用普通的非静态成员。尝试编写代码片段，观察将成员从静态更改为非静态（反之亦然）的效果。

> **关联问题**
>
> OOP（B1）可以以何种方式应用于数据库（A3）开发？

## B3.1 节末示例

### 活动

社交技能：结对编程

结对编程是一种基于研究的方法，旨在帮助初学者程序员建立信心。以两人一组的方式设计和实现编程项目，一名学生编写代码，另一名学生审查代码并提出改进建议，并定期切换角色。可以把它类比为在计算机键盘前既有驾驶员又有领航员。

## 银行账户

请参见下方银行账户场景的完整代码，该代码已更新以展示数组初始化、访问修饰符的使用以及静态与非静态变量和方法。

请注意，已实现两个静态变量和一个静态方法：

- interest_rate：由于所有银行账户的利率相同，将其设为静态很合理。这样只需更新一次，所有银行账户都会自动应用更改。
- next_account_number：通过每次创建对象时检查并递增此值，可以确保没有两个银行账户拥有相同的账户号码。
- find()：提供搜索 BankAccounts 数组以查找请求名称（通过参数提供）的功能。

```
class BankAccount:
    interest_rate = 5.00 # Static variable
    next_account_number = 1001 # Static variable
    def __init__(self, name):
        self._name = name
        self._balance = 0
        # Use the class name as a prefix to access the static variables
        self._account_number = BankAccount.next_account_number
        BankAccount.next_account_number += 1
    def deposit(self, amount):
        self._balance += amount
    def withdraw(self, amount):
        if self._balance < amount:
            return False
        self._balance -= amount
        return True
    def transfer(self, amount, recipient):
        if self.withdraw(amount):
            recipient.deposit(amount)
            return True
        else:
            return False
```

```
def apply_interest(self):
    self._balance += self._balance * (BankAccount.interest_rate / 100)
def get_balance(self):
    return self._balance
def get_name(self):
    return self._name
def __str__(self):
    return f"Account {self._account_number}: {self._name} has balance ${self._balance}."
@staticmethod
def find(accounts, name):
    for acc in accounts:
        if acc.get_name() == name:
            return acc
    return None # No matching account found
# Example usage:
if __name__ == "__main__":
    # Initialize a list with 3 accounts
    accounts = [BankAccount("Amy"), BankAccount("Brian"), BankAccount("Clare")]
    # Perform some transactions
    accounts[0].deposit(500)
    accounts[1].deposit(500)
    accounts[2].deposit(500)
    accounts[0].transfer(150, accounts[2])
    # Apply interest to all account balances
    for acc in accounts:
        acc.apply_interest()
    # Perform transaction using a static method to search the list
    amy = BankAccount.find(accounts, "Amy")
    if amy:
        amy.deposit(42)
    # Print balances using the __str__ method
    for acc in accounts:
        print(acc)
```

```
Java
public class BankAccount {
    private static double interestRate = 5.00; // static variable
    private static int nextAccountNumber = 1001; // static variable
    private String name;
    private double balance;
    private int accountNumber;
```
