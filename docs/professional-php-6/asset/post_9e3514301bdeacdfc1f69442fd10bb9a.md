
object model that appeared starting in PHP 5. For those already familiar with OOP in PHP 5, little has changed in version 6.

## Summary

In this chapter, you explored the concept of object-oriented programming (OOP). A class was shown as a blueprint for creating objects. Objects are run-time bundles of data and functions created from a class definition. They have characteristics, called _properties_, and behaviors, called _methods_. Properties can be thought of as variables, and methods as functions.

Some classes share a common parent type. For example, squares (children) are a type of rectangle (parent). When you declare a class to be a subtype of a parent class, it inherits the methods and properties of the parent. You have the option to override inherited methods. You can completely re-implement the method, if you so choose, or continue to use the parent’s implementation but also add specializations particular to the subclass (or not override the method at all).

Encapsulation is an important concept to OOP. It refers to the capability of a class to protect access to its internal member variables and shield users of that class from the particulars of its implementation. Member methods and properties have three levels of visibility: private, protected, and public. Private members can be used only by the class’s internal operations. Protected members are visible to subclasses. Public members can be used by code outside the class.

Object-oriented (OO) support in PHP received a major overhaul with the introduction of PHP 5 and the Zend Engine 2. New features and significant performance improvements since PHP version 5, and further enhanced in PHP 6, make PHP a real OOP language.

Chapter 2 discusses the Unified Modeling Language (UML), a system for diagramming OO software architecture that will provide you with the tools for describing and planning the architecture of even the most complex applications.

## Unified Modeling Language (UML)

If you’re the only programmer working on a small project, drawing a small sketch of the application on paper or keeping the design completely in your mind is often sufficient. A solo programmer can usually complete a project without any problems this way.

Suppose, however, that you were to get a larger project requiring two developers. You’re the one who’s responsible for designing the system, and the second developer is there to help you write the code. How would you communicate the design of this system to the other person? You could describe in words what classes were necessary, and provide a description of how the system functions both for the end user and internally. After a while, you might end up with a lot of text describing the system. If you imagine a larger project, it quickly becomes clear that describing a large software system purely in words is not practical; and if you created diagrams of your own design, then you would have the added task of explaining your system of notation to the other members of the team.

The Unified Modeling Language (UML) was designed to solve this problem. UML is primarily a language of standardized diagrams, each of which lends itself to describing a particular area of software design. UML gives everyone the same way of “speaking” about a system, and provides a powerful method of visualizing it.

In this chapter, you’ll work through the design and development of a hypothetical band-tracking system called BandSpy. In the process, you’ll learn about UML diagrams and where they fit into the process.

### Requirements Gathering

Here’s the hypothetical scenario for this chapter. A client from a record company has contacted you to develop a Web-based system to track the bands that the client represents. During an initial phone conversation, the client explains that BandSpy should enable Web users to view details about the different bands the company represents, and check out upcoming concerts. Someone from the record company should be able to add new bands to the system, edit existing band information, and book new concert performances for the bands. Although your conversation with the client is informal, it begins a key part of the software design: the requirements-gathering phase. In this phase, you’ll want to determine exactly what the software needs to do to satisfy its users.

### Interviewing the Client

Speaking on the phone, you arrange to meet with the client. After some quality get-to-know-you time, the meeting progresses to a further discussion of the system. The attendees of the meeting are Bill (the owner of the company), Jane (the operations manager), and Tom (the company “computer guy”).

During your initial interviews, getting a feel for the roles of the people who are involved is important. You can infer that the people attending the meeting have some interest in how the software works. That interest, however, may or may not always be beneficial to the outcome of the project.

The key person to identify during requirements gathering is the person who has detailed knowledge of the domain — the area that the software will model. That could include someone who previously did manually what the software will now automate, or it could be someone who knows how the business works and what the software must do to correctly model it. This person is often referred to as a domain expert.

Over the course of the interview, Jane does most of the talking. She describes what they’re hoping the system can accomplish and how the company currently handles this process. It’s a good bet that Jane is your domain expert. During further interviews, speaking to her directly will be useful. Bill stays quiet most of the time; he probably has other matters to attend to. Tom mentions that he’ll be the one actually entering the data into the system. You note that you may have to devote a little time to explaining the use of the administration tools to him.

During the course of the meeting you take notes on what Jane says the system must do, and you come out with the following list:

- [ ] Users can visit the BandSpy Web site and browse information about bands. Band information includes the type of band, musicians in the band, and what instruments they play.
- [ ] Users can view information about upcoming performances that might include one or multiple bands.
- [ ] A site administrator can add new information about bands.
- [ ] A site administrator can edit existing band information.
- [ ] A site administrator can add a new performance. Adding a new performance includes booking a venue and generating tickets. Separate third-party companies handle both the venue booking and the tickets. These companies have reservation systems that you will need to notify via the BandSpy software.

Now that you have a list of requirements, it’s time to start putting the UML diagrams to work.

### Use Case Diagrams

Use case diagrams show the system from the task-oriented perspective of a user. One use case represents a task the user is trying to accomplish with the system. Figure 2-1 shows a very simple use case diagram for users visiting the BandSpy site and browsing band information.

![](img/a1b732997d9cb194dceec0570dc79710_46_0.png)

The stick figure is called an actor, and the bubble is the use case. The line indicates that this actor can perform the connected use case. In use case diagrams, the actor is usually a role associated with a person, although it can represent an external system that acts upon your system.

Notice that the use case “browse band info” is rather general. A high level of detail isn’t necessary here. You just want to be able to cover all the use cases the system should be capable of handling. If necessary, use cases can be broken down into their separate scenarios. A scenario is the sequence of steps comprising the use case. For example, the scenario for the previous use case is as follows:

- 1. The user goes to the BandSpy Web site.
- 2. The user navigates the site using the menu.
- 3. The user examines band/musician/concert information.

Figure 2-2 shows the use case diagram for the administrative tasks.

![](img/a1b732997d9cb194dceec0570dc79710_46_1.png)
