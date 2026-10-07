Code, but in the abstract sense.

When you create an abstract class, which of course you will do so now in order to lay down the blueprint for a new data type, you are in effect specifying the interface for that type. You are declaring it to the world, or at least as far as the boundaries of your application’s codebase goes, how consumers, collaborators and clients of this new data type may interact with it. When you provide the public methods for your new data type, you're saying "Look, when you've got a variable of this particular data type, you can do this with it. You can expect it to behave in this particular way." As with arrays, strings and integers, it should be with the new objects that you create.

With inheritance, you can make a real mess of this, especially when it comes to the values that you return from a method call. For the time being at least PHP doesn’t allow you to specify the return type in a method’s declaration in the same way as, say Java does. Let me show you a quick snippet of Java code to help illustrate this.

```
abstract class Foo {
    public Bar getBarInstance() {
        return new Bar();
    }
}
```

The method declaration on line 3 indicates that the values returned from this method will be instances of the type Bar by specifying the return type before the actual method name.

Since PHP doesn’t rely on the power to enforce return types from method calls, we have to rely on ourselves and our teammates to follow a convention, a standard approach of honouring the interface that we specify in the abstract parent. Of course, this is readily communicated when the abstract parent class provides an implementation for that method. The developer can see in the code expected return type from calls to this method.

What’s missing though is the declaration of the return type when the abstract parent class also defines an abstract method. One such as this: