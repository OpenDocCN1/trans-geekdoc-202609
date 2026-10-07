
```xml
<sensor>
  <name>psd</name>
  interface information
</sensor>
<optimizer>
  interface information
</optimizer>
<radio>
  interface information
</radio>
<user-interface>
  interface information
</user-interface>
<policy-engine>
  interface information
</policy-engine>
</cognitive-controller>
```

In this listing, each type of component is defined. Because a cognitive radio will likely have multiple input methods for gathering information, the cognitive controller can define and connect to multiple sensors. Here, the cognitive radio has a sensor to collect the PSD of the radio environment as well as a sensor that collects radio performance meters. Each is described by a specific name that the cognitive controller uses to identify the sensor when collecting information.

## 2.4 Artificial Intelligence in Wireless Communications

Successful cognitive radios are aware, can learn, and can take action for any situation that might arise. Applications range from voice communications under low power conditions to communications in high interference zones to more complex, critical, and hostile military networks of interoperating vehicles and soldiers with many different network needs. A radio must respond to these scenarios and adapt the many parameters that define their waveform and protocols. These radios do not require learning; instead, they need highly sophisticated learning and decision-making capabilities.

Machine learning has been well documented and received both criticisms [13] and praise [14]. Successful applications of AI are often limited to narrowly defined, well-bounded applications. While waveform adaptation is a bounded problem, the technical demands for intelligence in a radio exceed those normally associated with successful applications of classic intelligence techniques, such as expert systems or neural networks. Waveform optimization requires stronger reasoning capabilities and the potential to create and test new design solutions.

A common theme we will continue to develop is the combined use of both learning and optimization processes. Feedback from a learning system can augment the optimization routines through comparisons between the radio's actions and the desired outcomes of the optimization. Furthermore, as touched upon in this chapter and developed in Chapter 6, a learning system can significantly adapt decision-making in time-constrained situations. If the cognitive radio requires an immediate solution, the learning system can provide a known working solution developed in the past. Given time constraints or lack of valid solutions, the optimization process can develop new solutions or evolve old solutions for better operation.

Information and knowledge are both important concepts for a cognitive radio. Information is data about the environment collected through the available sensors. Information can include items such as position, interference, battery life, or performance analysis. The information collected from the sensors feeds both the learning and the optimization routines to help make decisions. Knowledge is a concept developed from information. Knowledge is a useful representation of the information that says something about what information means. The sensors might provide the cognitive radio with time and position information, but the radio needs to know what information might mean about potential use patterns and known problems, such as areas of service outage or high interference during a daily commute.

More information is good, but only if the cognitive engine can transform the information into usable knowledge. Some sensors might provide a lot of information such as ambient temperature, but if the models used to make decisions do not use information, the sensor adds no useful knowledge to the system. On the other hand, sophisticated sensors that provide information about interference power over a wide bandwidth can find immediate use by a cognitive radio seeking access to a particular amount of spectrum.

## 2.5 Artificial Intelligence Techniques

Below, we list several AI techniques/areas receiving considerable attention in the literature on cognitive radio. We present and review a few particularly relevant papers regarding each AI technique, specifically the papers that represent the field or provide comprehensive background them themselves.

There are a couple of well-known areas of AI techniques that we purposefully leave out. One large technique in signal processing is the Bayesian network. This powerful learning technique based on Bayes' theorem uses past experience to enhance future decisions. The reason this technique is excluded from the following discussion is because there is little published work in the use of the Bayesian networks in cognitive radio. Haykin, who has a history of work with these and other AI techniques in communications, cites the approach in his article on cognitive radar [15], but does not offer details for how to employ it. Brief discussions of Bayesian networks appear in a few publications, and they are used in other aspects of communications and signal processing, and the technique will likely start making a major impact soon.

Another popular AI technique is the expert system. Expert systems have been successful in some applications, particularly early in the development of AI, such as the DENDRAL project in organic chemistry [16]. Mitola addresses the concept of expert systems at length in his dissertation on cognitive radio [17] in which he mentions the ideas of “knowledge-engineering bottlenecks and software of limited flexibility.” The bottlenecks occur due to the need for domain experts to define all knowledge, action, and behavior of the expert system. This same principle limits any refinement of the expert system without further relying on such experts, limiting how flexible the system is to new situations and in the face of new constraints and information.

The next sections highlight different artificial intelligence techniques that use information to make knowledgeable decisions in the cognitive radio. As Arthur C. Clarke famously said, “any sufficiently advanced technology is indistinguishable from magic.” Likewise, it may be true that any sufficiently advanced signal processing algorithm is indistinguishable from artificial intelligence.

### 2.5.1 Neural Networks

Neural networks are among the oldest form of AI in computer science, starting with the mathematical formulation by McCulloch and Pitts [18]. They have come and gone as a fad over the decades, but recent advances, both hardware and software, enable them in more applications. Of particular importance to cognitive radios, neural networks provide a means for signal and modulation detection and classification.

Chan et al. [19] did some of the early published work on signal classification algorithms with decision theoretic and pattern matching. Both methods used time-based statistics, and neither proved robust under low SNR conditions. Azzzouz and Nandi did some important work on the subject [20] and did some of the early work using neural networks as the signal processing technique of choice that showed greater promise in classification of signals under noisier conditions [21]. The use of neural networks in modulation classification has since become a well-accepted technique using both time-based statistics [22] and frequency analysis [23] as the inputs to the network.

Neural networks are really signal processing elements that perform simple operations on data. However, the collection of artificial neurons and clever learning algorithms allows neurons to build and adapt to represent and process data in interesting ways. In signal classification, they take multiple noisy input and provide accurate answers to the type of modulation represented.

### 2.5.2 Hidden Markov Models (HMM)

In circles, hidden Markov models (HMM) [24] might be considered artificial intelligence, though we certainly not categorize them as such. A HMM is a processing tool that uses data to predict future actions; an implementation of Bayes' law. We discuss them here because they are useful in communications and cognitive radios.

The best reference to learn about HMMs works is Rabiner's tutorial [24]. Channel modeling has extensively used Markov models in research. Probably the most famous is the two-state Gilbert-Elliott model [25] that describes a channel as either a good state or bad. When in one state, there is a probability of staying in that state or moving to the other state. The channel properties determine the type of transition probabilities. Researchers have developed other, more extensive models, and [26] provides a good comprehensive overview of these.

The idea of developing such a model lends itself to cognitive radios. Rieser and Rondeau looked into using HMMs in channel models where they used a genetic algorithm as the training method instead of the Baum-Welch algorithm [27]. The HMM in this instance was used to provide a compact channel model based on information gathered in a system to represent the current channel states. The idea was to use the HMMs as a sensor to understand the channel behavior in a cognitive engine, although the research was not taken further in this direction.

Mohammad's work used HMMs for a similar purpose, but was able to develop classification schemes in order to use the models for decision making in a cellular network [28]. The ability he developed to calculate a similarity distance between HMMs provides promise for future implementation in a cognitive radio system, especially in the context of the environmental modeling used in a case-based system as discussed in Chapter 6.
