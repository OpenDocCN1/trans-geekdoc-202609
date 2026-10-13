
The UML specification provides syntax and semantics for these diagram types but not yet a process for developing UML models, other than to suggest that model development should be use case driven, iterative, and architecture centric. Various companies promote their own modeling process for UML.

Although all the UML diagram types are worth studying, this book focuses mainly on information modeling for databases. This chapter addresses data modeling in UML, so considers only the static structure (class and object) diagrams. Class diagrams are used for the data schema. Object diagrams provide a limited means to discuss data populations. Some other UML diagram types are discussed in [Chapter 15](#Ch015_773-830_B9780443237904000190.xhtml).

Like ER, UML uses attributes. As discussed in earlier chapters, attributes are great for logical models, but are best modeled as relationships when performing conceptual analysis because this facilitates validation and minimizes the impact of change. For such reasons, we believe the best way to develop UML data models is to first do an object-role modeling (ORM) model and then map it to UML. Because ORM will be used to clarify the data modeling concepts in UML, to gain the full benefits of this clarification you should be familiar with the ORM concepts covered in earlier chapters.

No language is perfect, ORM included. Overall, UML provides a useful suite of notations for both data and process modeling while ORM is currently focused on data modeling only.

## 9.2 Object-Orientation

UML facilitates object-oriented (OO) code design because it covers both data and behavioral modeling, and lets you drill down into physical design details relevant to OO code. The class diagram in [Fig. 9.2](#Ch009_347-399_B9780443237904000013.xhtml#f0015) models a class whose instances are screen dialog boxes.

![Fig. 9.2 Example of a UML class.](images/B9780443237904000013/f09-02-9780443237904.jpg)

[Fig. 9.2](#Ch009_347-399_B9780443237904000013.xhtml#B-f0015) Example of a UML class.

The class shape in [Fig. 9.2](#Ch009_347-399_B9780443237904000013.xhtml#f0015) has three compartments. The name compartment includes the class name as well as a tagged value naming the author of the class. The attribute compartment lists the visibility, name, and type of each attribute. The visibility settings `+`, `-`, `#`, and `~` indicate whether the attribute is public, private, protected, or package, respectively. These visibility settings are software, not conceptual, issues. The `size` attribute is initialized to a given area value. The operation compartment specifies what operations are encapsulated in instances of the class. In this example, the operations may be implemented by methods to display the dialog box at a specific position, and to hide the dialog box.

[Fig. 9.3](#Ch009_347-399_B9780443237904000013.xhtml#f0020) shows another class diagram that depicts `Employee` and `Car` classes as well as an association corresponding to the ORM fact type `Employee drives Car`. The association is depicted by a line between the classes. The role name `driver` on the left end of the association clarifies the intended semantics (an association reading could also be supplied). The open arrow tip at the right end of the association is a navigability setting indicating that fast access is required from employee instances to their car instances. This may be implemented by including pointers from employee objects (software objects) to the car objects that model the cars that they drive. Navigability settings are implementation issues related to performance, not conceptual issues about the business domain.

![Fig. 9.3 The navigability setting demands fast access from Employee to Car.](images/B9780443237904000013/f09-03-9780443237904.jpg)

[Fig. 9.3](#Ch009_347-399_B9780443237904000013.xhtml#B-f0020) The navigability setting demands fast access from Employee to Car.

By omitting implementation details such as attribute visibility and association navigability, class diagrams can be used for conceptual analysis. When used in this way, class diagrams are somewhat similar to ER models. But there is a significant difference arising from the OO perspective. If you look at the classes in [Figs. 9.2](#Ch009_347-399_B9780443237904000013.xhtml#f0015) and [9.3](#Ch009_347-399_B9780443237904000013.xhtml#f0020), what strikes you as missing?

You guessed it! No identification schemes are provided for the classes. In object-oriented programming, objects may be identified by their memory addresses or internal object identifiers (oids), so UML does not require a value-based identification scheme for use by humans in communicating about the objects. For conceptual analysis, however, human-oriented reference schemes (e.g., dialog box numbers, employee numbers, car registration numbers) must be supplied.

To partly address this issue, UML 2.5 now allows you to mark a property (e.g., attribute or association end) as being (part of) the `identifier` for its containing class by appending `{id}` to the property name. However, UML has no standard notation for declaring a single-valued attribute to be a secondary identifier or even to be unique.

This book uses `{U*n*}` for uniqueness (*n* > 0), where the *n* is used to disambiguate cases where the same uniqueness constraint might apply to a combination of attributes. In [Fig. 9.4](#Ch009_347-399_B9780443237904000013.xhtml#f0025), for example, employee number and car registration number attributes are marked as the primary identifiers of employee and car, respectively. This entails that they are mandatory and unique. Additionally, the combination of employee name and birthdate has been declared unique. We also dropped the navigation arrow, as it is irrelevant to the business semantics.

![Fig. 9.4 Adding notations for identifiers and uniqueness.](images/B9780443237904000013/f09-04-9780443237904.jpg)

[Fig. 9.4](#Ch009_347-399_B9780443237904000013.xhtml#B-f0025) Adding notations for identifiers and uniqueness.

The requirement that each class *must* have a value-based identification scheme distinguishes both ORM and ER from UML. ORM classifies objects into entities (nonlexical objects) and values (lexical objects) and requires each entity to be identified by a reference scheme used by humans to communicate about it. ORM uses `object`, `entity`, and `value` to mean `object instance`, `entity instance`, and `value instance`, respectively, appending `type` for the relevant set of all possible instances. Entities may be referenced in different ways, and typically change their state over time. Glossing over some subtle points, values are constants (e.g., character strings) that denote themselves so do not require a reference scheme.

[Fig. 9.5](#Ch009_347-399_B9780443237904000013.xhtml#f0030)(a) depicts explicitly a simple reference scheme in ORM. If an entity type has more than one candidate reference scheme, one may be declared preferred. A preferred reference scheme for an entity type maps each instance of it onto a unique, identifying value (or a combination of values). In [Fig. 9.5](#Ch009_347-399_B9780443237904000013.xhtml#f0030)(a), the reference type has a sample population shown in a reference table (one column for each role). Here, icons are used to denote the real world employee entities.

![Fig. 9.5 A simple reference scheme in ORM, shown (a) explicitly and (b) implicitly.](images/B9780443237904000013/f09-05-9780443237904.jpg)

[Fig. 9.5](#Ch009_347-399_B9780443237904000013.xhtml#B-f0030) A simple reference scheme in ORM, shown (a) explicitly and (b) implicitly.
