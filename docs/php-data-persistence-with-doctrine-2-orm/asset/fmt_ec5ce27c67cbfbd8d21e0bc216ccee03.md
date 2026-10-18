
### 1.4 Conventions used in this book

Code listings are highlighted and have line numbering. Listings that start with a `$` symbol represent the command line, lines stating with a `>` symbol represent command output. New terms are written in *italic* on first usage.

### 1.5 An important notice for Amazon customers

If you bought this book at Amazon, it is currently somewhat more difficult to ensure that you automatically receive all of its updates as they are published. To avoid problems, please send a short email with “Updates Doctrine 2 book” in the subject line to mail@michael-romer.de. In this manner, you can be certain that you will really always have the latest version of the book. As thanks for your efforts you will also additionally receive the PDF and EPUB versions of the book.

## 2 Introduction

### 2.1 Object oriented programming (OOP) & the Domain Model

PHP developers nowadays mostly think and code in an object oriented way. Application functionality is built using classes, objects, methods, inheritance and other techniques of object orientation. In the beginning, OOP has mostly been used for the general technical aspects of application, such as MVC frameworks or logging and mailing libraries. All these components more or less can be used “as is” in all applications, no matter what domain the application is in: e-commerce, portal or community site. For complex systems and also if aspects such as maintainability and extensibility are important, OOP in the domain specific code also is an advantage. Mainly, every application consists of two different types of code: general technical code and domain specific code. General technical code often is re-usable when built as a library or framework, domain specific code often is too custom to be re-used.

Object oriented domain specific code is characterized by the existence of a so-called *domain model*. A domain model mainly means:

*   Classes and objects represent the main concepts of a domain, the so-called *entities* (these elements can also be *value objects* to be precise, but compared to entities, value objects don’t have a persistent identity). In an online shop, the main elements would be “Customer”, “Order”, “Product”, “Cart” and so forth.

*   Domain specific classes and objects may have associations between them. Again, in an online shop, an “Order” usually has at least one “Customer” that it references as well as one or more references to the “Product(s)” ordered.

*   Domain specific functions are implemented as a part of an entity. In an online shop, a “Cart” often has a `calculateTotalPrice()` method to calculate the final price based on the items in cart considering their quantity.

*   Functions that span multiple entities usually are implemented in so-called *services*, simply because they cannot clearly be assigned to one single entity. Again, in an online shop, the “Checkout” service may take care of lowering the inventory, invoicing, updating the order history, etc. The service deals with several different entities at once.

*   Whenever possible, domain specific objects are used instead of generic data containers such as PHP arrays (exceptions prove the rule here).

*   Business logic (such as business rules) is implemented within the domain objects of an application, not in e.g. controllers, whenever possible (controllers are used in MVC based frameworks to handle user input).

The main advantage of the domain model lies in having the domain specific code centrally in defined classes and objects supporting maintenance and changes. The possibility of incidentally breaking a function, when changing or extending code, drops. By isolating domain specific code from general technical code, portability is supported. That’s helpful, e.g. when migrating from one application framework to another.

Besides the advantages mentioned above, the domain model also supports teamwork. Often, when building and launching a new software product, besides programmers also business and marketing folks are involved. A domain model can bridge the mental gap between business and IT by unifying the terminology used. This alone makes a Domain model invaluable.

### 2.2 Demo application

Concrete examples make things easier to understand. Throughout this book, a demo application called “Talking” will help to put theory into practice. Talking is a (simple) web application allowing users to publish content online. The application’s domain model looks like this:

![Demo application "Talking" - Domain Model](images/domain-model-talking.jpeg)

Demo application “Talking” - Domain Model

A `User` can write `Post`s. A `Post` always only has one author and both entities reference each other. A User can act in one or more `Role`s. A `User` references its `Role`s, but from a given `Role`, one cannot access the `User`s in this Role. A `User` references `UserInfo` holding the date of registration and the date of de-registration if available. `UserInfo` references back to a `User`. A `User` references `ContactData` where email and phone number is saved. `ContactData` does not reference back to its `User`. A `User` may reference another `User` as its life partner. The `USER`’s life partner references back if known. A `User` may have an unlimited number of friends. Given a `User`, one can identify its friends, but there is no reference back. The `Post` of a `User` can have an unlimited number of `Tag`s. A `Tag` can be re-used in several `Post`s. There is a bi-directional association between a `Post` and its `Tag`s. A `Post` references its `Category`, however, there is no reference from a `Category` to its `Post`s. A `Category` can have subcategories which it references, as well as a parent `Category`, if given. Categories are user specific. A `User` references its categories, but there is no reference back.

The domain model is designed to use as many different association types as possible, so that we can see most of the features of Doctrine 2 in action in the scope of the demo application. In a real application, the domain model would probably look a bit different. As you can see, not every association between entities is bi-directional. As we will see later in this book, this essentially is a feature of an ORM system like Doctrine 2 living in the object oriented world. In relational databases, there are no uni-directional associations. They are always bi-directional by design.

## 3 A self-made ORM

| ![information](images/leanpub_information.png) || 

#### Jump straight into Doctrine 2?

This section describes why Doctrine 2 is such a big help for the application developer. Step by step, we will implement certain ORM features on our own, that Doctrine 2 already ships with. This chapter is not needed to learn Doctrine 2-but it helps understanding why one should learn it. |

| --- | --- |

### 3.1 Loading an Entity

A domain model is a good thing. As long as the application developer acts in his familiar object oriented world, there are no obstacles when designing and implementing a domain model. It gets harder, if it’s about persisting objects of the domain model in relational databases or loading and reconstructing previously stored objects. There is, for instance, the fact that objects are more than just dumb data structures. With their methods, they have behavior as well. Let’s consider the `User` entity definition of the demo application Talking:
