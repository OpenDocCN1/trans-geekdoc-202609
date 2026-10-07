
![](img/41fdf2aa71adfa568d36836737f447e6_26_0.png)

# Networks of 'Things'1

## 2.1 INTRODUCTION

This chapter contains an essential National Institute of Standards and Technology (NIST) standard (SP 800-183) that describes the building blocks of IoT (Voas, 2016). A standard is a document that provides the definitions needed for technologies to be built and worked together seamlessly. NIST is an organization with a central mission of promoting innovation and industrial competitiveness. Founded in 1901, NIST is a nonregulatory federal agency within the U.S. Department of Commerce. NIST innovations are based on measurement science, standards, and technology to enhance economic security and improve our quality of life.

The five primitives belonging to the Internet of Things (IoT) systems, and to most distributed systems, heterogeneity concerns, formalisms, reasoning, simulations, reliability and security risk trade-offs to be formulated and argued. These primitives apply well to systems with large amounts of data, scalability concerns, temporal concerns, and elements of unknown pedigree with nefarious intent. These primitives are the basic blocks for networks of 'things' (IoT), including the IoT. This offers an underlying and foundational understanding of IoT based on the realization that IoT involves sensing, computing, communication, and actuation. The material presented is generic to all distributed systems that employ IoT technologies (i.e., 'things' and networks).

## 2.2 NETWORKS OF 'THINGS'

From agriculture, to manufacturing, to smart homes, to healthcare, and beyond, there is value in having numerous sensory devices connected to larger infrastructures. This technology advance acknowledges the reality that human society is moving towards 'smart' and 'smarter' systems. The rapid changes in computer science, software engineering, systems engineering, networking, sensing, communication, and artificial intelligence (AI) are converging. The tethering factor is data.

There is no formal, analytic, or even descriptive set of the building blocks that govern the operation, trustworthiness, and life cycle of IoT. A composability model and vocabulary that defines principles common to most, if not networks of things, is needed to address the question: “what is the science, if any, understanding IoT?” NIST SP 800-183 offers an underlying and foundational science to IoT based on a belief that IoT involves sensing, computing, communication, and actuation.

Two acronyms will be used in this chapter, IoT and NoT, extensively and interchangeably – the relationship between NoT and IoT is subtle. IoT is an instantiation of a NoT, more specifically, IoT has its 'things' tethered to the Internet. An different type of NoT could be a local area network (LAN), with none of its 'things' connected to the Internet. Social media networks, sensor networks, and the Industrial Internet are all variants of NoTs. This differentiation in terminology provides ease in rating out cases from varying vertical and quality domains (e.g., transportation, medical, financial, agricultural, safety-critical, security-critical, performance-critical, high assurance, to name a few). That is useful since there is no singular IoT, and it is meaningless to speak of one IoT to another.

Primitives are building blocks that offer the possibility of an answer to the aforementioned questions and statements by allowing comparisons between NoTs. We use the term 'primitive' to represent smaller pieces from which larger blocks or systems can be built. In software coding, primitives typically include the arithmetic and logical operations (plus, minus, and, or etc.). In this document, we do not employ the restriction that primitives cannot be developed or derived from something else; this is a common, paraphrased definition for 'primitive', but it is not employed here.

This model does not specify a definition for what is or not a 'thing'. Instead, consider that each primitive injects a behavior representing that 'thing' into a NoT's workflow and dataflow. 'Things' occur in physical or virtual space. In physical space, consider humans, vehicles, residences, computers, switches, routers, smart device, networks, office buildings, etc. In virtual space, consider social media threads, files, data streams, virtual machines, virtual networks, etc. More considering 'things' are presented later in this chapter.

Primitives offer a unifying vocabulary that allows composition and information exchange among differently positioned networks. They offer clarity regarding concerns that are subtle, including interoperability, composability, and continuously binding assets that come and go on the fly. Because no simple, actionable, and universally accepted definition for IoT exists, the model and vocabulary proposed here reveals underlying foundations of the IoT, i.e., they expose the ingredients that can express how the IoT behaves, without defining IoT. This offers insights into issues specific to trust.

Further, we may general definition for a distributed system: a software system in which components located on networked computers communicate and coordinate their actions by passing messages. The components interact with each other in order to achieve a common goal. NoTs satisfy this definition. Thus, we consider IoT to be one of type a NoT and to be one type of a distributed system.

## 2.3 THE PRIMITIVES

The primitives of a NoT are (1) sensor, (2) aggregator, (3) communication channel, (4) external utility (eUtility), and (5) decision trigger. There may be NoTs that do not contain all of these, but that will be rare.

Each primitive, along with its definition, assumptions, properties, and role, is presented. We employ a dataflow model, captured as a sequence of four figures in this document, to illustrate how primitives, when composed in a certain manner, could impact a confidence in trustworthiness of NoTs. Although this model may seem overly abstract at first glance, its simplicity offers a certain elegance by not overcomplicating IoT's small handful of building blocks.

### 2.3.1 PRIMITIVE #1: Sensor

A sensor is an electronic utility that measures physical properties such as temperature, acceleration, weight, sound, location, presence, and identity. All sensors employ mechanical, electrical, chemical, optical, or other effects at an interface to a controlled process or environment. Basic properties, assumptions, recommendations, and general statements about sensor include the following:

- Sensors are physical; some may have an Internet access capability.
- Sensor output data: in our writings, $s_1 \to d_1$ means produced a piece of data that is numbered 1. Likewise, $s_2 \to d_2$ means sensor 2 has produced a piece of data that is numbered 2. $(d_1, d_2, d_3, ... d_4$ will be literally data). Analog sensors such as microphones and voters are counterexamples.
- Sensor may also transmit device information, such as via Radio Frequency Identification (RFID).
- Sensors may have identity or the identity of the 'thing' to which they are attached.
- Sensors may have little or no software functionality and computing power; more advanced sensors may have software functionality and computing power.
- Sensors may be heterogeneous, from different manufacturers, and collect data, with varying levels of data integrity.
- Sensors may be associated with fixed geographic locations or may be mobile.
- Sensors may provide surveillance. Cameras and microphones are sensors.
- Sensors may have an owner(s) who will have control of the data sensors, who is allowed to access it, and when.
- Sensors will have pedigree — geographic locations of origin and manufacturers. Pedigree may be cheap, disposable, and susceptible to wear over time.
- There may be differences in sensor security, safety, and reliability, e.g., between consumer grade, military grade, and industrial grade.

^1 This chapter was contributed by Jeffrey Voas.

DOI: 10.1201/9781003027799-2
