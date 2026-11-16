Now create a file called class.SweepstakesCustomer.php and enter this code:

```
<?php
require_once('class.Customer.php');

class SweepstakesCustomer extends Customer {
    public function __construct($customerID) {
        parent::__construct($customerID);

        if($this->customerNumber == 1000000) {
            print "Congratulations $this->name! You're our " .
            "millionth customer!" .
            "You win a year's supply of frozen fish sticks!";
        }
    }
}
?>
```

# # How Inheritance Works

The Customer class initializes values from the database based on the customer ID. You would most likely retrieve the customer ID from a loyalty program swipe card such as the type available at most larger grocery store chains. With the customer ID, you can fetch the customer's personal data from the database (just hard-coded in this example), along with an integer value representing how many customers have entered the store before that customer. Store all this information in public member variables.

The SweepstakesCustomer class adds a bit of extra functionality to the constructor. You first invoke the parent class's constructor functionality by calling parent::__construct and passing to it the parameters it expects. You then look at the customerNumber property. If this number is the millionth, you inform this customer that he or she has won a prize.

To see how to use this class, create a file called testCustomer.php and enter the following code:

```
<?php
require_once('class.SweepstakesCustomer.php');
//since this file already includes class.Customer.php, there's
//no need to pull that file in, as well.

function greetCustomer(Customer $objCust) {
    print "Welcome back to the store $objCust->name!";
}

//Change this value to change the class used to create this customer object
$promotionCurrentlyRunning = true;
if ($promotionCurrentlyRunning) {
```