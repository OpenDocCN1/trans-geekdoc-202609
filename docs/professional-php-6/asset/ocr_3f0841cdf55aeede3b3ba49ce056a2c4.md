You can now take a look at how to begin putting together this solution using UML. One caveat, however, should be made clear before you begin. This chapter demonstrates how, while designing an application, your thinking might evolve as you discover new and better ways of implementing the solution. As a result, the chapter should be read more as a progressive evolution and development of the sample application, rather than as a straightforward listing of its code. A concrete example such as this can help you gain a better understanding of how the principles of object-oriented programming (OOP) work.

# The Contact Manager UML Diagrams

Fire up the UML diagramming application of your choice and create a new file called ContactManager.[extension], where [extension] is the default file extension for your application (for example, .dia for diagrams created using Dia, and so on).

First, create classes for the different kinds of contact information that you want to represent. For this sample application, these are address, e-mail address, and phone number classes — but you could create classes for whatever type of contact information you require. Table 3-1 shows the sample application properties.

# Table 3-1 Contact Infor mation Classes

| Class | Properties |
| :--- | :--- |
| Address | street1<br>street2<br>city<br>state<br>zip (zip code)<br>type (home, work, and so on) |
| Email | email<br>type |
| PhoneNumber | number<br>extension<br>type |