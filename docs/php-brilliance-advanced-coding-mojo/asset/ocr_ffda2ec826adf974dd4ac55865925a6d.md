And favour Composition too.

hundred model objects whose behaviour can change (read "break") by the underlying base class changes.

This isn't such a far-fetched scenario. In the event that the framework's base model class drops the save() method and adds an insertOrUpdate() method, we have a hundred broken model classes because of the dependency that exists between our models and the framework's abstract base.

Now consider the effect of a strategy that would have injecting "save-ability" into our model classes instead of building model classes on top of the "save-ability" present in an abstract base.

If we were to wrap the framework's base model with our own adapter class and then arrange to have injected into new model instances, we protect our model layer against such devastating interface changes in that abstract base class.

That's not to say that our one hundred classes won't also be broken by such a change in the framework's base model of course. The fix, however, will be a one-liner in our custom adapter. The alternative? Comb through our entire codebase for calls of the save() method to see whether they need to be changed or not.

Obviously, the framework that made such a monstrous change would be the framework that became exceedingly unpopular with its users and as such, is highly improbable in the real world.

That being said, this scenario serves to make the point that we need at this stage. Inheritance, regardless of whether it's employed in order to achieve code reuse or not, introduces fragility into our object designs quite simply because those dependencies on parent classes are completely unavoidable. A change to the parent class automatically means the effects of that change will ripple through the entire hierarchy to greater or lesser degrees.

Code reuse through inheritance is completely avoidable though. Don't do it, ok? Just. Don't.

That's why we are here. Now at this point. To consider the fact that Composition is here to save the day. Not only can we immediately dismiss any kind of inheritance-related fragility, we gain the ability to employ switchable behaviours at runtime. This is something that we'll naturally explore when we get onto considering the design patterns that promote this idea of favouring composition and what it means for our application code.