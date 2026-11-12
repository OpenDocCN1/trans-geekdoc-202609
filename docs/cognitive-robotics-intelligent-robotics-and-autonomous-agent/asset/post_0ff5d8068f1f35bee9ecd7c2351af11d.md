
## KnowRob 2.0

NEEMs (episodic memory)

Giskard action executive

COGITO Metacognition

Introspection Self-programming

What, why, how? Answer

Plan executive

Generalized action plan
Contextualize action designator
Motion plan

Body motion query
Motion specifications

RoboSherlock perception executive

Figure 10.2
The CRAM cognitive architecture. Source: Courtesy of the EASE interdisciplinary research center at the University of Bremen, Germany.

the development of CRAM over the past ten years, a small subset of which includes Winkler et al. (2012), Tenorth and Beetz (2013), Beetz et al. (2015), and Kunze and Beetz (2017).

The CRAM Plan Language (CPL) executive is an extension of the Lisp programming language. It represents all the key aspects of a plan as persistent first-class objects in first-order logic. Thus, CRAM can reason about its plans, even at runtime. This is particularly relevant in the metacognition system. Plans specify how the robot should respond to sensory events, changes in belief states, and detected failures in plans. All these aspects of a plan can be queried, inspected, and reasoned about. A plan comprises a set of abstract plan designators for actions, objects, locations, and motions—that is, elementary movements. Designators are effectively placeholders and require runtime resolution based on the current context of the task action. Designator resolution is accomplished either by querying a priori knowledge embedded in the plan, by querying knowledge in the KnowRob2 knowledge base, or by accessing sensorimotor data through the perception executive. All plans have a similar generic structure, as shown below. The terms prefixed with a question mark are resolved at runtime based on the current state of the robot and the environment.

```
(par
  (perform
    (desig:an action)
    (type picking-up)
    (arm ?grasping-arm)
    (grasp left-side)
    (object ?perceived-object) ))
  ...
)
```

The KnowRob knowledge base is a knowledge representation and reasoning framework for robotic agents (cf. chapter 21). It is implemented in Prolog, and it is exposed as a conventional first-order time interval logic knowledge base. However, many logic expressions are constructed on demand from sensorimotor data computed in real time. It provides the background common sense intuitive-physics knowledge required by the CPL executive to implement its goal-directed underdetermined task plans—for example, how to grasp an object, depending on the object’s shape, weight, softness, and other properties; how it must be held while moving it—for example, upright to avoid spilling its contents; and where the object is normally located. Some knowledge is specified a priori, some is derived from experience, and some is the result of the simulated execution of candidate actions using a high-fidelity virtual reality physics engine simulator. All knowledge is represented by a first-order time interval logic expression and reasoned about, as needed.

KnowRob2 comprises five core elements embedded in a hybrid (i.e., multimodalism) reasoning shell, exposed through a logic-based language layer to an interface shell that provides perception, question answering, experience acquisition, and knowledge learning. The five elements are:
- a central set of knowledge ontologies and axiomatizations;
- an episodic memory knowledge base encapsulating the robot’s experiences, represented in both subsymbolic form and in generalized symbolic form;
- an inner-world knowledge base and virtual reality physics engine simulator;
- a logic knowledge base with abstracted symbolic sensor and action data, logical axioms, and inference rules; and
- a virtual knowledge base comprising a set of data structures for parameterized motion control and path planning.

The knowledge ontologies and associated axiomatizations provide structured representation of the knowledge about the robot and its environment. There is a core ontology and additional special-purpose, application-specific ontologies. The core ontology defines the robot configuration, object configurations, robot actions, tasks, activities and behaviors, environment configuration, and situational context. The axioms identify roles that objects can play—for example, a mug is a cylindrical vessel, with a handle, that can be used as a receptacle from which its contents can be drunk, mixed, or poured.

One of the main distinguishing aspects of KnowRob2 is its focus on episodic memory. This is an autobiographical memory of the robot’s experience as it had carried out tasks in the past. These are organized as NEEMS—narrative-enabled episodic memories—a concept introduced by the KnowRob2 designers. A NEEM comprises an experience and a narrative. The experience is a detailed low-level recording of a certain episode, such as records of poses and percepts based on exteroceptive and proprioceptive sensory data. It also includes control signals. This is unusual because motor aspects of memory are normally stored in procedural memory. Thus, CRAM episodic memory, and NEEMS in particular, generalizes the concept of an episode to include procedural elements. The narrative is an abstract symbolic description of the tasks, the context, the intended goals, and the observed effects (Beetz et al. 2018). KnowRob2 episodic memory, in representing procedural knowledge as declarative knowledge, allows it to be reasoned about. The episodic knowledge base provides the basis for answers to queries such as what actions were performed by the robot, when it performed them, how it performed them, why they were performed, whether or not they were successful, what the robot perceived while performing them, and what the robot believed when it performed them. The extraction of the generalized symbolic knowledge from NEEMS is facilitated by an interface to the Weka machine-learning framework (Holmes, Donkin, and Witten 1994).

The inner-world knowledge base facilitates geometric reasoning using a high-quality virtual reality system and physics engine. This allows KnowRob2 to simulate the outcome of candidate action and to establish the feasibility of that action. It provides symbolic names and properties for each entity, and it can infer background knowledge—for example, where an object is stored. The inner-world knowledge base serves two roles: as a representation of the belief state of the robot about itself and the world and as a reasoning mechanism for determining the outcome of candidate actions. Thus, it encapsulates two types of knowledge: current beliefs about robots and the world and the projected internal simulation of future states. It also acts as a learning mechanism, generating episodic memories off-line, effectively dreaming while physically inactive, and running simulations of activities with varying control parameters. These are recorded and transferred to the episodic-memory knowledge base.

The logic knowledge base provides information about the entities in the robot’s environment, including objects, object parts, object articulation models, and environments composed of objects, actions, and events. It uses an entity description language that allows partial descriptions of entities in terms of both symbolic and subsymbolic properties.

The virtual knowledge base provides computable predicates that facilitate the integration of nonsymbolic data into the reasoning process, allowing symbolic queries of non-symbolic data. This allows run-time sensorimotor states to be integrated into the knowledge base at run-time and to be used in reasoning in the same way as symbolic knowledge.

KnowRob2 provides a logic-based language interface that allows the hybrid reasoning shell to be exposed as a purely symbolic knowledge base even though internally it uses multiple symbolic and subsymbolic representations and reasoning formalisms. In this way, KnowRob2 can be treated by the CPL executive (and other systems through its OpenEASE interface; Beetz et al. 2015) as a symbolic, object-oriented query system in which entities can be retrieved by providing partial descriptions of them using the entity predicate. This allows KnowRob2 to appear as a “Siri for robots” (Beetz 2018)—that is, as a query and response oracle. Consequently, during task execution there is an ongoing dialogue between the CPL executive and KnowRob2, in which the CPL executive presents a series of under-determined queries, and KnowRob2 provides the corresponding responses, allowing the CPL executive to carry out the task using the action executive.

The action executive controls the robot by mapping parameterized actions (as requested by the CPL executive) to adaptive trajectories in real time.

Sensory information is available to the CPL executive either directly from the perception executive or indirectly through KnowRob2 by means of the virtual knowledge base and the associated computable predicates.

The metacognition subsystem allows CRAM to reason about plans and exploit transformational learning and planning to improve them in two complementary ways: by specialization using pragmatic everyday activity manifolds (PEAMs) and by generalization through metacognitive induction. This is possible because, as we noted above, the plans themselves are represented as first-class objects in first-order logic. PEAMs capture the subspace of motions necessary to carry out an action successfully by exploiting the constraints that knowledge of everyday activities and the environment bring to bear, rendering tractable by specialization the solution of problems that in their full generality are intractable. Generalization through metacognitive induction complements the PEAM solution strategy by exploring patterns among actions plans, seeking ways to transform them either by carrying out the action in a more efficient and effective manner or by accomplishing the outcome of the action in a different way.

## 10.6.2 ISAC

ISAC—intelligent soft arm control—is a hybrid cognitive architecture for an upper-torso humanoid robot also called ISAC (Kawamura et al. 2008). From a software engineering perspective, ISAC is constructed from an integrated collection of software agents and associated memories. Agents encapsulate all aspects of a component of the architecture, operate asynchronously (i.e., without a shared clock to keep the processing of all agents locked in step with each other), and communicate with each other by passing messages.

As shown in figure 10.3, the multiagent ISAC cognitive architecture comprises Activator Agents for motion control, Perceptual Agents, and a First-Order Response Agent (FRA) to effect reactive perception-action control. It has three memory systems: short-term memory (STM), long-term memory (LTM), and a working memory system (WMS).

STM has a robot-centered spatiotemporal memory of the perceptual events currently being experienced. This is called a Sensory EgoSphere (SES), and it is a discrete representation of what is happening around the robot, represented by a geodesic sphere indexed
