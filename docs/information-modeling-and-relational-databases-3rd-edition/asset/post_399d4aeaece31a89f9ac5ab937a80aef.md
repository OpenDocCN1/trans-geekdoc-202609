
A final point to note is that, like activity diagrams, UML state machines have no direct representation of persistent data, so it's not possible to show if a specific database item is used, modified, or created in any specific state. The only way of finding this out is by inspection of the code for the actions in each state.

State machines are very popular with some users of UML, but most of these appear to be in application areas dominated by either real-time constraints or the need to be highly reactive to external events. In a typical business information system, time constraints are less onerous, so a processing delay is more likely to be annoying than fatal. Historically, business systems were also less concerned with being reactive. In fact, early batch processing systems could hardly be said to be reactive at all. With the increasing trend toward online processing, reactivity is becoming more important.

Anecdotal reports on the use of state machines in business applications suggest that business people find state-based descriptions less intuitive than process-based descriptions. It also seems to be true that a large proportion of the developers of business software are unfamiliar with the basic concepts of state machines. However, state machines do offer some powerful capabilities, particularly the ability to generate application code from suitably constructed models. The next section discusses one approach that relies on state modeling to provide the behavioral aspects of an executable specification.

## Executable UML

As the name suggests, executable UML is a dialect of UML that is focused on a style of modeling that results in a model that can be compiled and executed (Mellor and Balcer, 2002). It is based on a fusion of ideas from the earlier Shlaer-Mellor methodology and standard UML. An executable UML model is built around three core concepts: specifying structural aspects, such as data, using UML class diagrams; specifying dynamic behavior and control using state machine diagrams; and specifying actions using an action language.

The use of class diagrams and state diagrams is close to standard UML but with a few detailed differences. At present, UML does not define any notation or syntax for an action language, although there is a specification for the semantics that must be supported by such a language. The consequence is that each variant of Executable UML has its own language. A proposal for standardizing an action language is currently in progress within the Object Management Group (OMG).

The first stage of analysis separates different areas of concern into different domains to be modeled. A domain contains a set of cohesive concepts that can be considered without requiring detailed knowledge of other domains. Domains are interconnected by bridges that resolve intercommunications required between domains.

The assumptions made in one domain can form the requirements for another domain. For example, a business-related domain may assume the existence of a communication network with certain characteristics. These business domain assumptions contribute to the requirements for the communication network domain.

Bridges allow the separation of concerns, so, for example, the elements in a business domain can be developed and refined without considering the details of any technical domain. This also makes the system design more resilient. For instance, modification to a technical domain does not necessarily have to impact a business domain, so we could "unplug" one technical realization and "plug in" a different one without impacting the business, if we can define a suitable bridge.

The functionality required in a domain can be established in any desired way. We assume here that this is done through use case analysis. The information contained in the use case descriptions can be dissected to determine an initial set of classes. The initial class definitions will likely be extended and refined many times as the design progresses.

Associations between classes on a class diagram are handled in a slightly different way from standard UML. Each association is given a unique identifier, and the association ends are named with verb phrases instead of the noun phrases of standard UML. Classes have operations defined in the usual way. These operations typically compute and return some value, or create, delete, or modify some object (or perhaps a combination of these). Each instance of a class (i.e., an object) has a life cycle. For some classes, the behavior of their instances does not vary. An object is created, it reacts in a fixed way to any stimulus (a call to one of its operations), and eventually it goes away—not a very exciting life cycle.

Other classes have behaviors that change over time, depending on the history of events to which the object has reacted. For these classes, a state machine can be defined to model their life cycle. State machines in most implementations of Executable UML adopt a subset of the possibilities defined in the UML specification. For example, actions are typically encapsulated into procedures that are executed on entry to a state (standard UML allows other possibilities).

The procedures are defined in an action language. The language is at a higher level of abstraction than standard programming languages such as C# or Java to remove dependence on a particular software platform. Action language statements are conceptually concurrent, as decisions about how to serialize these are left to the model compiler. Similarly, such concerns as data access, persistence, distribution, and so on are not specified in the action language.

The only direct manipulation that can be specified in an action language is the manipulation of the model elements themselves. At the time the model is compiled, the action language specification can be mapped onto the desired architecture. In principle, the same model could therefore be used in an embedded system, a web service, a distributed application, and so on.

Executable UML has been applied successfully in a variety of applications. Most of these are real-time applications that lend themselves very naturally to state-based specifications. Products are available from a small number of vendors who tend to be focused on the reactive systems market. However, there seems to be no reason why the concepts should not be equally applicable to general business systems, so the current focus may just reflect historical market positioning rather than any inherent feature of the technical approach.

## 15.6 Business Process Standards Initiatives

The late 1990s saw rising interest in supporting the automation of business activities, aimed at replacing the various ad hoc approaches that existed with a more general and systematic way of building business-focused systems. Although UML activity diagrams could be pressed into service, their primary purpose of describing object-oriented software made them less than satisfactory for expressing business concepts. As a result, the early 2000s saw several initiatives aimed at producing a standard for defining business activity.

| Organization | Initiative |
|---|---|
| BEA | Process Definition for Java (PD4J)-later absorbed into BPEL |
| IBM | WSFL-later absorbed into BPEL |
| Microsoft | XLANG - later absorbed into BPEL Windows Workflow Foundation (WWF) |
| The Business Process Management Initiative (BPMI) | Business Process Modeling Notation (BPMN) (later merged with OMG - see below) |
| The Organization for the Advancement of Structured Information Standards (OASIS) | Business Process Execution Language (BPEL) |
| The Object Management Group (OMG) | Business Process Definition Metamodel (BPDM) Business Process Maturity Model (BPMM) |
| The Workflow Management Coalition (WfMC) | XML Process Definition Language (XPDL) Workflow XML protocol (Wf-XML) Workflow Application Program Interface (WAPI) The WfMC reference model for workflow |
| World Wide Web Consortium (W3C) | Web Services Choreography Description Language (WS-CDL) Web Service Choreography Interface (WSCI) Web Services Conversation Language (WSCL) Web Service Definition Language (WSDL) |

Table 15.3 shows a partial list of organizations active in process-related fields and the initiatives with which they were involved. These efforts were focused in three main directions.

Metamodel. Although humans typically view a process design through some form of notation, automation of the process requires the construction of a data structure and procedures that can navigate through the structure. Transferability of process designs between tools and between organizations would be facilitated by having a common meta-model to ensure consistency. A leading proposal in this area was the Business Process Definition Metamodel (BPDM).
