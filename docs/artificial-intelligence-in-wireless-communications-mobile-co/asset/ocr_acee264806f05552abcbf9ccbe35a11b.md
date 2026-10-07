# The Cognitive Engine: Artificial Intelligence for Wireless Communications

processing technique of choice that showed greater promise in classification of signals under noisier conditions [21]. The use of neural networks in modulation classification has since become a well-accepted technique using both time-based statistics [22] and frequency analysis [23] as the inputs to the network.

Neural networks are really signal processing elements that perform simple operations on data. However, the collection of artificial neurons and clever learning algorithms allows neurons to build and adapt to represent and process data in interesting ways. In signal classification, they take multiple noisy input and provide accurate answers to the type of modulation represented.

# 2.5.2 Hidden Markov Models (HMM)

In circles, hidden Markov models (HMM) [24] might be considered artificial intelligence, though we certainly not categorize them as such. A HMM is a processing tool that uses data to predict future actions; an implementation of Bayes' law. We discuss them here because they are useful in communications and cognitive radios.

The best reference to learn about HMMs works is Rabiner's tutorial [24]. Channel modeling has extensively used Markov models in research. Probably the most famous is the two-state Gilbert-Elliott model [25] that describes a channel as either a good state or bad. When in one state, there is a probability of staying in that state or moving to the other state. The channel properties determine the type of transition probabilities. Researchers have developed other, more extensive models, and [26] provides a good comprehensive overview of these.

The idea of developing such a model lends itself to cognitive radios. Rieser and Rondeau looked into using HMMs in channel models where they used a genetic algorithm as the training method instead of the Baum-Welch algorithm [27]. The HMM in this instance was used to provide a compact channel model based on information gathered in a system to represent the current channel states. The idea was to use the HMMs as a sensor to understand the channel behavior in a cognitive engine, although the research was not taken further in this direction.

Mohammad's work used HMMs for a similar purpose, but was able to develop classification schemes in order to use the models for decision making in a cellular network [28]. The ability he developed to calculate a similarity distance between HMMs provides promise for future implementation in a cognitive radio system, especially in the context of the environmental modeling used in a case-based system as discussed in Chapter 6.