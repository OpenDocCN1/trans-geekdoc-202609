# Networks of ‘Things’

# 2.5.1 Open, Closed

NoTs can be open, closed, or somewhere in between. For example, an automobile can have hundreds of sensors; wired Central Processing Unit (CPUs); databases such as maps, wired communication channels through the car, and without any wireless access between any ‘thing’ in the car to the outside. This illustrates a closed NoT. Such a NoT mitigates nearly all wireless security concerns such as remotely controlling a car; however, could there still be concerns of malware and counterfeit ‘things’ that could reduce in safety. (There are issues related to wireless transmission ranges that we ignore for simplicity.) A fully open system would essentially be any ‘thing’ interoperating with any ‘thing’, any way, and at any time. From a “trustworthiness” standpoint, is impossible to assure since the NoT is unbounded.

Most NoTs will be between these extremes since a continuum will likely exist. The primitives serve as a guidepost to where reliability and security concerns require additional mitigation, e.g., testing and other technologies related to validation and verification.

# 2.5.2 Patterns

We envision a future demand for design patterns that allow larger NoTs to be built from smaller NoTs, similar to design patterns in object-oriented systems. In essence, these smaller entities are sub-NoTs. Sub-Notes could speed up IoT adoption for organizations seeking to develop IoT-based systems by having access to sub-NoT catalogues. Further, the topology of sub-NoT could impact the security and performance of composite NoTs.

# 2.5.3 Composition and Trust

To understand the inescapable trust issues associated with IoT and a specific NoT, consider the attributes of the primitives and elements shown in Table 2.1. The three rightmost columns are our best guess as to whether the pledge, reliability, or security of an element or primitive creates a trustworthiness risk. Those with question marks (?) are ones not we fully understand at this time.

The following table questions such as: what does mean for a NoT when its primitives are in continual flux due to natural phenomenon that are in continuous change and its virtual and physical entities are unknown, partially unknown, or faulty? Or if we have insecure physical systems employing faulty snapshots with incorrect assumed environments, where is the trust?

Such questions demonstrate the difficulty assuring and assessing NoT trustworthiness. We offer the following statement about NoT trustworthiness:

Trust in NoT A, at some snapshot X, is a function of NoT A’s assets {sensors(s), aggregator(s), communication channel(s), eUtility(s), decision trigger(s)} with respect to the members {geographic location, owner, environment, cost, Device_IDs, snapshot} when applicable.