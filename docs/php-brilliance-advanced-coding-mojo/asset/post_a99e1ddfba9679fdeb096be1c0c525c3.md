
Providing the polymorph.

```php
interface RepaymentCalc
{
    public function getPaymentPlan($loanValue, $loanTerm);
}

class FixedMortgageCalc implements RepaymentCalc
{
    public function getPaymentPlan($loanValue, $loanTerm)
    {
        // Logic to calculate a mortgage repayment
        // based on a fixed interest rate
        //
        return $paymentPlan;
    }
}
```

```php
class CappedMortgageCalc implements RepaymentCalc
{
    public function getPaymentPlan($loanValue, $loanTerm)
    {
        // Logic to calculate a mortgage repayment
        // based on variable interest rates but subject
        // to a cap to prevent repayments exceeding
        // a certain value
        //
        return $paymentPlan;
    }
}
```

As you can see here, I've provided an interface in order to ensure that when we inject a calculator into MortgagePlan, the calculator will provide the getPlan() method. Implementing the interface means that PHP will emit a fatal error if this isn't the case.

And lastly, those two specialised classes in the first example have now been modified so that instead of extending MortgagePlan, they now implement RepaymentCalc. Each calculator is now an injectable behaviour, allowing us to change the way the consuming object behaves at runtime. This is an important distinction and it means MortgagePlan instances live independently of the calculators that encapsulate the different repayment logic.

More to the point, it also means that we can change the way MortgagePlan yields repayment on the fly. Should we feel like switching to fixed rate then we simply inject an instance of FixedMortgageCalc into MortgagePlan and the repayment behaviour is automatically changed for us.

To take this example back in line with the original theory of supporting the “Same, different logic” idea the MortgagePlan instance will still be invoking getPlan() method this is the “Same” part. Now however MortgagePlan instance delegates the responsibility for providing repayment to whichever calculator has been injected into it this is the “different logic” part.

There is an additional benefit to using this approach too. If in the future we find ourselves in need of a new type of repayment calculator it will be significantly easier to implement. After all we have the required interface defined for us, we'll just need to code up new repayment calculator to encapsulate the new logic and we're good to go.

However, our analysis of delegate polymorphism wouldn’t be complete without turning our attention to the potential downsides of this approach. Despite what I've just illustrated above it's not all sunshine and roses in delegate polymorphism.

The principal criticism of employing this technique is that it leads to significant duplication of method declarations. Don't get all up just! I'm not implying that we are about to duplicate the actual logic merely the method names. What we must do is create proxy methods in our principal class to act as intermediaries between the client code and the real target.

We can see this in the code above. If our principal class is MortgagePlan we can see how it provides the getPlan() method on its public interface. This getPlan() method performs no real logic of its own. Instead it proxies the request to the instance of RepaymentCalc that it has consumed.

For a very simple example as this doesn't really pose too much of a problem that we are declaring getPlan() in the principal class and then declaring another getPlan() in each of the different calculator classes. But even that way consider what will happen if during the evolution of our application we find ourselves having to extend the interface of the consumed delegate? What effect will that have on the number of proxy methods that we need to incorporate into the consuming object?

The potential for our consuming object's interface to become cluttered with proxy methods is quite large. It's something that we need to be prepared for and it may involve us having to ask questions as to whether these proxy methods contribute to our vision of what the principal class's interface is supposed to be.

Consider for a moment our favourite model class User that we've already looked at. It could be said that we delegated the password handling responsibilities to a dedicated instance of the PasswordManager. By consuming the PasswordManager what methods of the delegate need to be proxied by the User? By scaling our thinking what happens to our User interface when we consume an AddressManager delegate and then for the consumer side we add an Orders delegate? It shouldn't be too difficult to imagine that our User interface can become quite extensive even before we start adding dedicated user-specific methods of our own.

In all things then it becomes a matter of consideration and experience although I hope this book will allow you to take some effective shortcuts in the latter regard. If you can foresee a time when you would end up with a significant number of proxy methods you might very well be served by switching the procedures on their respective heads. Rather than proxying method calls to a consumed AddressManager why not build out an address management module and have the User instance become a parameter to be passed instead?

# Summary

I appreciate that it may very well seem like I've tried to talk you out of using abstraction as a means of defining a new data type doing so much effort into convincing you of the benefits of doing just that. This is not meant to be the case at all. As with many things in life you need to base your decisions based on what you best judge the situation to be. How you come to make those judgements will naturally be influenced by the extent of the things that you know about the topic in hand.

In this case you now know that using abstract classes as a means of defining new data types in your language is a very powerful technique for building applications. You also know that using interfaces as a means of defining a contract is another equally powerful technique. And finally you've seen how delegate polymorphism can be used to create flexible and maintainable code, though as I've illustrated it's not without its downsides. All of these techniques are powerful tools in your arsenal, and you now know how to use them effectively.
