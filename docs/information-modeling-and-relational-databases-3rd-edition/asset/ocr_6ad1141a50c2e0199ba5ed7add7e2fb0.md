![](bbox=[0.22, 0.1, 0.75, 0.23])

FIG. 9.2 Example of a UML class.

The class shape in Fig. 9.2 has three compartments. The name compartment includes the class name as well as a tagged value naming the author of the class. The attribute compartment lists the visibility, name, and type of each attribute. The visibility settings “+”, “-”, “#”, and “~” indicate whether the attribute is public, private, protected, or package, respectively. These visibility settings are software, not conceptual, issues. The size attribute is initialized to a given area value. The operation compartment specifies what operations are encapsulated in instances of the class. In this example, the operations may be implemented by methods to display the dialog box at a specific position, and to hide the dialog box.

Fig. 9.3 shows another class diagram that depicts Employee and Car classes as well as an association corresponding to the ORM fact type Employee drives Car. The association is depicted by a line between the classes. The role name “driver” on the left end of the association clarifies the intended semantics (an association reading could also be supplied). The open arrow tip at the right end of the association is a navigability setting indicating that fast access is required from employee instances to their car instances. This may be implemented by including pointers from employee objects (software objects) to the car objects that model the cars that they drive. Navigability settings are implementation issues related to performance, not conceptual issues about the business domain.

![](bbox=[0.35, 0.66, 0.61, 0.75])

FIG. 9.3 The navigability setting demands fast access from Employee to Car.

By omitting implementation details such as attribute visibility and association navigability, class diagrams can be used for conceptual analysis. When used in this way, class diagrams are somewhat similar to ER models. But there is a significant difference arising from the OO perspective. If you look at the classes in Figs. 9.2 and 9.3, what strikes you as missing?