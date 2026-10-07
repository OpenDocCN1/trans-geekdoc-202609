# F. Baiardi et al. / Security and Resilience for a 4.0 Ship

18, 21–23. The sector is worth trillions and has an unmatched reach across international waters, which exposes people and goods to a diverse range of factors, putting the shipping industry at high risk, however the overall complexity and the critical tasks delegated to an ICT + OT infrastructure require methodologies and tools to manage cyber risk to cover issues such as unauthorized access or malicious attacks to ships' systems and networks. Risks may also occur from personnel accessing systems on board, by introducing malware via removable media.

The safety, environmental and conceptual consequences of incident may be significant. This chapter discusses a solution based on the Harpex methodology and platform [2-4]. The Harpex platform is an integrated set of tools that adapts a scenario approach to automate risk assessment and management. Each scenario of an ICT + OT infrastructure and some intelligent attackers with some predefined goals, i.e. some local or physical resources of the infrastructure they aim to control. An attacker can reach its goals by sequentially composing the attacks to escalate its over the infrastructure. This is the only strategy to overcome the infrastructure complexity and its large number of nodes. First, the platform builds a formal model, i.e. a digital twin, of the target infrastructure that describes the infrastructure modules, its vulnerabilities, and the physical and logical topologies. The platform also builds a formal model of each attack. Using the infrastructure twin and those of the attackers, the platform applies a Monte Carlo method with multiple adversarial simulations, i.e. simulations of the attacker behaviors to reach their goals. The multiple adversarial simulations support the discovering of alternative chains and a statistical sample of these chains. The sample is the input to compute statistics to assess and manage the risk. The adoption of a model-based approach avoids any interference and noise on the target infrastructure and makes possible to repeat any number of times to evaluate the effects of any change to the infrastructure or to attackers.

This chapter is organized as follows. Sect. 2 reviews problems that risk and cyber attackers pose to a modern vessel. It also outlines the problems a risk assessment and management methodology considers. It also discusses how it supports the discovery of attack chains and their neutralization. Sect. 4 presents the results of a risk assessment in a ship still in design. Sect. 5 discusses how to increase the resilience of a 4.0 ship. Lastly, we draw some conclusions.

# 2. Cyber Risk vs Ship Security and Safety

It is well known that all onboard systems on a 4.0 vessel can be very large. As an example, these systems could include:

+   - Cargo management systems
- Bridge systems
- Propulsion and machinery management and power control systems
- Access control systems
- Passenger servicing and management systems
- Communication systems
- Guest entertainment systems