
- Theory of mind
- Interaction dynamics
- Task and goal predictions for task switching

- Inner representations
- Model of the human
- Model of the environment

Motor action intentional and unintentional

Information

Environment

- Inner representations
- Model of the robot
- Model of the environment

- Theory of mind
- Interaction dynamics
- Goals and intentions

Figure 17.5 Human-autonomous agent interaction principles, appropriated from human-human interaction.

## 17.3.2 Principles and Characteristics of the Dynamic Decision and Action Framework

Based on predictions of the possible decisions a human agent could make (Lopez Pulgarin, Herrmann, and Leonards 2018), any DCAS should look at making decisions within a fraction of those prediction windows (e.g., one second) to then dynamically cue and actively influence the decisions of the human partner. Hence, human and autonomous agent would be able to cooperatively act within the time period of the predicted decisions and actions thereafter. The following axioms would lead to the DCAS:

- 1) The realization that we can treat the human as an “external source” or independent collaboration partner in relation to the autonomous agent instead of “in the loop.”

- 2) Learning from and adapting to the human and the signals people send in joint action situations, proxemics, and so on; learning to understand and predict adaptability within the human and their trust of the autonomous system as an autonomous, collaborative agent or partner.

- 3) Identification and subsequent learning from the “error” signals when situations go wrong. The principle of optimality of decisions and actions in human agents and control technology is an exploited commonality.

- 4) Identification and enabling of verbal and nonverbal communication channels in a human to indicate changes in “who is the leader, who is the follower” in joint action.

- 5) Subsequent “joint” cooperative, agent-based decision-making and dynamic action taking.

Overall, a coherent modeling methodology for decisions and actions would have to be developed that is deeply rooted in complementary research on human decision-making, cognition, communication, dynamic actions, dynamic decisions, and action theories in control and computer science.

This requires that agent models and their uncertainties involved in the joint decision-making process be predetermined. This includes both the human and the autonomous system. The more the autonomous system relies on principles that underlie successful human-human interaction, the easier it will be for the human to develop a theory of mind of the robot. Only an approach that allows the human to intuitively understand the “mind” of the robot and that takes into account that an agent’s own actions influence other agents’ actions and vice versa will make joint actions among intelligent autonomous systems and humans possible (King, Rowe, and Leonards 2011).

Autonomous artificial agent models take inspiration from the fact that human decision models (e.g., Bellet et al. 2009; Berkes et al. 2011) have strong similarity to discrete hybrid stochastic automata (DHSA; Bemporad and Di Cairano 2005). There is a decision-making level that is responsible for the decisions, resulting in subsequent dynamic actions at the automatic level. Hence, the decision-making level may imply a set of discrete yet uncertain decisions, each followed by an uncertain dynamic action. Decisions are carried out within a fraction of a second, while dynamic actions can extend over intervals of several seconds.

The probabilistic approach for the analysis of human decision-making based on Fiser’s sampling-based probabilistic representational framework (Haeffner, Berkes, and Fiser 2016; Fiser et al. 2010) is a possible guidance for the development of such agent models. In Fiser’s framework, both the human’s internal representation of visual, aural, and tactile events during acting as a coalition and the decision-making process in lead situations must be assessed. For the sequential character of decisions and dynamic actions, it therefore becomes necessary to explore how decisions in the present moment depend on the series of decisions made in the recent past. This leads to an assessment process of cues given to the human and the decisions made. For modeling the human decision-making process, the optimality principle following a Bayesian method can be used, such as the “cognitive tomography” method of Houlsby et al. (2013). Applied to behavioral tasks, this allows for a quantitative description of an internal representation of a human based on discrete test choices (figure 17.6). Alternatively, a machine-learning-based understanding of the decision-making model (Lopez Pulgarin, Herrmann, and Leonards 2017) could be deployed and the synergies explored in which decision probabilities determine decision costs. Though such methods resemble emergent methods in cognitive architectures, they aim at presenting their results in a clearer and more predictable manner than traditional data-driven methods.

For the lower automatic dynamic action level—that is, the dynamic action following the decision—learning-based, regressive models based on data-driven methods might be preferable to strongly physical model-based methods; they may provide a continuous integral or summative optimal cost function that the human follows. Optimal cost function models allow for a more flexible prediction of the human’s actions. This is, for example, used in inverse optimal reinforcement learning (Mombaur, Truong, and Laumond 2010). Both levels are joint via the DHSA (Bemporad and Di Cairano 2005) and exploit mechanisms like model predictive control (Morari and Lee 1999; Di Cairano et al. 2014; Rosolia, Zhang, and Borrelli 2018).

![](img/3dbcfad67b8516752e436bc9e574de5a_356_0.png)

Figure 17.6 Probabilistic internal decision model of a driver attempting to pass a car in front of them. Source: Adapted from Berkes et al. 2011.

As mentioned earlier, a joining principle in human decision, human action dynamics, and many artificially designed technological processes is *optimality*. Each decision and action can be quantitatively associated with a cost. For a robot, a part of the cost in a dynamic action can be characterized, for instance, by its distance, either to a target for target tracking or to the distance from a human for safety. For both humans and robots, their energy consumption could be included in the cost and would be expected to increase over time while remaining limited in order for it to be optimized. The optimization of energy consumption underlies many human functions, such as locomotion (e.g., Warren 2006).

In terms of decision-making, the synergetic power of cognitive-science-founded models (e.g., Fiser et al. 2010; Berkes et al. 2011; figure 17.6) and machine-learning models (e.g., Lopez Pulgarin, Herrmann, and Leonards 2017, 2018) has to be exploited. Humans develop an internal model for each perceptive decision that guarantees that the decision regarding an intended task is carried out with the highest probability of success (Fiser et al. 2010; Berkes et al. 2011) considering the uncertainty of the environment (figure 17.7). Hence, decision costs are inversely related to the probability of the decision made. Identifying not only the models and their uncertainty sources but the optimal criteria for joint action between agents is key (Fiser et al. 2010).

The cooperative decision-making process can use the set of aforementioned DHSAs within a cooperative agent-based process, using model predictive control principles, to speed up the decision process and to allow fast computation of dynamic control actions from the multiagent framework. A probabilistic decision framework would possibly enhance such a process (Turnbull et al. 2016). For this, a virtual autonomous agent (figure 17.7) can

![](img/3dbcfad67b8516752e436bc9e574de5a_357_0.png)

Figure 17.7 DCAS overview.
