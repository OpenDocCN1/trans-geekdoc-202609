
Static variables and methods don’t require an instance to be created for them to exist. They are created by the interpreter / compiler at runtime when the class is defined. This is why the main function in Java is defined as static, as it needs to exist and be executed before any objects have been created by the code itself.

Because statics do not depend on an object having been instantiated, it does mean that no static method may access instance variables within an object. It also means that any time an instantiated object makes use of a static variable or method, the objects are all accessing the same shared variable or method instead of their own instance of it. Consequently, should an object change the value of a static variable, that change will be visible to all other objects. You can think of a static variable as a global variable that is shared in common with all the objects of that class. Static variables come in useful when something needs to be shared across all objects within a class, or when the particular variable does not depend on an instance existing.

The term “non-static”, therefore, refers to the normal instance variables you have been defining within objects up until this point. Each object creates its own unique instance of these variables so, when used by one object, it does not affect the value stored in the matching variable of another object.

When referring to static variables and methods in code, it is best practice to prefix it with the class name, for example ClassName.variableName (see the examples in BankAccount below).

## Using a static variable to track ID values

One common scenario for using a static variable is to ensure each object of a class has a unique ID number. An example might be product numbers for a supermarket application.

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

## Using a static variable to track number of items in array (Java only)

In Java, another common usage of static variables is to keep track of the number of items populated within an array. Given arrays are fixed in size, the static variable can be used to ensure you place the next item at the next empty location. This is less of an issue in Python since static arrays are not really a thing, and the list construct is dynamic in size.

Alternative approaches to this would be:

- having an if statement testing for null inside a loop
- using an ArrayList, since it is dynamically resizable.

Here is an example:

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

> **Top tip!**
>
> Remember that static means one shared item for the class, not individual instances. Only use static for things that are common to all objects (like a company name), and use normal, non-static for properties specific to an instance (like an employee number). Experiment with writing code snippets to see the effect of changing members from static to non-static, and vice versa.

> **Linking question**
>
> In what ways can OOP (B1) be applied to database (A3) development?

## B3.1 End-of-section examples

### ACTIVITY

Social skills: Paired programming

Paired programming is a research-based approach to help develop confidence in beginner programmers. Work in pairs to design and implement your programming projects, with one student writing the code while the other reviews it and suggests improvements, switching roles periodically. Consider the analogy of having both a driver and a navigator at the computer keyboard.

## Bank accounts

See below for the full code for the Bank Accounts scenario, updated to illustrate initialization of an array, use of access modifiers and static with non-static variables and methods.

Notice two static variables and one static method have been implemented:

- interest_rate: As all bank accounts will have the same interest rate, it makes sense for this to be static. That way, it only needs updating once, and all bank accounts will automatically apply the change.
- next_account_number: By checking and incrementing this value every time an object is created, it can ensure that no two bank accounts have the same account number.
- find(): Provides functionality to search an array of BankAccounts to find one of the requested name (supplied through the parameters).

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
