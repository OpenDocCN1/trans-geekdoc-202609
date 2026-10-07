The difference is appreciable. Out there in application code, the call for a user instance is simply $user = User::create($userId); but the object that is returned is one that has been properly prepared with the role and account objects already provided and ready for use.

For smaller applications, this approach makes the codebase immediately much more maintainable. Where previously you may had a hundred or more locations where you were instantiating User objects, there’s just one. No longer do you need to perform a global search and replace when you modify the constructor - there’s just a single method that you have to make changes to and it’s right alongside the constructor that’s being changed. This technique also brings greater convenience to you as a lower coder and greater consistency when you work in a team that has adopted this approach.

Think on it - if all of your team follow the same convention and create the object's factory method in the same class definition as the target class itself any future change to the process of instantiation for that particular object only ever to involve editing just the one file.

There’s an optional, ancillary benefit of employing this technique too. By having the factory method within the same class (or in the base class for a family of related classes), it allows you to make the constructor method itself non-public. Consequently a private or protected constructor guarantees that client code cannot bypass the factory method process in order to obtain a usable instance by calling new directly. In a team based environment the newer members will sometimes be coerced into following the house rules by by constraints placed into the code directly. A constructor that has been set to private does this automatically.

This all works just as long as the factory method is the thing that is doing the work, rather just as a proxy for a list of parameters.

Even so, it remains little than than halfway house solution. It’s vastly superior to the habit of littering codebases with new This() and new That() that our more inexperienced colleagues might be used to, but it is certainly a long way short of the ideal.

Why is this? Well, let’s take a short while to explore the two key reasons why you might also want to avoid this technique.

The first reason is one that we’ve already encountered briefly. If our factory method