
representations and reflect about itself, its inferences, and its capabilities. Weyhrauch (1995) discusses the relationships between FOL and consciousness in artifacts. The original implementation of FOL is still available in LISP (see link in the list of additional resources).

An early attempt to model consciousness by considering different levels of representation is in Johnson-Laird (1983). In the well-known book on mental models, Johnson-Laird discusses consciousness as the “operating system” of the mind. Several unconscious distributed processes run in the brain, and consciousness acts as the central control system of the mind, a sort of operating system. According to this view, the content of consciousness is made up of the value parameters of the central control system.

Minsky (2006) described a multiagent system based on several interacting agents at different levels, in which the tasks of higher-level agents are self-reflection and self-consciousness (figure 23.3). In detail, Minsky proposed different levels of agents, in which each level reflects on and critiques the levels beneath.

The first levels of the system are related to agents devoted to instinctive reflexes and learned reactions. The middle level is relevant to deliberation—that is, to the prediction-planning capabilities of the system. The higher levels are related to reflection, self-reflection, and self-consciousness. In particular, the reflection level is related to the ability to criticize the deliberative techniques adopted in the previous level; the self-reflection level is associated with

![](img/3dbcfad67b8516752e436bc9e574de5a_467_0.png)

**Figure 23.3**
An outline of the multiagent system proposed by Minsky (2006).

the ability to generate critiques of the deficiencies and the weaknesses in the knowledge and methods employed by the system.

The higher level of the system is related to self-consciousness—that is, the ability to reflect on what others may think of the capabilities and performances of the system itself. A first attempt to implement the scheme proposed by Minsky in a simulated world was described by Singh and Minsky (2005).

Sloman and Chrisley (2003) followed a similar approach in the design of the H-CogAff architecture. H-CogAff is a framework architecture based on three primary levels related to reactive mechanisms, deliberative reasoning, and metamangement—that is, reflective processes. The proposed framework prescribes different types of information, forms of representation, uses of data and types of mechanism for each level, and ways to put them together in the architecture. The SimAgent Toolkit is a freely available implementation in the Poplog framework.

McDermott (2001) made a distinction between normal access to the output of a computational module and introspective access to the same module. The first concerns the output related to the processing algorithms of the module. The second is related to the higher-order access within the processing of the module according to the self-model. He discussed the relationships between higher-order access and phenomenology in the line of higher-order theories of consciousness (see, e.g., Carruthers 1996).

McCarthy (1995) stressed the idea that a robot needs the ability to observe its mental states. He proposed a logic formalism to deal with aspects of self-reflection that could make robots conscious of their mental states. In detail, he presented the “mental situation calculus,” an extension of the situation calculus formalism aimed at modeling introspective actions in robots.

According to the classic version of situation calculus (see, e.g., Reiter 2001), the evolution of a state of affairs in the world is modeled by a sequence of situations S0, S1, S2, ... Sn. The world changes when an instantaneous action a is performed. A new situation Si is the result of the application of action a to the old situation Si−1; then Si = Result(a, Si−1). In the situation calculus formalism, the truth value of a proposition p depends on the considered situation. Then the formula Holds(p, Si) means that p is true in the situation Si.

Let us consider the situation Si where the robot knows the proposition p—for example, the color of the object A. The formula Holds(Know(Color(A)), Si) formalizes the fact that the robot knows the color of A. The situation in which the robot infers by introspection that it does not know the color of A is formalized by the formula Holds(Know(Not(Know(Color(A)))), Si). In this case, the robot knows that it does not know the color of A. Then, because of this fact, the robot may start some actions to learn the color of A.

The mental state of the robot may evolve because of learning actions. Let us consider the previous mental situation Sn, in which the robot does not know the color of A. As an effect of teaching activities, the robot may learn the color of A. Then its mental state evolves to a new situation: Si+1 = Result(Learn(Color(A))), Si). The robot is in a new mental situation in which it now knows the color of A: Holds(Knows(Color(A)), Result(Learn(Color(A))), Si). Forgetting actions may be modeled similarly.

The mental situation calculus wants to capture the dynamics of self-reflection so that a robot may reason about its mental states. As emerges from the previous examples, the propositions and actions are mental, and the situations are the mental states of the robot.

In summary, the mental situation calculus is aimed at capturing the dynamic evolution of robot mental states.

Chellat et al. (2008) proposed a cognitive architecture for a robot with introspective capabilities, organized in three computational areas. The subconceptual area is concerned with the low-level processing of perceptual data coming from the sensors. In the linguistic area, representation and processing are based on a logic formalism. In the conceptual area, the data coming from the subconceptual area are organized in conceptual categories.

Robot self-consciousness is based on the higher-order perception of the robot, in the sense that the first-order perception of the robot is the immediate perception of the environment, while higher-order perception is the perception of the inner world of the robot.

The described cognitive architecture has been tested on the board of a moving robot performing guided tours at the Archaeological Museum of Agrigento, Italy.

## 23.6 Global Workspace Theory

The global workspace theory (GWT) was proposed by Baars (see, e.g., Baars 1997) as the unification of different processes in the cortex. The GWT is tightly related to the global neuronal theory discussed by Dehaene et al. (2003). Baars observed that the brain could perform an enormous amount of unconscious parallel processing, while consciousness is serial and of limited capacity.

The GWT is based on assumptions that the brain is a collection of many specialized processors. Consciousness is associated with a global workspace whose contents “broadcast” to the processors. The processors work in parallel, and they compete to gain access to the global workspace (figure 23.4, left).

At some point, one processor wins the competition, and it gains access to the global workspace. Then it enters into consciousness and broadcasts to all the other processors to recruit others and to select the corresponding action (figure 23.4, right).

![](img/3dbcfad67b8516752e436bc9e574de5a_469_0.png)

**Figure 23.4**
Global workspace theory. Left: Several unconscious processors compete to gain access to the global workspace. Right: The winning processor gains access to the global workspace—that is, to consciousness—and it recruits other processors.

Let us consider, for example, an agent attending an elaborate scene where there are many moving objects. According to the GWT, every moving object may be processed by an unconscious processor. All processors compete to gain access to the global workspace. Then, at some point, one processor corresponding, for example, to a ball moving toward the agent wins the competition, and it enters into consciousness. The winning processor recruits other processors to select the best action to be performed: for example, it will recruit the processors related to the motion of the arm so that the arm catches the moving ball.

Contexts shape conscious contents, and they constrain the competition of unconscious processors. Therefore, a coalition of processors may be expedited to gain access in a particular context and to recruit other processors. For example, a context related to a specific emotion may assist processors in achieving consciousness instead of other processors.

The GWT is a framework theory, and several cognitive architectures inspired by the GWT have been proposed in the literature. The main cognitive architecture is LIDA (Learning Intelligent Distributed Agent), developed by Stan Franklin and colleagues over the years (see, e.g., Franklin et al. 2014; see also chapter 10 for a general discussion of cognitive architectures).

Baars and Franklin (2009) reported on the relationships between LIDA and the GWT. An initial version of LIDA, named IDA, was built by Franklin (2003) as a dispatching system for the US Navy. The goal of IDA was to assign sailors to new billets at the end of their tours of duty. These assignments were performed by detailers, and IDA completely automated the roles of detailers. Interaction with sailors was performed by email in natural language, and IDA was able to negotiate the new billets with sailors and to write orders to them.

An overview of LIDA is shown in figure 23.5. Several processors based on different technologies were implemented in the architecture, such as neural networks, sparse distributed memories, schema mechanisms, behavior networks, and subsumption architectures. LIDA performs several aspects of the GWT, like perception, attention, episodic and declarative memories, the global workspace, and the selection of actions.

The cognitive cycle of LIDA is based on the following steps:

- The system perceives an entity, giving rise to a percept.
- The percept is sent to a preconscious buffer, where the percept gives rise to local associations.
- The percept competes for consciousness.
- If the percept wins the competition, then it broadcasts to all the other processors to recruit for resources.
- An action is selected according to the goal context hierarchy.
- Once the action is selected, then the action is executed, and the cognitive cycle restarts.

The chosen action may be performed immediately, or it may be sent back to the perceptual system for further examinations.

The LIDA architecture presents learning capabilities through the feedback generated by the global workspace. The feedback signals are sent to the unconscious modules, and they provide the basis of the reinforcement- and associative-learning processes of the architecture. The Lidapy framework is a freely available recent implementation of LIDA in Python (see link in additional resource list).
