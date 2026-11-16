object associated with it. The most obvious way to construct this would be to have an array of Course objects as a member variable of the Student object, as shown here:

```
/* student class */
class Student {
public $courses = array();
// ... other methods/properties
}
/* using the student class */
$objStudent = new Student(1234); //constructor not shown above
foreach($objStudent->courses as $objCourse) {
print $objCourse->name;
}
```

Of course, if the most obvious approach were the best possible approach, this book wouldn't require this chapter. The previous method has a few problems:

+   - Exposing the array of Course objects as a public member variable breaks encapsulation. There is no opportunity to validate changes to the array, or to change the state of the Student object, should that be necessary.
+   - It's not obvious from this implementation how the courses will be indexed in the array, and how to traverse that array to find a specific Course object in which you might be interested.
+   - Most important, to ensure that the courses array is available to any code that might want to use the Student object, you must pull up all the course information from the database at the same time as the student information. This means that even if you want to print only the student’s name, you must fetch all the information about courses, unnecessarily increasing load on the database server and bogging down the entire application.

The Collection class is designed to solve all these problems. It provides an OO wrapper around an array, and implements a mechanism that enables lazy instantiation. Lazy instantiation defers creation of the members of the collection until they are actually needed. It’s called “lazy” because the object determines on its own when to instantiate its component objects, rather than create them when it is instantiated. When you create a Student object, the Course objects should not be created at the same time. Only when you first attempt to access the courses should they be created, and this should happen automatically without requiring you to do anything special.

The functional requirements of the Collection class are as follows:

+   1. Establish a wrapper around an array of objects.
+   2. Provide methods to add, remove, and fetch the member objects in a predictable, obvious way.
+   3. Enable you to easily determine how many member objects exist in the collection.
+   4. Enable you to use lazy instantiation to save system resources.