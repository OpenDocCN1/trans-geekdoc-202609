The second consideration within this example is the clear and direct manipulation of an object's properties outside the object itself.

```
$newBalance = $userBalance - $orderTotal;
userAccount->setBalance($newBalance);
```

In this particular case, we are setting up a new variable called $newBalance as the result of subtracting $orderTotal from $userBalance, which we then proceed to pass back to the $userAccount object as the new balance value that it is meant to maintain.

It only takes a moment of careful consideration to realise that this is a terribly flawed approach to programming. In both cases, we're accessing a property value that really ought to remain private and personal to the owning object instance. In both cases, we're flying in the face of what we ought to be understanding the notion of encapsulation to.

The first case in our example is pretty bad but the second case is unforgivable.

Even so, this is such an extraordinarily frequent occurrence in PHP code that you might be tempted to imagine that it's actually the right way to do things. Take a moment to consider controller methods that you yourself have written in the past; how many times you have asked a model layer for data elements and then either massaged them into a structure for view file to use or even made some sort of logic decision on the values retrieved? I have certainly done this very thing hundreds of times in the past.

If we are meant to be telling objects to do things, instead of asking them for details and performing the operations ourselves, then we should longer see such violations in our controllers.

Why creating such violations be a bad thing? The answer to that lies with the fact that the code that we write into an enterprise application is rarely complete, finished and done. Those pesky little minions on the business team will most assuredly see to.

Consequently, whenever we expose the finer details of an object's state, as indeed we do twice in the example above, we are also tightly coupling our code to those same details of state.