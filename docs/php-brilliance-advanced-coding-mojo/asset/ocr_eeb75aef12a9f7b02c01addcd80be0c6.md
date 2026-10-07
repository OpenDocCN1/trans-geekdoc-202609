Much has been written about when an object may be considered newborn and indeed, the arguments presented do hold true for software intended to run on the desktop in an offline world.

Some developers may very well argue that it's perfectly possible to create a large and complex, yet robust and secure application that still invokes new on the same classes hundreds of times throughout the code base. Such an application may be heralded as the singular proof that our new found fear is indeed irrational.

# But

Such an approach carries with it enormous risks. Even if the codebase right now is secure and stable, any future changes to the constructor methods of any of the classes would entail a significant amount of work to implement all of the necessary changes.

Do bear in mind that our world isn't the desktop oriented offline one. Our software isn't delivered as a finished product on an installable CD or DVD ROM.

Instead we work on delivering tagged releases through an iterative cycle that follows lean or agile methodologies, coding up individual stories to be added to the product with the next release and always with the business team leaning over our shoulders scratching out the next change request.

How much better would it be if, for every class declaration within your application code, there was only ever one, singular and unique location where the new keyword was used for each class in question?

Incidentally, I never meant to imply that we should always avoid the use of new. It is simply impossible to create object oriented code without it. I just wanted to make that bit clear at the very least.

Let me just go over that again. For each and every class that we declare in our application's codebase, we should have one and only one location where the new keyword is used on that class.

So, if we create a User class in our application, we need to have only one location where the corresponding new User() code is written. The benefits from adopting this as an in-house rule are numerous even though it's almost certainly going to be