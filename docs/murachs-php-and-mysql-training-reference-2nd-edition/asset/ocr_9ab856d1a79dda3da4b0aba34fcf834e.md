# # How to code properties

Figure 14-3 shows how to code the properties of a class. To start, you code the access modifier followed by the property name and an optional initial value. The initial value must be a scalar value, an array of scalar values, or the NULL value. A *scalar value* is a literal number, string, or Boolean value.

When you declare a property, you begin by coding an access modifier to control its visibility. If you omit the access modifier, the property defaults to public. However, to make your code more readable, it’s generally considered a good practice to always code the access modifier.

In most cases, you should use the private modifier for your properties as shown in the first example. That way, you create a *private property* that can’t be directly accessed by code outside the class.

In some cases, you may want to use the public modifier as shown in the second example. That way, you create a *public property* that can be directly accessed by code outside the class. Note that this public property also includes a default value of an empty string.

If you’re using inheritance as described later in this chapter, you may want to use the protected modifier for your properties as shown in the third example. This creates a *protected property* that works similarly to a private property. You’ll learn about the differences between private and protected properties later in this chapter.

Although it’s common to code each property on its own line, you can code multiple properties on the same line as shown in the fourth example. Here, five private properties are coded on the same line by separating each property name with a comma.