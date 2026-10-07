
# The Cognitive Engine: Artificial Intelligence for Wireless Communications

For a radio to become cognitive, we have to address many aspects in communications and computer science. We will also see how these concepts and their application to communications systems require a breadth of understanding of multiple disciplines. This makes radio design a very exciting but also a very difficult research topic to study. Our intention in this chapter is to leap directly into the core framework of cognitive radio design before pulling back the big picture in subsequent chapters to some of the fundamental areas of research.

From our definition in Chapter 1, a cognitive radio is the application of intelligent processing and adaptation to a wireless communications system. We implement this as a processing engine to translate observations about the environment to action. We call this part of the radio *cognitive engine*. In this chapter, we describe the function of a cognitive engine as well as the design of the cognitive engine we have developed. The description and development of the cognitive engine leads to a more general treatment of the use of learning techniques and artificial intelligence in wireless communications systems at the end of the chapter.

The cognitive engine (CE) is the intelligent core of the system described by Figure 1.2. Its design serves two simultaneous objectives:

- 1. Develop and apply cognitive radio algorithms;
- 2. Deploy cognitive radio functionality.

# Artificial Intelligence in Wireless Communications

![](img/7780d97a7979a9fac4a1941139511cc9_26_0.png)

**Figure 2.1** The cognition cycle with an outer loop for observation and optimization and inner loop for learning.

In particular, the actions of a cognitive radio (CR) follow the cognition cycle first proposed by Mitola [1]: observe, orient, plan, decide, learn, and act. A revision of the cognition cycle, published in a similar format in [2], is shown in Figure 2.1. This figure simplifies the actions of Mitola's loop and provides a system close to a real implementation. In a way, it is a more detailed version of the AI agent of Figure 1.2. The radio platform provides both the input to the sensors and receives controls from the actuators. The sensors are labeled here as environment observations and cover a number of domains of information useful for a cognitive radio. The sensors pass the information on the rest of the cognitive engine, which is a mixture of modeling, optimization, and learning algorithms. The outer loop contains a more straightforward synthesis of optimized waveforms while the inner loop provides long-term learning and reasoning abilities. The results of the cognitive engine are then used to control the radio by applying knobs to create new waveforms. We use the theoretical aspects of this cognition loop to develop the waveform engine architecture through this chapter.

## 2 Cognitive Radio Design

A cognitive radio is a flexible and intelligent radio capable of creating any waveform and using any protocol supported by the radio hardware and software. Waveforms consist of all of the parameters that define the way in which the radio transmits and receives information, including transmitter power, operating frequency, modulation, pulse shape, symbol rate, coding, and so forth. Protocols are the rules by which network nodes transfer information.

# The Cognitive Engine: Artificial Intelligence for Wireless Communications

A cognitive radio develops waveforms and chooses protocols in real-time using artificial intelligence. These actions require three components:

- 1. Perception: Sensors that collect data on both external factors (channel conditions, other radios, regulations, user needs) and internal factors (waveform capabilities, available computational resources, remaining battery power).
- 2. Conception: An intelligent core that learns and understands how to combine knowledge from the sensing mechanism to aid the adaptation mechanism.
- 3. Execution: An optimization and adaptation mechanism that alters the radio's behavior.

Figure 2.2 presents a generic architecture for a cognitive radio. The cognitive engine is a separate entity within that radio that works alongside the normal communications path. The engine relies on information from the user, radio, and policy domains for instructions on how to control the communication system. This structure works well as a generalized architecture as it makes no recommendations about how the cognitive engine (and therefore the rest of the cognitive radio) should behave while still mapping the interactions of the rest of the systems. The communications module appears as a simplified protocol stack, again showing the independence of the cognitive engine from the overall system.

Figure 2.2 shows three input domains that concern the cognitive radio. The user domain tells the cognitive engine performance requirements of services and applications. Service and application requirements are related to the quality of service measures of a communications system. As each application requires different QoS concepts like speed and latency, this domain sets the performance goals of the radio.

The external environment and RF channel provide environmental context to the radio's behavior. Different propagation environments cause a more complex receiver than line-of-sight propagation. Heavy multipath environment or log-normal fading require a more complex receiver. The external environment also plays a significant role in performance and adaptation. This information helps the decision-making and waveform development.

Finally, the policy domain restricts the system within regulatory boundaries. The policy environment might determine a maximum amount of power a radio can use in a given spectrum, as was done in the 700-MHz band recently auctioned by the FCC [3].

# Artificial Intelligence in Wireless Communications

![](img/7780d97a7979a9fac4a1941139511cc9_28_0.png)

Figure 2.2 Generic cognitive radio architecture that receives input from three domains and controls a system.

Important regulatory action in the United States for our purposes includes the report and order on cognitive radio [4], recent action open source software for radios [5], and the regulations on Part 15 devices for unlicensed spectrum [6]. The rules from the FCC and other regulatory bodies impose constraints on the optimization space.

## 2.2 Cognitive Engine Design

In order to better explain the operation of a cognitive engine, we now expand the discussion by introducing some specifics of our implementation.

To develop the cognitive capabilities of Figure 2.2, Figure 2.3 presents an architecture of the cognitive engine. It includes a central component called the cognitive controller that acts as the system kernel and scheduler to handle the input/output and timing of the other components. The other major components include:

- Sensors: collect radio/environmental data.
- Optimizer: given an objective and environment, create an optimized waveform.

# The Cognitive Engine: Artificial Intelligence for Wireless Communications

![](img/7780d97a7979a9fac4a1941139511cc9_29_0.png)

**Figure 2.3** The cognitive engine developed at Virginia Tech's Center for Telecommunications (CWT) (patent no. 7289972).

- Decision Maker: coordinate information and decide how to optimize and act.
- Policy Engine: enforce regulatory restrictions.
- Radio Framework: communicate with the radio platform to enable new waveforms and pull information from the sensors.
- User Interface: provide control and monitor support to the cognitive engine.

One major point of the cognitive engine is to enable the integration of other algorithms and systems. For example, one user interface being developed at the Virginia Tech (VT) Center for Telecommunications (CWT) is a public safety radio (PSCR), which is an interface and control system for the cognitive engine designed for the public safety community [7].

The number of available SDR platforms is rapidly increasing. We have personal experience and working knowledge of a few for use with
