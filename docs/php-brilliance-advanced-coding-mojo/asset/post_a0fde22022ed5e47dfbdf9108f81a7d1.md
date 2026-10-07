
Proding the polymorph.

function did in the first example. There's still another key point to make on top of this though: As the consumer, the renderVehicle() method has no need to know the actual class name that the $vehicle parameter is an instance of. Only that it conforms to the interface that is specified by the more generic Vehicle definition as given by the abstract parent.

At this point, I'd like to draw your attention back to that simplistic interpretation of polymorphism that I gave at the beginning of this chapter. Even though we've switched our focus away from the provider and towards the consumer, the idea “Same name, different logic” remains consistent with this type of polymorphism too. The same name component refers to the fact that we're using the abstract parent's classname when we hint the input parameter for the renderVehicle() method. At the same time, we know that the different logic component is satisfied by the fact that the method can receive any one of the derived class within within this particular family of types.

As developers it should be quite plain to see that we use polymorphism regularly in our daily coding (or at least, I do) and therefore it should also be quite plain to see why I put so much effort into trying to get across this data type definition idea.

I'll say it again though. Of course I will. As long as we continue to correctly support the idea that the abstract parent provides us with the definition of a new data type and as long as we ensure that any class derived from the abstract parent continue to support the data type's definition then we can reasonably expect the collaborators that work with instances of this data type to operate without error irrespective of which concrete class instance they end up with working.

This is the very basis of generic programming as it applies to object oriented PHP.

This discussion wouldn't be complete though without an illustration of how we can break parametric polymorphism. It's exceptionally easy to do. I know this is the case because I've seen it far too many times in far too many projects. It goes like:

Proding the polymorph.

# class VehicleRenderer
{

```
public function renderVehicle($Vehicle $vehicle)
{
    switch(get_class($vehicle)) {
        case "Car":
            $this->renderCar($vehicle);
            break;
        case "Motorcycle":
            $this->renderMotorcycle($vehicle);
            break;
        case "JetSki":
            $this->renderJetSki($vehicle);
            break;
    }
}

// Individual render methods for different vehicle classes
...
```

How we break it is very simple. Instead of relying on the interface that is provided by the abstract parent vehicle class as we were previously, we're now building intimate knowledge of our concrete child class implementations into our consumer and as have broken the generic nature of it in the process. renderVehicle() method knows how to check the actual class of its input parameter before it can proceed to render the details contained within.

Whenever you see this kind of coding approach, you can be certain that the underlying data type of the consumed object has been broken through the inappropriate use of inheritance, which is a shame because a modification to a particular child class requires modifications to the consumers of the child class. In a largeish application, you can be confident that this is going to lead bugs; grepping code bases in order to find every line of code that needs changing usually does.

As you can see, subtype polymorphism and parametric polymorphism are really closely related, so long as they're done correctly. The improper use of abstraction and inheritance will break our beautifully polymorphic process, turning elegant programming into a mess of spaghetti code in virtually no time at all. But what if I told you that you could enjoy all of the benefits of polymorphic behaviour

without any of the drawbacks of using inheritance? Well you can and I’m going to talk about it next.

## Delegate Polymorphism

What if, instead of relying on the process of hard-wiring all of the different logical implementations of our data types into the various specialised child classes, we could dispense with the notions of abstraction and inheritance completely and still support switchable behaviours that better represent the things within our application actually do. Our times rather ropy and somewhat disparate interpretations of what abstraction and inheritance actually would suddenly cease to be the source of so many bugs.

The good news is that we can and whilst I’ve no doubt that such notion might start sending shivers up and down the collective spines of many a Senior Developer, once we’ve explored the possibilities I’m certain that at least some of you might start concoct ways in which Delegate Polymorphism might be implemented in your projects.

As the name suggests, the process relies on the implementation of a design pattern called Delegation, which in turn embodies the notion that the changeable aspects of what would otherwise become specialised child class are instead encapsulated into separate, independent objects to which method calls are instead delegated to in order to execute the particular favour of logic that the delegate encapsulates.

I’m really talking about there are injectable, encapsulated behaviours basically come in the form of helpers. Let’s look at some code.

```
abstract class MortgagePlan {
    private $loanValue;

    private $loanTerm;

    abstract public function getPaymentPlan();
}
```

So far, good. Clearly we’ve created a new data type here, one that’s called MortgagePlan. We have private properties representing the value of the loan and the duration of the loan expressed as the loan term.

```
class FixedMortgage extends MortgagePlan
{
    public function getPaymentPlan()
    {
        // Logic to calculate a mortgage repayment plan
        // based on a fixed interest rate
        ...
        return $mortgagePlan;
    }
}
```

```
class CappedMortgage extends MortgagePlan
{
    public function getPaymentPlan()
    {
        // Logic to calculate a mortgage repayment plan
        // based on variable interest rates
        // subject to a cap to prevent repayments
        // exceeding a certain value
        ...
        return $mortgagePlan;
    }
}
```

And here I've provided the usual suspects in terms of specialised child classes. In the first instance, we have FixedMortgage, which is capable of calculating the mortgage repayments that would fall when a fixed rate mortgage has been taken out. The second instance features the necessary logic in order to calculate a variable rate mortgage that nevertheless is subject to capping to prevent repayments exceeding a certain level.

I would fairly feel confident that each and every one of my readers has encountered this kind of code: child classes that implement specialised logic based on a set of circumstances the stabilisation is intended to represent. This is standard practice but it doesn't actually have to be this.

If we were to apply delegate polymorphism to the scheme above, we could actually do away with the abstraction and inheritance process. Even though this is clearly another simplistic example and real life projects are rarely this easy, it does rather make for a good illustration of the point.

Proding the polymorph.

It- doesn't take a great deal of refactoring to turn this unnecessary inheritance hierarchy into a simple mortgage class and a pair of injectable behaviours. Let’s see that in action.

```
class MortgagePlan
{
    private $loanValue;
    private $loanTerm;
    private $repaymentCalculator;

    public function setCalc(RepaymentCalc $calc)
    {
        $this->repaymentCalculator = $calc;
    }

    public function getCalc()
    {
        return $this->repaymentCalculator;
    }

    public function getPaymentPlan()
    {
        $calc = $this->getCalc();
        return $calc->getPaymentPlan($this->loanValue, $this->loanTerm);
    }
}
```
