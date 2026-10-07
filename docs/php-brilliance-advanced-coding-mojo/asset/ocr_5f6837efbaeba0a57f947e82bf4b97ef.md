Code, but in the abstract sense.

this matter will not require quite so many words as has gone before it. In essence, we have already covered a lot of the ground work already and it won't take so much to extend these ideas just a little further.

Thus far've been considering abstraction from the perspective of data and in doing so, we've explored how we might create potentially very structures which describe not only how the individual attributes might appropriately grouped together in a more logical whole but also how we expect that collected unit of data to behave and interact with the rest of our system.

If you consider the final example of the User class from the previous chapter, we have distilled the essential attributes and characteristics into a blueprint from which user objects may be created. You will recall that such user objects were seeded with a UserTransport instance that was injected via the constructor and, the public interface of the User class itself provides no hint of such nefarious activities. What we have done is to hide the complexities of our User class internal workings, abstracting them away behind our designated public interface.

Thus we have been discussing data abstraction.

With the abstraction of control, we turn our attention away from the objects that know things and instead, consider the lot of the objects that do.

The core principle is the same. We seek to mask the complexities of a given process by tucking them away behind an interface, which, whilst potentially quite complex in its right nevertheless relieves the operator of needing to know the finer implementation details of the entire process. Let's take a moment to consider how the case of a motorcar might help us understand this flavour of abstraction. Now I don't mean a car class. A real one. One that you drive to the grocery store and back again.

When you climb into the driver's seat, you are confronted with a potentially dazzling array of controls. A wheel, pedals, sometime, some mechanism to change gears, maybe a satnav, turn indicators, controls for the headlights. And so the list goes on. The car's purpose is not, despite what some of you might think, to provide a cosy little space in which you might make out with the hottie from the coffee shop. It's purpose is to go somewhere. You can achieve this by interacting with the interface that the car provides you with.

Therein lies the point. Whilst driving to the grocery store, have you ever said that