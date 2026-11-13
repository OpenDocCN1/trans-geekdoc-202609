Observer pattern: provides a one-to-many link between objects to notify objects of changes in state via a subscription-style service.

# Observer pattern

The observer pattern is used to maintain a list of dependent objects that have subscribed to it so that they receive notifications when an event occurs. The observer pattern allows the observing object to communicate changes to other objects that are interested in those changes.

This pattern is widely used in implementing distributed event handling systems such as in web pages, where you might add event listeners to handle user input (clicks, keyboard events, and so on).

# Interface

Before looking at how to apply each pattern, it is worth noting Java examples that demonstrate the use of an interface. The interface is not in your syllabus, but a quick introduction is merited as it is the right tool for the job to demonstrate these patterns.

An interface is a construct that defines a set of methods that implementing classes must provide, without specifying how these methods should be implemented. It allows different classes to interact with each other through a common set of behaviours, ensuring consistency and interoperability. Interfaces are similar to, but not quite the same as, abstract classes. They differ in the following ways:

+   Interfaces do not store state (no instance variables). They simply define methods that need to be implemented.

+   A class can implement multiple interfaces, whereas using normal inheritance is limited to only one parent class.

+   Interfaces do not have constructors as they are not concerned with the logic of implementation (no variables, remember). They are just focused on providing a list of methods that require implementation.

An example might be an interface called School. This interface defines methods attendClass (), doHomework (), takeExam (). Different students might implement these methods differently, but they must implement all of them in one form or another.

```
/* The interface designs a contract specifying methods that must be provided by
 * those classes that implement it. */
interface School {
    void attendClass();
    void doHomework();
    void takeExam();
}
class StudentA implements School {
    public void attendClass() {
        System.out.println("Student A attends class online via Zoom.");
    }
    public void doHomework() {
        System.out.println("Student A does homework in the early morning with a quiet background.");
    }
}
```