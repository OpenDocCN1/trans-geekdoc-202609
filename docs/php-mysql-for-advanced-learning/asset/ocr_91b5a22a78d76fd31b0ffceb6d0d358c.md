# PHP OOPs Inheritance

Inheritance is the process of creating a new class from the existing. However we can also add some additional functionality or resources to the newly created class apart from the existing base class.

It could be useful if you have certain classes represent some common methods or properties. For example The e-Commerce portal have several classes and in each class you require some user information like email and auth key, So instead of creating separate properties for each class you can create a master class and let allow other classes to use these properties using inheritance.

When we say an inherited class is a child class or sub class and from which we inherit is called the parent class or base class.

There are several types of Inheritance in PHP OOPs programing are listed below-

+   - **Single Inheritance**: When one class is inherited by a single class called Single Inheritance.
+   - **Multilevel Inheritance:** When a parent class is inherited by a child class then that child class is further inherited by child class.
+   - **Hierarchical Inheritance**: When a single parent class has more than one child class called hierarchical inheritance.

*Please note PHP doesn’t support multiple inheritances , However **Traits** are there in PHP to solve the same.*