F. Baiardi et al. / Security and Resilience for a.i.o Ship

98, that is each ring in the chain, increases the privileges and enables the execution of further attacks until the attacker acquires all those in one of its goals, while the system model describes the target system modules, its vulnerabilities, and the corresponding attacks, the digital twin of an attacker describes its goal of how it selects the attacks in its chains. The module vulnerabilities determine which interactions may occur among the target system and the attackers. Harpex represents users of the target system as attackers can attack through social engineering to acquire their privileges.

The modular descriptions of, respectively, the system and the attackers enable Harpex to derive statistics and probabilities to support an assessment starting from simpler and measurable factors. For example, we can estimate the success probability of each element of the chain, a single attack, more easily than the success probability of the whole chain. Harpex preserves the overall complexity in the joint evolution of the models of, respectively, the target system and the attackers. Rather than describing this evolution, Harpex adopts a Monte Carlo approach that repeats the evolution several times to collect data to compute statistics of interest. This overcomes limitations of risk assessment strategies based on a system independent ranking of vulnerabilities [9].

The adoption of a Monte Carlo approach results in larger freedom for defining the complexity of the models of the system and of each agent. As example, a vulnerability may depend upon errors or faults of some entity and the model may simulate their occurrences according to the corresponding probability distributions. Furthermore, the model may describe all the attacker actions, such as those to collect information about the modules of the target system to discover their vulnerabilities.

The assessment can freely choose the complexity of the various models to cover all the aspects of interest. In general, an assessment selects the model complexity according to both the level of details and the computing power that is available to simulate the joint evolution of the target system and its attackers.

# 3.2 The Harpex Platform

To support the proposed methodology and the corresponding Monte Carlo approach, we have developed the Harpex platform, an integrated suite of tools that supports the building and the interactive execution of the models. The main platform tools are

+   * the builders that collect information to define the various models,
* the engine that interact executes these models and the Monte Carlo method to produce an assessment database,
* the manager that uses the assessment database to select from a catalog the countermeasures to deploy to minimize ICT risk.

The assessment database includes information about the attack chains that the attackers have executed in the simulations of the Monte Carlo method. The database is an accurate statistical sample of the attack chain the attacker can select and implement. The platform returns static countermeasures to deploy to manage the risk. A static countermeasure updates the target system in a permanent way to minimize risk. However, the assessment database is one of the inputs of Harpex CAT, a security information event platform that monitors in real-time the attacks against the target