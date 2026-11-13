
```python
def transfer(self, amount, recipient):
    self.withdraw(amount)
    recipient.deposit(amount)

def __str__(self):
    return f"Account {self.name} has balance ${self.balance}"
```

### Java

```java
public class BankAccount {
    private String name; // Create an instance variable
    private double balance; // Create an instance variable
    public BankAccount(String name) {
        this.name = name; // Set instance 'name' to value of parameter 'name'
        this.balance = 0.0;
    }

    public void deposit(double amount) {
        balance = balance + amount;
    }

    public void withdraw(double amount) {
        balance = balance - amount;
    }

    public void transfer(double amount, BankAccount recipient) {
        this.withdraw(amount);
        recipient.deposit(amount);
    }

    public String toString() {
        return "Account " + this.name + " has balance $" + this.balance;
    }
}
```

## Creating an object

Creating an array is the process of declaring and instantiating an object variable based on the class type. It is at this point that you pass any parameters required by the constructor.

The following example creates an instance of an object using the identifier name acc, of the type BankAccount. You can treat acc just like any other variable from that point onward.

### Python

```python
# Python
acc = BankAccount("Neo")
print(acc)
```

### Java

```java
public class Main {
    public static void main(String[] args) {
        BankAccount acc = new BankAccount("Neo");
        System.out.println(acc);
    }
}
```

## Creating an array of objects

When initializing an array of objects, it is important to note that each individual object still requires its constructor function to be executed. This may require iterating over the entire array to explicitly execute the constructor on each element. Some examples based on the BankAccount scenario follow.

> **Top tip!**
>
> Because arrays contain multiple objects, their names should always be a plural of the object contained within. In this case, it could be bankAccounts (Java's camelCase) or bank_accounts (Python's snake_case).

```python
# Python - example 1
accounts = [
    BankAccount("Amy"),
    BankAccount("Brian"),
    BankAccount("Clare")
]

# Python - example 2
accounts = []
for i in range(0, 3):
    name = input("Name for new bank account: ")
    accounts.append( BankAccount( name ) )
```

```java
// Java - example using static array
BankAccount[] accounts = new BankAccount[3];
accounts[0] = new BankAccount("Amy");
accounts[1] = new BankAccount("Brian");
accounts[2] = new BankAccount("Clare");

// Java - example iterating over static array
String[] names = {"Amy", "Brian", "Clare"};
BankAccount[] accounts = new BankAccount[3];
for (int i=0; i<accounts.length; i++) {
    accounts[i] = new BankAccount( names[i] );
}

// Java - example using ArrayList
// Remember to import java.util.ArrayList
ArrayList<BankAccount> accounts = new ArrayList<BankAccount>();
accounts.add(new BankAccount("Amy"));
accounts.add(new BankAccount("Brian"));
accounts.add(new BankAccount("Clare"));
```

## B3.1.5 Encapsulation and information hiding in OOP

- Encapsulation: bundles data and the methods that manipulate that data together into a single object. It serves to hide the implementation details of the object from outside code.
- Access modifiers: the mechanisms provided by the programming language to control visibility of methods and variables within an object.

Encapsulation is the idea that programming code outside of the class should not have direct access to the data within the class. You can visualize the data as being protected by a capsule wrapped around it! The only way to permeate the capsule is through the methods the class allows.

By controlling access, encapsulation ensures that variables are only used in the manner in which they were intended, helping protect your code from invalid, error-inducing values. It also means that you can write code that uses encapsulated classes without needing to know or care how the class manages its internal state.

Successful encapsulation of your classes is fundamental to facilitating modularity in object-oriented programming.

### Linking question

How can the principles of encapsulation and information hiding (B2.5) be applied to secure network communication? (A3)

### Access modifiers

Encapsulation is achieved through using access modifiers. The structure of access modifiers is different between Java and Python.

In Java, the access modifier is specified by supplying the relevant keyword in front of the variable or method definition. There are four access modifiers to know:

- Private: Indicates it should only be accessible by the current object.
- Protected: Indicates that it may be accessed by the current object, and any objects that inherit it (more on that in B3.2.1).
- Public: Indicates it may be accessible to any code within your program.
- Default: When no modifier is provided, it allows access for any object within the same Java package (as denoted by the package statement at the top of your Java file); Python does not have an equivalent of this.

In Python, access modifiers work slightly differently. They are specified through a naming convention for your variables and methods. They can be bypassed. In this sense, they are more guidelines than rules. That said, for the purposes of your course, you should avoid bypassing them.

- Public: The default behaviour is that variables and methods are treated as public.
- Internal use: The single underscore prefix (e.g. _variable) is used to indicate it is only for internal use within the class. While this is purely a convention, and the Python interpreter does not enforce it, most Python editors strongly hint at not using these variables by hiding them or making them less visible.
- Name mangled: The double underscore prefix (e.g. __variable) is used to instruct the Python interpreter to rename the variable or method at runtime. The name is mangled to include the class name, which makes it harder (but not impossible) to access from outside the class. For example, __variable in a class named MyClass would be mangled to _MyClass__variable.

This might seem like it makes a variable private, but Python doesn’t have truly private variables. Name mangling was created to avoid naming conflicts, rather than to enforce strict access control. The mangled name can still be accessed from outside the class; it just requires knowledge of the name-mangling pattern Python uses.

For the purposes of your course, you can treat either the single or double underscore prefix as denoting private, but ensure you are aware of the technical subtleties involved.

### Accessors and mutators

By setting your variables to private, the inevitable consequence is you will need to create a number of public methods through which code outside your class can interact with those variables, query their value or request they be updated.

- **Accessor**: a public method that allows external code to “access” the value of a private instance variable within an object; also known as “getter method” as it “gets” the value.
- **Mutator**: a public method that allows external code to update or mutate the value of a private instance variable within an object; also known as “setter method” as it “sets” the value.

Methods that perform these tasks are formally known as **accessors** and **mutators**. They are also often referred to as getters and setters.

For instance, if a Person class has variables for name and age, then there may be accessor methods `getName()` and `getAge()`, as well as mutator methods `setName()` and `setAge()`.

Crucially, the example above serves to reinforce the important role that encapsulation can play in protecting your data. You may not want it to be so easy to update a person’s name in your application, and the person’s age may be calculated behind the scenes using the current date and a stored date of birth, rather than just being stored as an integer that will soon drift to being out of date.

Requiring accessor and mutator methods, rather than giving external code free access to your variables, allows separation of responsibilities and keeps the class in control of what happens to its data.

> **Top tip!**
>
> For beginner programmers, the following is recommended good practice:
>
> - Set variables to **private** where possible. Create accessor and mutator methods for any attribute you want external code to have access to.
> - Methods (or functions) should be **public** if you want external code to have access to them. If the method is an internal helper function, set it to **private**.
>
> Study the updated code for the Bank Account scenario in Section B3.1 to see inclusion of access modifiers.

> **ACTIVITY**
>
> **Research skills and thinking skills: Code analysis**
>
> Operation sabotage! Take a piece of OOP programming code and insert some deliberate errors into it that break the principle of encapsulation. Swap with a classmate, and refactor the code you are given to ensure proper use of encapsulation again. Discuss and compare changes with your classmate afterwards. Did you both spot all the errors and apply appropriate corrections?

- **Static**: methods and variables that belong to the class, not the individual objects. Only one copy is created that is shared with all instances in common.

## B3.1.3 Static and non-static variables and methods

The term static is used to represent variables and methods that are associated with the class itself rather than any individual object instances.
