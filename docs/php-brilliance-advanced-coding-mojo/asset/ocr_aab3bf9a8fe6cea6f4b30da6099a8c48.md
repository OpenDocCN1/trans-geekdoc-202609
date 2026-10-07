# Tell, Don't Ask

In other words, we’re leaving ourselves vulnerable to bug-like scenarios, which will certainly crop up should we modify the innards of the UserAccount class at some point in the future.

Consider the implications that would become apparent should the business team decide that we should be maintaining the user’s account balance as a penny value, rather than as pounds or dollars? Would you rather modify just a single object or alternatively, have to search the entire codebase for all of the locations where your code is extracting and working with the balance value itself?

The correct answer is of course that you would rather have to modify the innards of a single class. With in this mind, and before we get much further, let’s fix up our earlier code so that the two violation cases are dealt with appropriately. Doing so will allow us to compare the broken code with the corrected version.

Such a fix might look like this:

```
class OrderController {
    public function addOrderAction() {
        try {
            $userAccount->payOrder($order);
        } catch (InsufficientFundsException e) {
            // handle exception
        }
    }
}
```

What has happened here? Well, first of all, we’ve eliminated this piece of validation code from the addOrderAction() method. It never really belonged in the first place. Why not? For the simple reason that it’s not a controller’s job to have intimate knowledge of a model’s state, in this case, the actual balance value that this UserAccount instance is responsible for maintaining. Only the model object itself, the UserAccount instance, should know how it works internally.

The second case, that of actually modifying the instance’s balance value has also been removed from the controller.