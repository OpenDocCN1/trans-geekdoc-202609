# Tell, Don't Ask

would create the more specialised child classes such as Administrator, Member and Editor classes. Each of these child classes would have their own implementations of the getWelcomeMessage() method coded up accordingly.

This might be fine if our requirements for how our user roles are to be implemented are exceedingly simplistic.

The reality, of course, is that there is no such thing as “simplistic” when it comes to dealing with the business team.

Which leads us to second, and more likely, approach to coding user roles. We create an inheritance hierarchy of role classes, with a BaseRole as the abstract parent and more specialised child classes as EditorRole, PublisherRole and AdministratorRole. These role instances are then created and injected into our User instances whenever the User instances are themselves instantiated.

The result? In this case, the process of displaying a welcome message doesn't utilise a single if() statement in order to display the desired message. The User instances are appropriately equipped with role instances that allow them to respond to the getWelcomeMessage() method call correctly and without any decision making to get in the way.

Let's get ourselves back on track. If the key element Alec Sharp's quotation is “Object oriented tells to do things” then what are we really doing if not creating object methods that read, write and manipulate an object's state?

Does this sound familiar? It certainly should given that we have devoted a lot of time to examining encapsulation. Yes, this is one of circular references that I mentioned previously. The Tell, Don't Ask principle has a direct correlation with what we know about encapsulation and how it is “the bundling of properties and the methods that act upon properties into a single logical unit.”

It is also precisely the reason why Lizzie is currently hopping from one foot to the other whilst pointing at her screen enthusiastically. The reason for such suddenly frantic and slightly out-of-character behaviour? Certain luminaries of the programming world found on this particular principle, considering it to be superfluous and unnecessary in many cases, Martin Fowler is one luminary who argues some very valid points concerning this principle in his bliki post¹.

> ¹³http://martinfowler.com/bliki/TellDontAsk.html