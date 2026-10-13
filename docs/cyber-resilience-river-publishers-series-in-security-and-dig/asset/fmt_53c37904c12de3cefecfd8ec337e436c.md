
# Robotics Development and Cyber Resilience

Robotics development is influenced by such technologies as augmented and virtual reality (`AR/VR`). Here, `AR` can be used, for example, to see how robots will look and work indoors, as well as to set up and repair with a contextual hint to the service technician. `VR` can be used as a simulator, for example, paired with machine learning, in order to practice the robot control not in a costly physical environment, but in a cheaper virtual one. Robots are already integrated with the Internet of Things and additive technologies in the context of creating "factories of the future". At the same time, the cyber security importance cannot be overestimated when robots are introduced into life-critical and mission-critical processes.

Thus, the modern robots are some physical models of living organisms, designed to carry out a number of industrial and other operations as per a predetermined algorithm in accordance with changes in environmental parameters.

There are three robot generations:

*   With program control,
*   With the feedback presence,
*   Integral robots.

Within the framework of which there are the following types of robots: production (for example, a robot-manipulator), transport (delivery robot), accompanying (a robot-consultant), research (robot-laboratory), specialized (delivery drones, collection robot, robotic security guards) and etc. Currently, there are about `50` robot manipulator types, more than `200` unmanned aerial vehicle (drones) types, more than `80` android types, more than `1000` dual-purpose robots, etc. in the world.

`Industry 4.0` has demanded from robots a number of abilities that exceed human ones, namely:

*   Fast self-development and evolution through deep self-learning, semantic understanding and generating new knowledge about the subject area based on models and methods of artificial intelligence;
*   Autonomous behavior and independent decision-making based on the complex integration of the macro- and microenvironment factors and parameters variety,
*   Group behavior support and integration into a mixed hybrid environment based on group unions of robots and humans.

According to world robot statistics, the global market for robotization is more than `75 billion`. At the same time, the annual world sale growth of industrial robots amounts to `15%`, and in quantitative terms up to `400 thousand` robots per year.

What is waiting us in 10–15 years? According to experts, there comes a new era of so-called *cyborgization and hybridization*, as the next robotization stages [34, 132, 133]. Multirobot systems will learn to make decisions and respond to changing environmental conditions, including in the under destructive intruder cyber-attacks. Man will become part of the robotic, and later – the hybrid world. It is the direction where research and development, creative team `R&D` from world technologically developed countries, primarily `Japan, the USA, South Korea, China, Germany, and Russia`, are conducted.

## 1.3.3 Mathematical Formulation of the Cyber Resilience Control Problem

We introduce the following concepts:

*   Cyber system,
*   Cyber system behavior;
*   Cyber system mission;
*   Cyber system behavior disturbance;
*   Cyber system state.

These concepts are among the primary [15, [261](#Reference.xhtml#ref0265)–[263](#Reference.xhtml#ref0267)], undefined concepts and are used in the following sense.

### Primary concepts

A **cyber system** is understood as a certain set of hardware and software components of a critically important information infrastructure with communications on control and data between them, designed to perform the required functions.

The **cyber system behaviour** is understood as some algorithm introduction and implementation for the system functioning in time. At the same time, the targeted corrective actions are allowed ensuring the system behaviour cyber resilience.

The **cyber system mission** is called the mission; corrective measures are cyber disturbance detection and neutralization. In other words, a cyber system is designed for a specific purpose and may have some protective mechanism, customizable or adjustable means to ensure cyber resilience [15, [16](#Reference.xhtml#ref0016), 34, 150, [264](#Reference.xhtml#ref0268)].

A **cyber system behaviour disturbance** is a single or multiple acts of an external or internal destructive impact of the internal and/or external environment on the system.

The disturbance leads to a change in the cyber system functioning parameters, prevents or makes the system purpose difficult.

#### A disturbance combination forms a disturbance set

The **cyber system state** is a certain set of numerical parameter characteristics of the system functioning in space.

The numerical process characteristics depend on the functioning conditions of the cyber system, disturbances and corrective actions to detect and neutralize the disturbances and, in general, from the time.

The set of all corrective actions for detecting and neutralizing disturbances is called the **corrective action set**; the set of all digital platform behaviour system states is called the **state set**.

Thus, we will assume that without disturbances, as well as the corrective measures for the disturbance detection and neutralization, the cyber system is in an operational state, and meets some intended purpose [34].

As a disturbance result, the cyber system transits into a new state, this may not meet its intended purpose.

In such cases, the two main tasks appear:

1.  Detection of the disturbance fact and, possibly, changes made to the normal cyber system functioning process;
2.  Setting the optimal (cyber-resilient) in a certain sense (based on a given priority functional) organization of the cyber-system behaviour to bring the cyber system to an operating state (including redesigning and/or restarting the system, if this solution is considered the best).

On the basis of the introduced concepts, we will reveal the content of elementary, complex, and disturbed calculations in terms of **dynamic R.E. Kalman interrelationships** [34, [265](#Reference.xhtml#ref0269), [266](#Reference.xhtml#ref0270)].

### Disturbed machine computation

Further, we will use the term "elementary cyber system behaviour", considering the structure, which input receives some input value at certain points in time and from which some output value is derived at certain points in time. The above concept of the elementary cyber system behavior as a system `Σ` includes an auxiliary time point set `T`. At each time point `t` ∈ `T`, the system `Σ` receives some input value `u(t)` and generates some output value `y(t)`. In this case, the input variable values arc selected from some fixed set `U`, i.e. at any time moment `t`, the symbol `u(t)` belongs to `U`. The system input value segment is a function of the form `ω`: (`t1`, `t2`) → `U` and belongs to some class `Ω`. The output variable value `y(t)` belongs to some fixed set `Y`. The output values segment represents a function of the form `γ`:(`t2`, `t3`) → `Y`.

The **complex cyber system behaviour** is understood as a generalized structure, the components of which are elementary given system behaviours with communications on control and data among themselves [22, 132, 133, 183].
