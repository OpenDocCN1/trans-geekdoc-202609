
The only direct manipulation that can be specified in an action language is the manipulation of the model elements themselves. At the time the model is compiled, the action language specification can be mapped onto the desired architecture. In principle, the same model could therefore be used in an embedded system, a web service, a distributed application, and so on.

Executable UML has been applied successfully in a variety of applications. Most of these are real-time applications that lend themselves very naturally to state-based specifications. Products are available from a small number of vendors who tend to be focused on the reactive systems market. However, there seems to be no reason why the concepts should not be equally applicable to general business systems, so the current focus may just reflect historical market positioning rather than any inherent feature of the technical approach.

## 15.6 Business Process Standards Initiatives

The late 1990s saw rising interest in supporting the automation of business activities, aimed at replacing the various ad hoc approaches that existed with a more general and systematic way of building business-focused systems. Although UML activity diagrams could be pressed into service, their primary purpose of describing object-oriented software made them less than satisfactory for expressing business concepts. As a result, the early 2000s saw several initiatives aimed at producing a standard for defining business activity.

[Table 15.3](#Ch015_773-830_B9780443237904000190.xhtml#t0020) shows a partial list of organizations active in process-related fields and the initiatives with which they were involved. These efforts were focused in three main directions.

[Table 15.3](#Ch015_773-830_B9780443237904000190.xhtml#B-t0020)

A partial list of initiatives related to process standards.

| ![t15-03-9780443237904](images/B9780443237904000190/t15-03-9780443237904.jpg) |

| --- |

**Metamodel**. Although humans typically view a process design through some form of notation, automation of the process requires the construction of a data structure and procedures that can navigate through the structure. Transferability of process designs between tools and between organizations would be facilitated by having a common metamodel to ensure consistency. A leading proposal in this area was the Business Process Definition Metamodel (`BPDM`).

**Execution**. The rapid growth of web services has led to a demand for a consistent way of expressing business processes in an executable form. The basic web protocols are stateless, but business processes may require lengthy conversations between distributed participants in a process. One way of tackling this problem is to have a specialized programming language targeted at a business process execution engine. A leading proposal in this area was the Business Process Execution Language (`BPEL`).

**Notation**. Most process models use some form of diagrammatic presentation of the process design. This typically takes the form of a flow diagram showing sequencing, branching, and so on, perhaps with some additional annotation to indicate related features such as the use of resources and organizational structure. The graphical syntax (including symbols and connection rules) varies from one notation to another. Perhaps more importantly, the semantics also vary. For example, a diamond shape may look similar in two different notations but have subtly different implications in each. A common notational standard would simplify staff training, make process designs more readily understandable, and reduce the scope for semantic variation. The leading proposal in this area was the Business Process Modeling Notation (`BPMN`) which, over time, evolved to become the mainstay of process modeling. We will return to further details of `BPMN` later.

`BPDM` was aimed at representing business process elements in a way that was independent of any specific notation or process modeling methodology. The concept of a metamodel is intended to provide a kind of vocabulary of concepts related to process modeling, with a clear definition of the meanings of the concepts and how one concept can relate to another.

`BPDM` supported two complementary views of business processes: “Orchestration” and “Choreography”. Orchestration is concerned primarily with *what* happens and *when* and is usually defined in some flow-based notation (although the notation itself was considered outside the scope of `BPDM`). Choreography describes how business entities collaborate in a process, considering that the entities may be independent and may have their own internal processes. The focus of choreography is on the responsibilities of the role players in a process and the interactions between them.

The `BPDM` Metamodel was based on the “Meta Object Facility” (`MOF`) that also underpins `UML` and some other `OMG` standards. As well as providing a baseline for concept definition, `MOF` also supports an `XML` syntax that can be used for transferring business process models between tools and between organizations. An obvious shortcoming of `BPDM` was the lack of a standard business-friendly notation, and so `BPMN` was proposed to fulfill this role.

`BPEL` aimed at extending standards for web services to add explicit support for business processes. It was conceived as a programming language using `XML` syntax. The original version, called `BPEL4WS`, was based on Microsoft’s `WSFL` and IBM’s `XLANG` approaches. The merged version was renamed `WS-BPEL`, or simply `BPEL`. `BPEL` could be applied to abstract process definition, but its main application was seen as the definition of executable business processes.

`BPEL` assumed the existence of one or more Web Service Definition Language (`WSDL`) files that define the web service interfaces. `WSDL` is a separate standard, which is used for other purposes besides support for `BPEL`.

Because of the mixed inheritance of `BPEL`, the implementer sometimes had a choice of alternative constructs that could potentially produce the same effect. In some cases, it was necessary to use the block-structured part of the language. In other cases, it is necessary to use the graph-based part of the language. Some of the semantics of the constructs were very subtle, and effects could be produced that may not have been what the process implementer intended.

One consequence of block-structured elements is that some process constructs that can be expressed in a graph-oriented approach cannot be expressed in block-structured form, and some remodeling may be required. [Fig. 15.34](#Ch015_773-830_B9780443237904000190.xhtml#f0175) shows a nonstructured process flow and one possible way in which it could be remodeled. To get to a block-structured form, any looping constructs must be arranged so that there is only one entry point into the loop and only one exit point from it. We look at process structures in more detail in [Section 15.4](#Ch015_773-830_B9780443237904000190.xhtml#s0025).

![Fig. 15.34 (a) An unstructured process. (b) A structured equivalent.](images/B9780443237904000190/f15-34-9780443237904.jpg)

[Fig. 15.34](#Ch015_773-830_B9780443237904000190.xhtml#B-f0175) (a) An unstructured process. (b) A structured equivalent.

## 15.7 Business Process Model and Notation

The original specification for the Business Process Modeling Notation was produced by `BPMI`, and, as the name suggests, was aimed directly at providing a systematic way of defining business processes in a way that would be accessible to a business community as well as technical experts. It defined a graphical syntax for drawing process diagrams in a flowchart-like style that would be easy to understand. This made it possible to validate a process description from a business perspective, something that could not be achieved with other technical languages that were proposed around the same time.
