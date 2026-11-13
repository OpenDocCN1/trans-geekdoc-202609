```
}
return null; // No matching account found;
}
public static void main(String[] args) {
    // Initialize an array with 3 accounts
    BankAccount[] accounts = new BankAccount[10];
    accounts[0] = new BankAccount("Amy");
    accounts[1] = new BankAccount("Brian");
    accounts[2] = new BankAccount("Clare");
    // Perform some transactions using array index
    accounts[0].deposit(500);
    accounts[1].deposit(500);
    accounts[2].deposit(500);
    accounts[0].transfer(150, accounts[2]);
    // Apply interest to all account balances
    for (int i=0; i<3; i++) {
        accounts[i].applyInterest();
    }
    // Perform transaction using a static function to search the array
    BankAccount amy = BankAccount.find(accounts, "Amy");
    if (amy != null) {
        amy.deposit(42);
    }
    // Print balances using the toString() function
    for (int i=0; i<3; i++) {
        System.out.println(accounts[i]);
    }
}
```

# # Students and grades

Here is another complete example, this time also showing the use of objects as instance variables within the other objects. In this case, each Student object contains an array of Grade objects. Study the example and identify the use of access modifiers, static and non-static variables.

![](bbox=[0.283, 0.67, 0.785, 0.835])

UML diagram of Student and Assessment Classes