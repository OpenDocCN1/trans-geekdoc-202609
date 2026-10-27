```
}
}
$tmpVisitor = new Visitor("Chandler","150");
echo "Height : ". $tmpVisitor ->m_Visitor_Height; //prints 150
```

Returning to my earlier remark that object-oriented principles are "global" in the sense that they should be regarded by a developer. I demonstrated access modifiers using the Crocodile’s cage, but I also needed to illustrate encapsulation and inheritance. Inheritance and encapsulation are essential strategies for limiting the capabilities of a class-defined object.

# Inheritance

You're probably familiar with the Crocodile’s cage, notably the one made out of steel bars. In PHP, the cage was designated as protected, which meant that it could be viewed by the Crocodile and its extended classes. In PHP5, the keyword extends should be used in the class definition to indicate inheritance.

```
class Parent
{
}
class Child extends Parent
{
}
```

Inheritance refers to the transmission of "knowledge" down the hierarchy. It is a technique for incrementally adding new functionality to existing code. Class hierarchies are used to organize classes, and heredity allows a single class's design and functions to somehow get transferred through the ladder. As a result, minimal programming is required when introducing further functionality to complex systems.

When a step is positioned at the bottom of the ladder, just the computation and information associated with that step must be added. During that period, everything else gets transferred to you. The capability of object-oriented programming to reuse existing objects is a big advantage.

# The Overriding of Method

Method overriding occurs when the base class's method is re-defined using the derived class's name, function signature, and access modifier (public or protected). The purpose of overriding a method is to provide the functionality to the base class that isn't previously specified. Assume you have a milkshake class from which two subclasses, mango, and strawberry, are derived.

While the Beverage class defines methods for mixing, shaking, and other operations, the specialized classes Mango and Strawberry will need to override the stir and mix features because they will have their own methods for mixing and stirring. Consider the following scenario for a milkshake:

```
class MilkShakes {
public function mixing_method() {
```