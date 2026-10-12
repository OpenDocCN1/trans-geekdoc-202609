
Several techniques have been proposed to support Federated Learning as the response to the previously outlined question on opportunities to train a model without the data needing to be centrally located. In that context coordinating distributed training and centralized aggregation have significant roles. Coordination and distribution are, according to [[18](#ch2.xhtml#ref2_18)], summarized through the steps below, based on structures as outlined in [Fig. 1](#ch2.xhtml#fig2_1). Here, a central node (Central Server, of [Fig. 1](#ch2.xhtml#fig2_1)), aggregates the outcome of the actions at the client nodes (Node 1, 2, and 3, of [Fig. 1](#ch2.xhtml#fig2_1)), that is performing the local training. The steps below represent one round of distributed training, and are performed iteratively to achieve reasonable accuracy:

![Figure 1. An example of a basic federated learning scheme [22].](images/fig2_1_B.jpg)

[Figure 1. An example of a basic federated learning scheme](#ch2.xhtml#R_fig2_1) [[22](#ch2.xhtml#ref2_22)].

1.  **Initialization**: The nodes are activated and wait for the central server to give the calculation tasks.

2.  **Client selection**: local nodes are selected to start training on local data.

3.  **Configuration**: the central server orders selected nodes to undergo training on the model on their local data in a pre-specified fashion.

4.  **Reporting**: each selected node sends its local model to the server for aggregation. The central server aggregates the received models and sends back the model updates to the nodes.

5.  **Termination**: once a predefined termination criterion is met (e.g., a maximum number of iterations is reached, or the model accuracy is greater than a threshold) the central server aggregates the updates and finalizes the global model.

Further discussions on implementation details on Federated Learning won’t be elaborated on in this section. For more information on details regarding implementations of principles behind Federated Learning [[19](#ch2.xhtml#ref2_19)]. For developers of Federated Learning systems today, there are predeveloped platforms, where developers do not have to care about the underlying machinery, for creative customized development purposes. For instance, [[20](#ch2.xhtml#ref2_20)] provides information on the Python programming based TensorFlow Federated (TFF) platform, with several informative examples on how to set up a TFF environment, and how to get started using it to speed up the construction process. Moreover, similar support is provided by Oracle, but with Java as the development programming language ([[21](#ch2.xhtml#ref2_21)]).

### 3.2 Views on Federated Learning and Artificial Intelligence

IoT (Internet of Things) based systems are commonly addressed in contexts of the Digital Factory (more of that in a coming section), and as a concept, according to [[23](#ch2.xhtml#ref2_23)] this contributes to industries becoming more intelligent. Here it is pointed out that AI will have an impact on ML training on IoT devices, and with FL as a platform for distributed ML. That is, AI is seen as a higher-level concept including not only ML but also FL. The AI view of FL is also addressed in [[13](#ch2.xhtml#ref2_13)] which especially describes isolated islands of data, and data privacy and security, as two major AI challenges.

As a field, ML is generally seen as included in the broader field of AI. Moreover, AI is also seen in the field of Cognitive Science as a way to simulate cognitive behavior, and also as a response to external stimuli. The Cognitive side of AI is here two-folded, one sensor we often use is prolongations, and the second human cognitive functions such as vision (image, video, 3D-Lidar), hearing (sound), haptic (tactile), smell (fragrances/odors) and taste (tastebuds). To make sense of this data we often must analyze and orchestrate it as our cognitive perceptors would have experienced it in the first place firsthand.

Still, ML is a key component of the field of FL, and where further subconcepts of AI are generally not considered an issue. However, ML has clear limitations in data imbalances [[24](#ch2.xhtml#ref2_24)] or even in the absence of data. The authors, therefore, extend the discussions on AI for Federated Learning, not only to focus on ML but complement the AI approach with concepts from Cognitive Science, as outlined in [Fig. 2](#ch2.xhtml#fig2_2), and discussed in a further section. The authors of this chapter are aware that such approaches are outside the common frames for FL, but still want to shed light on significant principles and open up for further discussions and research themes.

![Figure 2. Scheme over federated learning, AI, ML and Cognition, a) the common view, b) the extended view.](images/fig2_2_B.jpg)

[Figure 2. Scheme over federated learning, AI, ML and Cognition, a) the common view, b) the extended view.](#ch2.xhtml#R_fig2_2)

## 4. Industry 4.0

The fourth industrial revolution or 4IR also called Industry 4.0 and ‘The Connected Age’ originates back to the 1900 century going from hand production methods to machines. A technological revolution followed where railroad and telegraph networks were extensively built out which meant faster transfer of people and ideas. The 3rd industrial revolution also known as the digital revolution advanced rapidly after the two world wars, and has completely set a new scene regarding industrialization, and has laid the foundation for the 4ir.

Industry 4.0 includes key components such as Cyber Physical Systems (CPS) where the “function of CPS has been identified as monitoring physical processes and creating a virtual copy of the physical world to support decentralized decision-making” [[25](#ch2.xhtml#ref2_25)]. The concept of CPS aligns with that of Digital Twins where a digital twin relates to a virtual copy of its corresponding physical system [[26](#ch2.xhtml#ref2_26)]. Typically, the digital twin emphasizes the connection between the physical model and the corresponding virtual model or virtual counterpart. This connection is typically established by generating real time data using sensors [[25](#ch2.xhtml#ref2_25)].

The fourth industrial revolution and ‘always being connected’ means we have a trend towards extensive automation and data exchange both privately and in manufacturing processes, it is here that the FL plays a major part. Telecommunication via 4G/5G/6G [[27](#ch2.xhtml#ref2_27)], Bluetooth [[28](#ch2.xhtml#ref2_28)], and WiFi [[29](#ch2.xhtml#ref2_29)] create a baseline with communication standards for our federated learning highway. Federated learning uses this network and can real time meet requirements and support in decision-making via efficient analytics in operational contexts. Industry 4.0 corresponds to the concept of a Digital Factory, that is, the digitization of the industry, where contexts of industrial robots more and more rely on technologies, such as CPS and Digital Twins. Other terminologies of use are *Smart Factory*, and *Dark Factory*, that correspond to the autonomy of industrial robots on an individual basis, as well as at a holistic level. By the holistic level, we mean the interaction between robots to fulfill a task of assembly.

### 4.1 Automation

Automation per definition means “the use or introduction of automatic equipment in a manufacturing or other process or facility” [[30](#ch2.xhtml#ref2_30)]. Automation in software development is “…applications that minimize the need for human input and can be used in a variety of ways in almost any industry. At the most basic, automation software is designed to turn repeatable, routine tasks into automated actions” [[31](#ch2.xhtml#ref2_31)]. This means tasks and procedures need to be correctly understood and represented when translated and digitally mapped to represent their intended operation, i.e., task and perception.
