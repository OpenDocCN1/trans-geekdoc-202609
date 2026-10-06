```
public function getTotalBalance() {
    return $this->_totalBalance;
}
```

```
$a = new Account();
$a->makeDeposit(500);
$a->makeWithWithdrawal(100);
echo $a->getTotalBalance() . "<br />/"; // Displays "400"
$a->makeWithWithdrawal(1000); // Displays "Insufficient funds"
```

Because the variable storing the account balance is private, it cannot be manipulated directly. Customers who have to actually make a deposit via makeDeposit() if they want to increase the value of their account.

By encapsulating internal data and method implementations, an object-oriented approach can protect and control access to its data and hide the details of implementation, making the application more flexible and maintain.

# # Object Overloading with __get(), __set(), and __call()

Normally, if you want to read or write an object's property, PHP dutifully reads or sets the property's value (assuming the property exists and your code has permission to access it). Similarly, if you call an object's method, PHP looks for the method within the object and, if it finds it, it runs.

However, PHP lets you use a technique known as overloading to intercept attempts to read or write an object's properties, or call its methods. This can be quite powerful. As far as the calling code is concerned, the object contains fixed, pre-programmed properties and methods. However, behind the scenes, your object can be doing all sorts of interesting things.

+   - The calling code sets the value of $myObject->property, which actually causes $myObject to retrieve the value from an array instead
- The calling code sets $myObject->anotherProperty to a new value, but behind the scenes $myObject actually writes this value to a database field
- The calling code calls $myObject->aMethod(). This method doesn't actually exist in $myObject, but $myObject intercepts the call and calls another method instead

Although you probably won't use object overloading that often, you can see that the technique can offer a lot of flexibility.