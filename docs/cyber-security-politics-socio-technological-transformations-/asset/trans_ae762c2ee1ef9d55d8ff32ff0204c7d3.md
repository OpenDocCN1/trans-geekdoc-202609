
Valeriano, B., Jensen, B., and Maness, R. C. (2018). *Cyber Strategy: The Evolving* *Character of Power and Coercion*. Oxford: Oxford University Press.

Van Puyvelde, D., and Brantly, A. F. (2019). *Cybersecurity: Politics, Governance and* *Conflict in Cyberspace*. Cambridge: Polity.

Whyte, C., and Mazanec, B. (2019). *Understanding Cyber Warfare: Politics, Policy, and* *Strategy*. Abingdon: Routledge.

10.4324/9781003110224-17

`**15**`

[`**15 Understanding transnational**`](#index_split_000.html#p8)

[`**cyber attribution**`](#index_split_000.html#p8)

[`Moving from “whodunit” to who did it`](#index_split_000.html#p8)

[*Brenden Kuerbis, Farzaneh Badiei, Karl Grindal,*](#index_split_000.html#p8)

[*and Milton Mueller*](#index_split_000.html#p8)

Like the broader field of cyber security, cyber attribution is a socio-technical endeavor. Accordingly, we can expect that any transformation of cyber attribution will “be co-constituted by technological possibilities, political choices, and scientific practices” (Dunn Cavelty and Wenger 2020). This chapter examines some of the current practices of attribution, scientific developments in the field,

[and possibilities for its transnational institutionalization.1](#index_split_005.html#p249)

First, we provide some background on the role of attribution in deterrence and accountability, and the challenges of attributing, particularly to nation-state actors. We then analyze attributions made from 2016 to 2018. We characterize the actors involved and types of attributions, finding a shift toward private actor attributions and mix of approaches by states. Next, we explore some technical advances in attribution. Better algorithmic-driven attribution, seemingly possible by the collection and analysis of numerous artifacts left on networks by threat actors, could certainly help push attribution forward although it raises issues of how state and non-state actors cooperate. We also look at attempts to understand behavioral aspects of attribution, exploring one game-theoretic attempt to model when states will or will not attribute an attack to another state, and use our dataset to explore certain predictions of the model. This exercise allows us to understand more clearly which state and non-state actors make or avoid making attributions, and the institutional conditions under which their agreement on attribution might occur.

In light of the above analysis, it is unlikely that attribution made by a nation-state (or even allied states) will be accepted as neutral and authoritative by another state, especially if those states are rivals or hostile. Given political fragmentation and socio-technical uncertainty around the current practice of attribution, we review proposed models for institutionalizing transnational attribution. The initial models offered have dramatically different structures and actor participation. Recognizing the shortcomings in them and the strategic use of attribution by states, a group of university-based and independent researchers are seeking to build independent, transnational attribution capabilities grounded in scientific method. Such a collective approach, if recognized, could address credibility DOI: [10.4324/9781003110224-17](https://doi.org/10.4324/9781003110224-17)

`*Transnational cyber attribution*`

`*Transnational cyber attribution*` 221

issues and result in more stable outcomes and ultimately help with accountability.

We conclude with a brief agenda for future research.

**The role of cyber attribution in deterrence and accountability**

One can defend against a cyberattack, but without attribution, attackers lack a deterrent. At best, secure systems increase the time needed to find a vulnerability to a point beyond that which the attacker is willing to spend. Without proper incentives to restrain malicious attacker behavior, be they state or non-state, it’s unreasonable to expect the present situation to change. As a deterrent, attribution has several advantages over other responses: Unlike strategies such as hack backs, it might not result in the militarization of the internet and it might even prevent it (Dunn Cavelty 2012).

Accurate attribution requires experienced threat intelligence and digital forensics experts. While governments and threat intelligence groups will attribute attacks to specific intrusion sets, sometimes even linking these to specific actors, there is no internationally recognized forensic process with an evidentiary based level of confidence. Rather, attribution is more often than not based on limited evidence and the reputation of the attributing entity. Considering that both attributing groups and attackers could be based anywhere in the world, without a recognized standardized and institutionalized process for attribution, can we expect a global coalition to implement sanctions or otherwise deter the attacker?

There is an important distinction between identifying intrusion sets and assigning them to an adversary or “threat group” on the one hand and linking this adversary with a known state or non-state actor on the other. Robert Lee refers to the latter as “true attribution” (Lee 2016). This two-part distinction can be compared to Herb Lin’s model, developed in the article “Attribution of Malicious Cyber Incidents”, which uses three levels of attribution: Machines, human operators, and the ultimate party responsible (Lin 2016). In Mandiant’s 2013 attribution of an Advanced Persistent Threat (i.e., “APT-1”) to the China PLA Unit 612398 all three levels of Lin’s model are described (Wittes 2013). At the lowest level would be IP addresses associated with command and control (C&C) servers. Next, is attribution to a human operator; the Mandiant report identifies a persona who went by the alias “ugly gorilla”, but associated this with the real person, Wang Dong. Ultimately though, the report is attributing APT-1 to China’s People’s Liberation Army and hence the Chinese state.

Defining an ultimate responsible party can be particularly challenging when it comes to state involvement. Even when a person is clearly identified as being in the attributed country, it is not necessarily clear from the forensics whether that person was a contractor or an employee, or whether they were operating under express instructions or on their own. Jason Healey’s Spectrum of State Responsibility acknowledges that states employ hackers, contract out hacking,

`222 *B. Kuerbis, F. Badiei, K. Grindal, and M. Mueller*` encourage hacking, or permit its use within their jurisdiction, each level representing a different degree of state responsibility (Healy 2013).

**The challenge of attribution to nation-state actors**

The practice of attribution can be cumulative, grouping information from incidents to create intrusion sets. Intrusion sets are adversarial behaviors, what is sometimes abbreviated as “tactics, techniques, and procedures (TTPs)”, and technical resources with common properties from previous attacks that are grouped together (e.g., a “campaign”) and associated with a common actor (e.g., a “threat group”). This process has some general standardization by convention and predictive success, but there is no one correct method. Accordingly, SANS in 2010

noted:

There is no rule of thumb or objective threshold to inform when linked intrusions should become a campaign. The best measure is results: if a set of indicators effectively predict similar intrusions when observed in the future, then they have probably been selected properly.

(Cloppert 2010)

