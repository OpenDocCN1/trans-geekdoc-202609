
The following occurs if the subjects from which the higher layer subject receives messages and to which it sends messages have not been refined themselves: for each incoming message of the higher layer subject from a nonrefined subject, one refining subject on the corresponding lower layer needs to be selected, which also receives the exact same message (the sender remains the same), creating the incoming link between SID layers. Similarly, for each outgoing message of a higher layer subject to a nonrefined subject, a refining subject on the corresponding lower layer needs to be chosen, which also sends the exact same message (the receiver remains the same), creating the outgoing link between SID layers. This means that the role of the refining subject in the process flow can now be entirely replaced by the refining subjects of the lower layer, while still adhering to the original message flows.

In case that the subject from which a higher-level subject receives a message (both on the same SID layer) has already been refined itself, the message in question can be received from the corresponding refining subject of the lower-level subject. The same can also be done if a receiving subject on the same layer as the higher-level subject that should be refined has already been refined previously. The application of the presented refinement rules is illustrated in Figures 13.2 and 13.3 for different constellations of subjects across layers.

Since the process-based approach is based on executing behavior diagrams (SBDs) refined from interaction diagrams (SIDs), once all subjects of a higher SID layer have been refined, there are no message links left between the higher layer and the lower layer. If all refined subjects of the lower layer are detailed in terms of SBDs, then the lower-level model can be put into operation and the higher-level model is not needed for execution. However, the refinement hierarchy allows stakeholders to understand the design, both, in terms of the behavior specified on the refinement layers for engineering (i.e., DT operation), and their relation to value-chain processes – all subjects that are not leaf subjects can be represented as placeholders or intermediate subjects for later refinement.

According to the integrated design and engineering approach, SBDs of the leaf subjects on the higher layer need to send messages to the refining leaf subjects of the lower layer. This relation ensures behavior is executed correctly. It is denoted by additional (engineering) message links between layers, such as the ones depicted in Figures 13.2 and 13.3. It should be noted that with regard to refinement situations not all possible constellations between subjects of different layers were depicted, but the rules for the remaining options can be inferred from the given examples.

For the demonstration case, a model version including the SBD layers was created, to demonstrate the behavior refinement of leaf subjects. It is depicted in Figure 13.4. As can be observed from the modeled internal behavior, further possibilities for behavior refinement exist. Do-states can be split into more fine-grained actions, which could again be modeled explicitly as states. Currently, only the 'happy path' of behavior was modeled, i.e., the intended and optimal occurrence of states. In case that, e.g., the operational status report sent by the transport robot states that some of the installed sensors are not working correctly, additional behavior would be necessary. In subject-oriented languages, such as the Parallel Activity Specification Scheme, exceptional cases could be modeled through the optional guard behavior of a subject [7].

![](img/0dd4397c67b063014553965e4f1cf7e4_251_0.png)

FIGURE 13.2 Abstraction layer architecture – diversion of message flow to refining subjects. Subject that is being refined (distribution logistics center) receives messages from refined subjects on a different layer than the one that it should be refined at (VP Transporter, VP Informationsystem) and sends messages to unrefined subject (transport company).

The created models can furthermore be seen as 'containers' for other models and data, or as an embodiment of a possible structure indicating the relationships between them. Other models and data can be assigned to each of the elements in the abstract layer structure, i.e., to a state, to an SBD, to a message, to a subject, or to a layer. This way, the abstract layer architecture can be used as an integration concept for DT data. The service robot subject can, e.g., have an associated 3D model of the robot, a kinematic model, and sensor data produced by the robot.

![](img/0dd4397c67b063014553965e4f1cf7e4_252_0.png)

FIGURE 13.3 Abstraction layer architecture – diversion of message flow to refining subjects. subject that is being refined (distribution logistics center) sends messages to refined subjects on a different layer than the one that it should be refined at (TC Transporter, TC Informationsystem) and receives messages from unrefined subject (vaccine producer).

## 13.4 Discussion

In this section, we reflect on the architecture and its application presented in the previous section. We clarify design and engineering challenges that popped up in the course of application and may need further research.

Since the proposed architecture consists of one or multiple SID layers and one or multiple SBD layers, an organization dealing with various value-added processes may need further structures to organize the process diagrams. When the proposed architecture can be created for each value-chain process of an organization, communication across processes is likely to occur and some SIDs and SBDs might be needed to show the involvement of particular roles or tasks in various value chains.

![](img/0dd4397c67b063014553965e4f1cf7e4_253_0.png)

FIGURE 13.4 Abstraction layer architecture – SID layers and SBD layers containing the internal behavior of leaf subjects.

A substantial issue that needs to be addressed in the generic architecture concerns the interaction between subjects that belong to different layers of refinements. Two design and engineering topics refer to that situation:

- What happens in case the subjects from which incoming messages originate have already been refined?
- The same question occurs for subjects to which outgoing messages are sent.

In both cases, a specific level of granularity has already been achieved that is relevant for organizational and/or technical implementation. It depends on the allocation of subject carriers (humans or cyber-physical components) whether further refinements are required or not. Consistency is maintained by propagating already existing specifications to the next layer of refinement, in case the level of detail is sufficient for implementing the represented process. The items raised above relate to the challenge of multiple refinement layers and subsequent introduction of SID layers. Some guidance can be provided by the following two development principles: (1) once a SID subject has been refined to the level of a SBD, in case further refinements are needed, the existing SBD is replaced by the SBDs of the new refining subjects for execution and (2) SID refinements to a further set of SID layers correspond to the refinement of those messages already addressed on the upper SID layers.

Finally, each executable leaf subject is part of a (layered) SID and interacts with at least one other SBD. Each flow between messages between SBDs can thus be assigned to a message connecting two subjects of the SID, with these two subjects not necessarily being located on the same SID layer.

## 13.5 Conclusion

In this chapter, we have addressed layers of abstraction targeting to structure design and engineering of DTs as part of CPS. Integrating design and engineering along with digital modeling leads to challenges with respect to synchronizing digital process components as well as DTs with their physical counterparts.

Another issue concerns the required levels of granularity. A case-to-case architecture to that respect facilitates the composition and aggregation of required CPS functionalities. The proposed architecture is a first step to pragmatic DT development for CPS, taking into account the heterogeneity of components and the dynamic nature of CPS design and operation.

The presented architecture is based on two intertwined layers of abstraction, designed to tune for engineering a declarative interaction network to
