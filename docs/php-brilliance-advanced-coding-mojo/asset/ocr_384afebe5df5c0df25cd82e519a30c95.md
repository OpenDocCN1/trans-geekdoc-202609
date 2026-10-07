# Brain Check

We really have reached the end of Part One now, but before we move on let's take stock of what we have covered thus far.

In a way, this section might be considered a glossary; it certainly fits that particular bill. However, being a glossary isn't its full intent. Rather, it's a checklist of the topics that a developer exhibiting PHP Brilliance could stand up and deliver a lightning talk on.

Take a moment to review the list. Given thirty minutes preparation time, could you deliver a 10 slide, 5 minute presentation on each of this topics? Without resorting to a search engine?

If the answer is no, consider beefing up your knowledge on the topic in question.

# Encapsulation & information / implementation hiding

Encapsulation is the process of bundling values (properties) with the methods that act upon those properties. Information / implementation hiding is a kind of “bolt-on” concept that we can apply to update encapsulation in order to provide objects that act as black boxes, protecting their properties and controlling access via a well-defined public interface.

# Exposing state through setters and getters

Following on from the principle of encapsulation, the application of dumb setters and getters, methods that do nothing but provide access to object properties, leaves us prone to bugs caused by an object losing control over its state. Magic__get() and __set() methods can cause a great deal of problems in exposing an object's state and extreme caution should be applied before using them.

# Abstraction & Inheritance

Abstract provides us with a means of defining a new data type to live alongside the language provided types of string, integer, array and object. Inheritance