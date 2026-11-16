
Individual member variables remain much the same:

```
protected $FirstName;
protected $LastName;
protected $Username;
protected $Password;
protected $EmailAddress;
protected $DateLastLogin;
protected $TimeLastLogin;
protected $DateAccountCreated;
protected $TimeAccountCreated;
```

Notice that the variables are declared ‘protected’ — this is important, as it permits the parent class to access and manipulate those variables directly.

Finally, you can see the implementation of the two all-important abstract methods:

```
protected function DefineTableName() {
    return("system_user");
}

protected function DefineRelationMap() {
    return(array(
        "id" => "ID",
        "first_name" => "FirstName",
        "last_name" => "LastName",
        "username" => "Username",
        "md5_pw" => "Password",
        "email_address" => "EmailAddress",
        "date_last_login" => "DateLastLogin",
        "time_last_login" => "TimeLastLogin",
        "date_account_created" => "DateAccountCreated",
        "time_account_created" => "TimeAccountCreated") );
}
```

These were declared in the parent class as abstract, so you are obliged in your child class to provide an implementation using the same method name (keeping in mind that PHP is case sensitive). Neither method takes any parameters. Instead, two simple values are returned — one is a string indicating the name of the underlying database table, and the other is a simple associative array mapping relation names to PHP member variables.

## Benefits

Before closing, it’s worth taking a minute to reflect on the benefits of the approach discussed in this chapter. What you’ve been able to do is construct a reusable, portable, PDO-enabled toolkit class that enables you to create data-bound business objects in moments.

Indeed, the example `User` class itself contains not a jot of SQL — it doesn’t need to, as all of the standard CRUD (create, read, update, delete) methods can be generated for you on request. Not only is your code more lightweight, your application is also more portable. Should you later decide to port from, say, MySQL to PostgreSQL, or, indeed, the other way around, very little should need changing.

The “abstract class” approach is neat, too. You are not in the least bit limited as to what you can do in your child class. The previous example was simple, but naturally you can add your own methods, too — some of which will probably make use of SQL more complex than simple CRUD operations. In addition, there’s nothing to stop you from delegating relation mapping to something a bit more readable than PHP — maybe an XML document, for example.

In a big project with 20 or more business objects, ORM starts to make a lot of sense. You’ll wonder how you ever lived without it.

## Summary

In this vital chapter, you were introduced to a further layer of database abstraction — that of object relation mapping (ORM). Having been introduced formally to the two varieties of classes you are likely to meet in the course of your enterprise-grade PHP projects (namely, business objects and utility classes), and having learned about the measures you can use to help identify each, you were introduced to a simple example of a stateless business object representing a hypothetical commercial entity.

With an understanding of how such a business object works on a functional level, but does not retain data, you were introduced to a traditional approach to retention by binding to a database relation — namely, a specific table within a relational database — and shown how it can enable and facilitate persistence of your object’s properties in a manner largely suitable for an enterprise-grade project.

Finally, by recognizing the limitations of your business object, you built and examined a reusable, toolkit-ready enterprise class for the development of data-enabled objects in your own projects. By maintaining an identical interface to your business-specific class, you proved to yourself that a common business problem could be solved by abstracting away business-specific issues into subclasses of a toolkit-ready module.

In Chapter 8, you’ll discover that PHP, despite being developed from the ground up as a procedural Web application development language, is ideally suited for developing event-driven applications as well.

## Event-Driven Programming

Sometimes it is useful to think of an application in terms of *events* and how best to handle them, rather than look at that application’s architectural design from a traditional object-oriented (OO) perspective. That’s not to say that you must discard an OOP approach altogether to implement event handling, but rather that you build classes around the events relevant to the application. This approach is rather radical, but for many applications, you may find that it gives you a massively powerful mechanism for approaching the software architecture of the whole project.

Events occur pretty much all the time, and some of the best examples of event-driven programming are the applications you use every day, such as to manage e-mail or write text. For the end user of traditional desktop GUI applications, event handling is of paramount importance because these applications are designed to lurk around until the user does something, and then react accordingly. Of course, the same is now true for many Web-based applications.

Nearly all actions taken by a user, and even those taken by the applications themselves, can be thought of as an event. A rather contrived example of an event not initiated by a user is your machine’s clock. If you wanted to create an application that performed various actions depending on the time, you could capture certain changes in time as an event, and bundle it off to a piece of code that deals with it accordingly.

Whatever needs to be done, applications have various ways to implement a solution, and PHP 6 is no different in this regard. There is, of course, no new extension or library to deal with events, because the way you deal with them is more about how you “think” about designing an application, rather than how you actually implement it. In other words, they need no special underlying technology. Let’s take a look at one way to handle events in PHP.

### Understanding Events

An event is any occurrence to which your application can react. You will almost certainly have already written applications that have handled events in some capacity or another. When something happens or some condition is suddenly met, deciding what action to take in your code (no matter how trivial) is a form of event handling. For example, imagine that you have implemented a database holding a number of records, and you want your customers to be able to work on those records via a Web interface. You would probably realize that the users must at least be able to view and update records, so your likely reaction would be to create functions to view and edit records.

Deciding which function to call depends entirely on the input provided by the user. Accordingly, the interface you develop needs to present the various options, and enable users to decide which ones they want. After the user has decided, the application must respond accordingly by calling the correct functions, which will handle the request.

Typically, you might create a home page with two buttons, one offering the option to view the records and another to edit them. The following code snippet might suffice as a mechanism to handle that choice:

```
switch($_GET['action']) {
 case "edit_record":
 edit_record();
 break;
 case "view_record":
 view_record();
 break;
 }
```

As you can see, the previous snippet of code is designed to interpret information from $_GET (in other words, the user's request) and make a decision about what response to take, based on what the user has requested. That's it — you have handled an event that was fired by the simple action of a user clicking a button.

This principle stands for pretty much any event you could possibly imagine. For those of you who use Outlook or something similar, system-generated events are commonplace. Warnings about meetings and deadlines pop up all the time based on a specific event firing (for example, the system's clock reaching a certain time).

Of course, how you implement the code to handle events is up to you. Using a switch statement is not the only way; any sort of loop could enable you to respond to events. An if/else block would work just as well in the previous example.

You may be wondering what all the fuss is about events. After all, what you've seen so far seems simple enough. Why can't you just leave it at that? The problem with what has been discussed so far is that you could easily end up with a big mess if your application changes or grows after your initial development run. What starts off as a nice simple if statement could grow to monstrous proportions, rendering any attempts to understand it in the future very difficult indeed. This has obvious implications as your application's needs become more complex. Accordingly, you should use the simple methods alluded to previously only for very simple requirements, where you can be sure the code is at no time going to blossom into a full-blown enterprise application.

### Using OOP to Handle Events

To implement effective event-driven solutions in your own PHP applications, it is best to take a step back and determine (from a high-level perspective) how these applications should behave. A more sophisticated approach to implementing events would enable you to more easily control their behavior
