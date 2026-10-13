
If the activities are implemented in some object-oriented software language, a standard approach would be to create some object within the Activity `A` instance and then pass it to the corresponding Activity `B` instance; in other words, we could say that Activity `A pushes` the data to Activity `B`. If the two activities are operating in the same memory space, this could be accomplished by passing a reference to the relevant object; otherwise, an additional step of serializing the object may be required.

From a conceptual viewpoint, these last details are irrelevant. Whether Activity `A` “pushes” an object to Activity `B`, whether Activity `B` “pulls” an object from Activity `A`, or, indeed, whether any “object” is involved at all is purely an implementation issue. From a conceptual standpoint, we certainly need to be concerned about the rights and responsibilities of activities regarding data, but we explicitly do not want implementation issues to become entangled with the process definitions.

Processes elements (at any level) utilize data in three main ways: (a) to compute some result of value to the process, (b) to determine a course of action, and (c) as information to guide process activity, for example, as reference material for a human involved in the process. Our main need is to define data scoping: which activity needs which item of data and for what purpose. If we have ambitions to automate the construction of automation systems to support business processes, this is clearly crucial. Even if we have more modest ambitions, such as simply providing a checklist to implementers, this still seems to be an important facet of process definition.

From a high-level perspective, we can classify an activity’s usage of a data item in terms of whether it is limited to reading the data item or whether it can also modify it. If modification is allowed, we can further distinguish between the ability to create new data, modify existing data, or delete existing data. (One could also predict other uses for such information, such as identifying the data privileges that should be given to specific user roles, but that is outside the scope of this chapter.) In contrast, the types of features that we would *not* want to specify at a conceptual level include the following.

### Communication mechanisms

*   between different levels (process, subprocess, activity)
*   between different elements (e.g., activity to activity)
*   between process elements and the environment

### Data transfer mechanisms

*   “push” (data explicitly sent to process element)
*   “pull” (data requested by process element)
*   pass by value versus pass by reference
*   with or without locking
*   with or without transformation
*   etc.

These issues are largely outside the scope of a business process model, and so we don’t consider them in detail here. Of course, a business model alone does not contain sufficient information to determine the detailed mechanisms (and deliberately so). What we do have is the ability to identify the relationships between low-level atomic activities and low-level data manipulation and query operations.

We are not limited to operating only at this level because, as we have seen, we can compose collections of low-level elements into higher-level elements until we reach a more convenient level of expression. However, this still leaves the realization underconstrained, as there could be many ways of linking data to process for the same conceptual design. The choices between the alternatives are somewhat orthogonal to the conceptual elements. For example, are we building a self-contained or distributed system operating over a network? How many users do we intend to support? Are we concerned about issues such as availability and scalability? The additional information required is what might be termed the *technical architecture* of the system, which is more concerned with the engineering aspects. In principle, given a definition of the technical architecture of a system, we should be able to generate the necessary system elements required from a business model. We have already seen how this could work in examples such as Executable UML. In the future, we can expect similar ideas to be widely adopted as a natural outgrowth of conceptual modeling.

## 15.9 Process Models, Databases, and ORM

BPMN provides a standard notation and semantics for process descriptions. It has support for defining the execution of business processes but can be used to define processes at a purely conceptual (implementation-independent) level. Equivalently, ORM supports information modeling at a conceptual level, so we have the capability of defining both business information and business activities in a consistent way. But although both BPMN and ORM produce valid business models, neither approach makes any reference to the other in their basic forms. In this section, we will see how these two viewpoints can be reconciled.

The BPMN standard provides two elements relating to data along with the ability to associate them with activities, summarized in [Fig. 15.36](#Ch015_773-830_B9780443237904000190.xhtml#f0185).

![Fig. 15.36 Data options in BPMN.](images/B9780443237904000190/f15-36-9780443237904.jpg)

[Fig. 15.36](#Ch015_773-830_B9780443237904000190.xhtml#B-f0185) Data options in BPMN.

Because an ORM model generally specifies information that is intended to be stored (not temporary variables that are used then discarded), the BPMN `Data Object` is not relevant to a BPMN-ORM linkage. This leaves the `Data Store` reference as the only way of representing persistent information in a BPMN model.

A BPMN `Data Store` reference is linked to an `Activity` (usually a `Task`) by a `Data Association`. In BPMN, associations are generally used to link artifacts to process elements and are shown with a single dotted line (dashed lines have a different meaning). Associations can have an arrowhead showing the directionality of the association, but the semantics of this for a `Data Store` are a little ambiguous in the BPMN specification. Access to a database is usually a request-response cycle, so it’s uncertain what an arrowhead would be indicating. The sensible option is therefore to use an association with no arrowhead.

The only textual notation provided for the `Data Store` reference is its name, which can be shown inside the icon or near it. A name alone is obviously not sufficient to define an adequate ORM linkage. A possible BPMN-compliant supplement would be the use of a `Text Annotation` linked to the `Data Store`, which could be used to add arbitrary text to a BPMN diagram. `Text Annotations` have no significant limitations or format requirements, and so a convention could be established for describing the linkages between `Activities` and `Data Stores` in a way that precisely locates the relevant areas of an associated ORM model. However, this would add considerable clutter to the BPMN diagram.

This exhausts the graphical options in BPMN, but a `Data Association` also has attributes that are not displayed on BPMN diagrams. One of these is “assignment”, which identifies one or more data elements involved in the transfer from source to target. Potentially, this provides a point at which references to an ORM model could be stored, but these would only be visible in the BPMN tool being used to manage the process model and not to anyone viewing the graphical representation of the process from a business perspective. Such attributes are intended to facilitate process automation and have little relevance to modeling at a conceptual level.
