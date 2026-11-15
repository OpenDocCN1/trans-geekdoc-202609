![](bbox=[0.27, 0.1, 0.78, 0.23])

FIG. 6.31 Euler diagrams are okay for simple subtyping (a) but not complex cases (b).

Earlier in the chapter, Euler diagrams were used to depict one set as a subset of another. In designing a conceptual schema, we often need to introduce subtypes and spell out clearly what is a subtype of what. Euler diagrams may be used to do this for simple cases, such as Fig. 6.31(a) where B and C are subtypes of A.

Interpreting this as a hypothetical Euler diagram, the question is open as to whether A contains any elements not in B or C. If A does have more elements, this can be shown by adding an asterisk to the region outside B and C. As discussed in Section 8.2, the Barker notation for ER instead uses a special type called “Other” for this purpose.

The good thing about Euler diagrams is that they show containment intuitively by placing one set or type spatially inside another. This works well for simple cases. In practice, however, an object type may have many subtypes which might overlap, and a subtype may have many supertypes.

For example, the subtype pattern in Fig. 6.31(b) depicts the following information: B, C, and D are subtypes of A, and E is a subtype of both C and D. Moreover, B overlaps with C (i.e., they may have a common instance) and C overlaps with D, but B and D are mutually exclusive (cannot have a common instance). For example, A = Person; B = Asian; C = Consultant; D = American; E = TexanConsultant.

For such cases, Euler diagrams become hopelessly complicated. Moreover, individual subtypes may have many specific details recorded for them, and there is simply no room to attach these details if the subtype nodes are crowded together inside their supertype nodes.

For such reasons, Euler diagrams are eschewed for nontrivial subtyping. What we need is a simple notation that can be used to display subtypehood and subtype roles no matter how large or complex the situation is. This is achieved by displaying subtypes outside their supertype(s) and depicting the subtype-supertype connections by means of an arrow.

The basic idea is shown in Fig. 6.32. Here, A and B are object types. Suppose A = Employee and B = Manager. The entity type Employee is the set of all employees about which facts might possibly be recorded. The subtype Manager is the set of all managers about which facts might be recorded. At any given database state, pop(Employee) and pop(Manager) are, respectively, the set of employees and set of managers actually referenced in the database.