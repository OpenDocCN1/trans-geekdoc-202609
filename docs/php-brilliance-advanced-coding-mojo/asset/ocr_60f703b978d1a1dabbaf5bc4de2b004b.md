# Instantiaphobia 261

significant number of features, this means that this particular line (with or without constructor parameters) may be found in hundreds of different locations.

If we were to go through encapsulation chapter again, but inside an application that invoked a new User() more than a hundred times, would that not represent an awful lot of leg work in order to update every occurrence? IDEs, terminals and command line clients all provide a global search function, in which theory will allow you to locate and modify every occurrence in order to accommodate the changed modified method signature of the constructor.

That is, as long none of your colleagues has implemented code that creates objects using a variable that holds a class name. What do I mean by that? Well, let me show you another snippet of code, one that illustrates dynamic class name resolution:

```
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