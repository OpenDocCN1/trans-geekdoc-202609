> We'll get some of the whys and wherefores in the next chapter, But Don’t Talk To Strangers

It is of course somewhat ironic that a dependency injection container might itself be considered a dependency but the actual truth of the matter is that it quite often is. At the end of the day, the reason for both why this chapter exists and why it immediately follows on from the chapter on Instantiaphobia.

Often a developer's first inclination when they encounter this fancily named super factory is to consider the dependency injection container to be the one and only, singular and unique source of all prepared objects within the application.

As such, we'll start seeing couriers cropping up as the container needs to be transported from one layer to the next, and on to the next. And on the next.

Addressing this particular scenario is shockingly simple; look at the process in reverse and work backwards.

As Lizzie might be keen to point out, it used to be the sort of developer that would think of the process in terms of a request coming in, getting processed and resulting in a response going out. That is of course how it is likely to happen within our application code.

That’s also how a lot of beginners will address the matter of coding up a particular feature.

But that’s not necessarily how we should think it before building it.

In a multi-tiered application, this may involve devising a model factory that has a dependency on the persistence layer, with the model factory in turn being set on service instances by a service broker, which in turn might be set on controller instances.

In other words, there’s no rule that we cannot create multiple dependency injection contains and have them as the bridge between each layer. The controllers, services, models and persist-able data objects can all be furnished by their own dedicated containers; discrete units with a laser sharp focus of operation.

And with nary courier to be seen.