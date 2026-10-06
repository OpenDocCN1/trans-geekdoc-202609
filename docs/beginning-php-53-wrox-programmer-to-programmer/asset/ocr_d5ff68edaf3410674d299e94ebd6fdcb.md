# Part II: Learning the Language

By the way, you can also use type hinting with regular functions, not just methods, and you can check that an argument is an array using:

```
function showAll( array $items ) (
```

Sadly, PHP supports type hinting only for objects and arrays. Other data types, such as strings or integers, can be checked using this technique. If you want to check for these types you'll need to use is_string(), is_int(), and so on as described in Chapter 3.

# Making Your Classes Self-Contained with Encapsulation

So far, most of the classes you've created in this chapter have public properties, and outside code has been able to reach a class's innards and manipulate its public properties. Usually, this is a bad idea. One of the strengths of OOP is encapsulation. This means that a class's internal data should be protected from being directly manipulated from outside, and the details of a class implementation — such as it stores values or manipulates data — should be hidden from the outside world. By doing this, you gain two advantages:

+   - You can change your class's implementation details at any time without affecting code that uses the class
- You can trust the state of an object to be valid and make sense

Generally, all internal properties of a class should be declared private. If outside code needs to access those variables, it should be done through a public method. This gives you the opportunity to validate the requests requested by the code and accept or reject them.

For example, if you're building a banking application that handles details of customer accounts, you might have an Account object with a property $totalBalance and methods called makeDeposit() and makeWithdrawal(). The only way to affect the balance should be to make a withdrawal or deposit. If the $totalBalance is implemented as a public property, you could write outside code that would increase the value of variable without having to make a deposit. Obviously, this would be bad for the bank.

Instead, we implement this as a private property and provide a public method getBalance(), which returns the value of that property:

```
class Account {
    private $_totalBalance = 0;

    public function makeDeposit($ $amount ) {
        $this->$_totalBalance += $amount;
    }

    public function makeWithdrawal($ $amount ) {
        if ($amount < $this->$_totalBalance ) {
            $this->$_totalBalance -= $amount;
        } else {
            die("Insufficient funds<br />");
        }
    }
}
```

182