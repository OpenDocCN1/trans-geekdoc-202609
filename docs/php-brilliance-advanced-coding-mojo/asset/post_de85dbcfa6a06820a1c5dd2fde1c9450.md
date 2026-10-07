
# Talking Points

place and it remains a perfectly valid pattern. To be certain, you will never want to instantiate a new database connection for every query that you perform, and so it remains appropriate to employ the Singleton pattern for such things as this.

However, the problems with the approach above are manifold, with the principle one being less about the code itself and much more about how this code encourage its usage throughout the rest of the codebase.

With or without a namespace, the database singleton instance is globally accessible, leading to code that looks very much like the following.

```php
// elsewhere...
class OrderModel {
    private $db;
    public function __construct() {
        $this->db = Database::getInstance();
    }
}
```

when a developer who knows that he needs to avoid using the anti-pattern and not to pass the database connection through a controller does something like this in their code, the result is a bit of a tangle. What we end up left with is a hard-coded dependency; an OrderModel class that is tightly coupled with the Database class, which in turn depends on Config class. In other words, all of wrong.

This is a prime example of tightly coupled code. Our OrderModel has a clear dependency upon the Database class, given that it is hard-coded in the body of the __construct() method. Worse than this is a flagrant disregard for the idea of only talking to our closest friends per the Law of Demeter. Yet, the worst is still to come; acquiring the database connection in the __construct() method presents us with a particular challenge. All of these things render our OrderModel prone to failure. How? Ignoring the fact that there's no error handling in the code above would allow it to safely recover from a failed connection attempt, the tightly coupled nature of this code imposes additional responsibilities on the development team to ensure that there are no adverse effects from changes occurring now and in the future.

The very best way for a development team to avoid adverse effects of the changes they make to codebase is to employ tests. Lots of tests. Software testing can be done in a variety of different ways: functional testing, integration testing, regression testing and unit testing to make four. Each type of testing involves varying amounts of labour at various stages. Unit testing requires the most amount of labour at the setup stage; you write the code and you write the tests to go with it (the other way around if you're into test driven development) but there's little effort involved in running test suites.

At the end of the spectrum, functional testing requires little effort at the code creation stage but disproportionately intensive on the delivery stage, especially if the development team is working in concert with QA. Engaging in iterative build cycles, such as those encouraged by agile methodologies and processes, means that we want most if not all of our testing to be automated. It would serve us all to devote one week of each sprint to testing and clearly want to save ourselves as much pain as possible whilst we go about delivering our code one story at a time. That means the right amount of automated testing.

So which levels are the right ones? Fortunately, this problem has been solved already. Mike Cohn, in his excellent book Succeeding with Agile, proposed the concept of the Testing Pyramid, which illustrates perfectly how to concentrate most of our efforts at the unit level, proving the pyramid's broad base with the widest level of test coverage and proceeding to narrow the scope of each testing level until we reach the functional tip.

Many developers hate unit testing, most common reason is that it takes too much effort to do it properly. Another answer to that is that bug-fixing takes too much effort and you have no choice but to do it properly, at the expense of spending time working on new stuff or worse, sacrificing time for it!

Adopting a regimen of unit testing, building up an effective set of test suites with a high degree of code coverage will save you and your team countless hours of future bug fixing. This is a very good thing. In order to build up those test suites, you have to create code that is testable in the first place. Just to be clear, let's bring that OrderModel back into view.

```php
class OrderModel
{
    private $db;
    public function __construct()
    {
        $this->db = Database::getInstance();
    }
}
```

As stands, this poor model class is impossible to unit test. Why? Firstly, we have a hard-coded dependency on the Database class, right there in the code, making virtually impossible to test this class without having the Database class present, due to the call to getInstance(). I say virtually impossible because there's a clever piece of kit called Patchwork which allows you to rewrite class definitions on the fly, and includes statically defined class methods too. You should consider it as an escape plan for testing legacy code, rather than a get-out clause for writing untestable code now and in the future!

Secondly, that hard-coded dependency is written into the constructor, which in turn means that you can't test the method directly, only the after effects become evident after it's called (i.e. a new object instance is created). Clearly then, we need a different approach to development since "going live" with an untested and untestable OrderModel doesn't bear thinking about. Which is what this part of the book has been largely about: promoting code that exhibits high structural quality by promoting loose coupling as a means of achieving testability.

Tell, Don't Ask us to encapsulate business logic in the right places; places where logic is readily testable. The Law of Demeter wants us to decouple our code by only talking (collaborating) with our closest friends. Friends can be readily replaced with mocks and stubs in a testing environment. Instantiaphobia wants us to concentrate the process of object creation in very distinct locations, either dedicated factories or a dependency injection container. Why? Because newing up objects willy-nilly entails tight coupling to the classes so referenced.

For a more thorough treatment of writing highly testable code, I have one more recommendation for you and book recommendations go, this one's a strong one. In Grumpy Programmer’s Guide to Building Testable PHP Applications Chris Hartjes delivers some excellent advice on how to focus on writing testable code from the outset. To quote the follow directly:

> The best applications are ones that consist of small, loosely-coupled modules that can be combined to solve problems. - Chris Hartjes

This has been a key focus of Part Three: raising the structural code quality of the applications that we write by promoting the concept of loose coupling. In doing so, we are able to provide a broad base of unit test coverage and thereby go a long way towards guaranteeing that quality.

Which brings us back to our poor, old OrderModel, which, if we're honest, is a candidate for needing 100% test coverage. Before we even get onto the matter of testing its methods, we need to fix that constructor.

# Talking Points

# class OrderModel

```php
{
    private $db;
    public function __construct(Database $db)
    {
        $this->db = $db;
    }
}
```

There. Done.

What we have covered though is precisely how our OrderModel is going to be given that database connection in the actual application itself. That sort of thing requires the application of “backwards” to be sent back to the browser.
