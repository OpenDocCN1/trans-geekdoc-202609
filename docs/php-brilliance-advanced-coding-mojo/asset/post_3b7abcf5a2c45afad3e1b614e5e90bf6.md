
The reverse is just as true. Failing to acknowledge this particular principle will lead to a codebase that exacts a terrible price on that most valuable of commodities: high quality pub time.

In an agile world, with over-eager business teams possessing a seemingly endless supply of spanners that they can throw into the works, we are not always able to know in advance what the final version of a particular class should look like before we've built it. Heck, in an agile world, we rarely arrive at a finished object. Instead, we have to satisfy ourselves with interstitial moments of operational software. These moments on the development timeline are commonly known as “releases” and get tagged as such.

Of course, modifying the constructor of a particular class inside application code that is already in production is a major sign of poor initial design. Fortunately, if you take on board all of the ideas that we discuss in this book, poor design days should be well and truly behind you.

This is why this chapter exists in the first place - it's about avoiding future headaches by adopting a quite specific coding technique today. At some point in the future, your teammates are quite possibly going to think of you as being psychic if you take this approach on right now.

But what is this approach?

Let's start with a snippet of code:

```
$user = new User();
```

Our beloved user class returns again! Once we've finished celebrating this fact, we should ask ourselves “Where is this code?". In a naively designed system, or more likely, that simply grows organically, it'll be everywhere an instance of a User object is required.

Quite literally, everywhere a $user instance is required, it'll be instantiated. One project that I worked on previously had the $user instance for the currently logged-in user instantiated at the start of every request, irrespective of whether that instance would be used to service that request or not. For a largish application with significant number of features, this means that this particular line (with or without constructor parameters) may be found in hundreds of different locations.

If we were to go through encapsulation chapter again, but inside an application that invoked a new User() more than a hundred times, would that not represent an awful lot of leg work in order to update every occurrence? IDEs, terminals and command line clients all provide a global search function, in which theory will allow you to locate and modify every occurrence in order to accommodate the changed modified method signature of the constructor.

That is, as long none of your colleagues has implemented code that creates objects using a variable that holds a class name. What do I mean by that? Well, let me show you another snippet of code, one that illustrates dynamic class name resolution:

```php
public function getObject($className)
{
    return $className;
}
```

No matter how efficient the global search in your editor of choice is, it will not be able to find every code location where a new User is instantiated if there’s even a single line of code that calls this method with ‘User’ set as the value of $className.

Using the new keyword in multiple locations for the same class simply sets up you a world of pow. It’s as simple as that.

As easy as it is to type $user = new User() in the piece of code that you’re working currently, I can save with a level of confidence bordering on the level of smug git that you’ll rue the decision at a later point.

This where Instantiaphobia comes in. Ok, I confess - this is a completely made up word but it’s one I think captures the essence of this particular lesson, as it were. What I’m hoping to arrive at here is the development of an irrational fear of creating new instances.

I calling it a phobia serves us very well. If a phobia is an irrational fear, developing a fear for using the new keyword that can’t easily (initially) explained should serve us well in the future.

Much has been written about when an object may be considered newborn and indeed, the arguments presented do hold true for software intended to run on the desktop in an offline world.

Some developers may very well argue that it's perfectly possible to create a large and complex, yet robust and secure application that still invokes new on the same classes hundreds of times throughout the code base. Such an application may be heralded as the singular proof that our new found fear is indeed irrational.

# But

Such an approach carries with it enormous risks. Even if the codebase right now is secure and stable, any future changes to the constructor methods of any of the classes would entail a significant amount of work to implement all of the necessary changes.

Do bear in mind that our world isn't the desktop oriented offline one. Our software isn't delivered as a finished product on an installable CD or DVD ROM.

Instead we work on delivering tagged releases through an iterative cycle that follows lean or agile methodologies, coding up individual stories to be added to the product with the next release and always with the business team leaning over our shoulders scratching out the next change request.

How much better would it be if, for every class declaration within your application code, there was only ever one, singular and unique location where the new keyword was used for each class in question?

Incidentally, I never meant to imply that we should always avoid the use of new. It is simply impossible to create object oriented code without it. I just wanted to make that bit clear at the very least.

Let me just go over that again. For each and every class that we declare in our application's codebase, we should have one and only one location where the new keyword is used on that class.

So, if we create a User class in our application, we need to have only one location where the corresponding new User() code is written. The benefits from adopting this are numerous even though they will only be felt at some point in the future. We may not know exactly when those benefits will be felt, but we do know the circumstances that will give rise to those.

# A factory method in every class

If we want to achieve that goal of ever having one instance of the new keyword per class, the easiest approach to making a start on this is to add a factory method to the class itself. Or to put it another way, every time we create a new class in our application, we can add a factory method to that class and we've gotten the single instance of the new keyword covered.

Here's an illustration of that:

Instantiaphobia

```php
class User {
    private function __construct() {
        // Init object
    }
    /**
     * Factory method included in the class
     */
    public static function create() {
        return new User();
        // A real(create) method would of course
        // do much more to set up the user instance
        // than just "return new"
    }
}
```

// Elsewhere in our application
$user = User::create();
