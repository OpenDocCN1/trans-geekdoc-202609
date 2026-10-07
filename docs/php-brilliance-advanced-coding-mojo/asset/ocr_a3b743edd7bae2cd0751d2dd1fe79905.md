Expressing good traits.

you encounter this kludgey keyword in the middle of a use declaration, you need to go and look at the trait that contains the unsuccessful method. Are you satisfied that that method is entirely optimal to the trait's operation. This needs to be considered not just for the case at hand, but in all cases. If another team member favours a different method over this one, will lead to a bug?

Of course, we might be tempted to go down route of pseudo-namespacing our trait's methods to avoid the possibility of any collision as we've already seen, when encapsulation is called for, encapsulation should be used.

Finally, we've arrived at the last level in our precedence hierarchy. When a trait consuming class is itself derived from a parent class via the miracle of inheritance, any methods declared in the parent class will be overridden by any identically named methods in any trait that a child class consumes. This is actually logical when you remember that a trait is nothing behind an automated copy and paste mechanism. The end result is just the same as if you'd coded the overrides into the child class directly.

However, since the overriding methods aren't immediately visible to the developer (they’re "hidden" behind the use keyword), caution should certainly be exercised to ensure that a trait's methods don't accidentally override any methods declared by the parent, not least because it's the parent that presents that all important interface guarantee to the rest of our code. In other words, a trait can mess with your data type definitions and you wouldn't necessarily know about it until something goes wrong.

# The Yo-Yo problem... horizontalised

I haven't exactly painted a rosy picture in support of traits, have I? Yet they provide us with a very powerful means of achieving code reuse. We already know that our application’s should be DRY, not WET. We already know that the duplication of the same pieces of code throughout our application’s code base only ever leads to a maintenance nightmare in the future.

Even though I've taken us through quite a nightmareish landscape, our considerations of the problems that traits bring with them are not over yet, although I promise that this is the very last one!