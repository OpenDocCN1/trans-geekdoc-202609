And favour Composition too.

to a particularly desired method, or via creating a parent class to share that method. Or indeed through creating great, wobbly towers of “re-use through inheritance” and using method overrides to blank out the ones that we don’t.

The core issue here arises through the hard-coded dependencies that we naturally create via the extends keyword. As developers, we learn that hard coded dependencies between one class and another are a bad thing. They cause tight coupling to occur, which in turn leads to brittle code taking up residence within our applications. Not good.

In the majority of cases, that or is.

The tight coupling that occurs between a parent class and any child classes that have been derived from it is of course a natural outcome of inheritance anyway. As long as we treat abstraction and inheritance in the correct manner, this will never be a problem for us.

How so?

In recognition of the fact that it’s the abstract parent that provides the data type definition that we are looking for to be present in all of the child instances. If we proceed to modify the behaviour of the parent, that those behavioural changes should subsequently and correspondingly become evident in all of the child classes is a desirable outcome.

Unfortunately, we cannot say the same for an inheritance hierarchy based on code use. When the hierarchy has been constructed for the benefit of common access to useful methods, changes to those shared methods have to be assessed in terms of the corresponding effects on all of the subclasses.

If there was a single most significant cause for the devastating loss of highly valuable pub time, it’s the inheritance hierarchy built for code-use.

Thankfully, we know better than do that. When those popular MVC-like frameworks wish to sully the minds of our colleagues with their wishes to have them extend a base model class loaded with convenience methods, we can take measures to protect our application code from the perils they represent.

Think about this for a moment - if, in the process of building our application, we ended up creating a hundred different model classes that are all based on a framework’s convenience-oriented base model the final outcome is that we have a