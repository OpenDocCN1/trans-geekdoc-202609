
## Multi-Agent Paradigm for B2C-Ecommerce

- Usually, this consists of three dimensions of trust: intellect (compatible with ability), morality (integrity and honesty), and goodwill (benignancy) [13,79].

Rotter also described trust as “a belief maintained by an individual or group that it is possible to depend on the world, pledge, verbal or in written declaration of another individual or group.” Again, trust is characterized as a perception specific expectation that defines actions.

Zucker described trust as collection of mutual social expectations that are central to social activity and to determine, encouraging people to respond to each other without defining contractual information [41]. Similarly, Korsgaard et al. asserted that trust is the confidence that group members have in their leader's goodwill and loyalty (that is integrity and benignity), Hart and Saunders described trust as the faith that another party will act as planned, coupled with expectations of the goodwill of the other party. This trust is made up of a sense of the integrity of the partners, transparency (willingness not to hide information), care (not taking undue advantage) and dependability [29,38,40].

McAllister described trust as the degree to which an individual is assured of, and able to act on the basis of, another's terms, conduct, and choices, “that is a belief-based behavioural purpose” Kumar, Ramwami et al. describe reliability based on procedural rules and perceptions-facing in the management of a relationship, and distributive justice as the presumed fairness.

Rousseau et al. described that belief deals with the desire to recognize based on optimistic assumptions of another's actions or conduct. Rousseau et al. also acknowledged, along with Lewis and Weigert, trust varies considering the history and essence of the agreement between the parties [64,65].

Dwyer et al. characterizes trust as a collection of values related to interchange in a partner’s capacity and desire to participate in the social exchange. Moorman et al. characterized trust as faith in the dependability and morality of another person as “a desire to rely on an exchange partner in whom one has faith.” Morgan and Hunt describe trust as a desire to rely on one another, based on values or perceptions derived from the knowledge, reliability and benignity of the partner. In the sense of e-commerce, Gefan (2002) describes trust as a single dimension construct constructed with a customer's evaluation that the supplier is reliable, based on Luhmann's (2006) concept of trust as a process that reduces social complexity and contributes to a readiness to a supplier. This willingness is extracted from the assumption that its responsibilities would be fulfilled by the seller [42,61].

**Reputation:** Reputation is perceived on the basis of consumer trust ratings [56,75]. The reputation of Histos [56,75] is based on customer witness details; the broker and third-party agent's most recent experience with the agent is based. Thus, the value of reputation of any user is a worldwide measure that is exchanged by all observers [72].

### 3.2.3 MAS Communication

Agents are basically a kind of shared code procedure and, therefore, agree with the classic concept of a two-part distributed computing model: elements and connectors. Consumers, suppliers and facilitators of contact messages that are shared through connectors are components.

### 3.2.4 FOUNDATION FOR INTELLIGENT PHYSICAL AGENTS (FIPA)

FIPA is a global non-profit community of businesses and establishments that share the initiative to develop standardized agent technology requirements. FIPA is designed not only as a single-application technology

The following set of principles is at the centre of FIPA ():

- 1. Agent innovations have a modern framework for addressing old problems and new ones.
- 2. A large degree of maturity has been achieved by technologies of agent.
- 3. Standardization is necessary for certain agent technology to be of use.
- 4. It has been shown that standardization of generic technology is feasible and that other standardization for agent produces successful outcomes.
- 5. It is not a priority to standardize the internal mechanics of the agents themselves, but rather the framework and language needed for accessible coordination.

The communication of agents in FIPA is focused on the passing of messages, where agents interact by formulating and sending each other messages. By setting forth the encoding, grammar and pragmatics of the texts, the FIPA ACL defines a basic message language. A specific method for the internal transport of messages is not laid out in the standard. Instead, FIPA specifies that messages transported between platforms should be encoded in a textual format, because different agents may operate on different platforms and use different networking technologies. The agent is believed to have some way to convey this kind. The ACL syntax is very similar to the commonly used language KQML. However, there are fundamental differences between ACL and KQML, considering syntactic resemblance, the amass the presence of a formal semantics for ACL that can eradicate complexity and uncertainty from the use of the language. Through defining contact protocols, the specification facilitates typical types of inert-agent conversations, which are patterns of messages shared by two or more agents. These protocols vary by basic query-request methods to better know negotiation method for contracts and auctions in English and Dutch. Other elements, including agent-software integration, agent agility and protection, ontology service, and human-agent communication, are defined in other sections of the FIPA standard. Even so, they have not been taken into account in the implementation of JADE [60,67].

FIPA reference model is given in Figure 3.1.

FIPA-compliant Agent Framework comprises the DF (Directory Facilitator), ACL (Agent Contact Channel) and the AMS (Agent Management System). These agents are all enabled synchronously at the start-up of the agent platform. It is possible to break the agent platform into many hosts (where the firewall is absent between them). In order to implement multi-domain applications, a set of FIPA-compliant (Directory Facilitator) DFs can be initiated at runtime.

### Multi-Agent Paradigm for B2C-Ecommerce

![](img/9665bc5b38d724f414c78dda7410a_63.png)

FIGURE 3.1 FIPA reference model.

### Agent Communication Channel (ACC)

The ACC is an agency that offers a service on an agent platform directly to the agents. In order to carry out its message transport tasks; the ACC can access information provided by other platform services such as AMS and DF.

### Agent Management System (AMS)

For each Agent platform, the agent is eccentric and obligatory. It monitors and handles the agent platform and activities of agents. In other words, it handles an agent’s enrolment and revocation into its portal. In addition, the white-pages service is another significant service that the AMS offers to the agent community. It is a list of registered agents on the AP who are recognized by their GUID (Global Unique Identifier: the identifier which uniquely locates the agent inside the community). In order to obtain information about platform users, any agent may inquire the AMS.

### Directory Facilitator (DF)

A DF agent helps others agents with the yellow pages service. This is helpful in acquiring details the different services including the agents that provide them. An agent domain is created by all agents registered at a given DF. A separate agent domain is handled by each DF.

### Performatives of FIPA

Performative is defined as the form of the communicative act of message. Using FIPA ACL messages, agent communication is implemented. As given in the Table 3.2, FIPA used the following performative messages. SUBSCRIBE messages are the ones used by buyer and seller agents. INFORM messages are used to reply to the REQUEST or SUBSCRIBE texts. FAILURE messages are being used by the buyer agents to provide information about the failed outcome of a negotiation to the seller agent or broker. Ultimately negotiating agents use CFP, PROPOSE, ACCEPTPROPOSAL, REJECT-PROPOSAL and REFUSE messages. The variety of communication acts of FIPA (performatives) are listed below.
