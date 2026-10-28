# # Additional skills for working
# with objects

Now that you’ve seen the basic skills for working with objects, you’re ready to learn additional skills for working with objects. Although you won’t need these for most applications, you may need them occasionally.

# ## How to loop through an object’s properties

Figure 14-10 shows how to use a foreach loop to loop through the properties of an object. Although the code in this figure just displays each property, you can perform any type of processing on each property of the object.

The foreach loop works differently depending on whether it’s coded inside or outside of the class for the object. If you code a foreach loop within a method of a class, the foreach loop processes all properties whether they are public, protected, or private. If you code a foreach loop outside of a class, the loop only processes the public properties of the object.

Using a foreach loop to process an object’s properties works much like using a foreach loop to process an associative array. To start, you code the foreach keyword followed by a set of parentheses and a block of code. Within the parentheses, you code a reference to the object followed by the as keyword, an optional variable to hold the property name, and a variable to hold the property value.

The first example in this figure defines an Employee class that contains both public and private properties. To save space, the get and set methods for the private properties aren’t shown in this example. Within this class, the showAll method uses a foreach loop to display a list of all property names and values.

The second example creates an object from the Employee class and sets all four properties. Here, the constructor sets the two public properties, and methods set the two private properties.

The third example calls the showAll method of the Employee object to execute a foreach loop that’s coded inside a class. As a result, this code displays all properties of the object including its private properties.

The fourth example codes a foreach loop outside the class declaration. As a result, it only displays the two public properties of the object.