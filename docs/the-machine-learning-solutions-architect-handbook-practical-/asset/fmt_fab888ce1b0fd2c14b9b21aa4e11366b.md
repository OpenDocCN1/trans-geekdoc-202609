
6.  **Level 5 – Superhuman**: This is where AI is better than 100% of humans. Again, only narrow AI such as `AlphaFold` (a protein folding model), `AlphaZero` (an AI model that plays the game of Go), and `Stockfish` (an open-source chess engine) has achieved this level of capability. So what is the path to achieving AGI? No one has claimed they know the definitive answer yet, but the pursuit continues through the exploration of various active research areas such as multi-modality understanding, memory management, cross-domain reasoning and planning, and continuous self-learning. Furthermore, leading AI experts have been proposing diverse theoretical approaches in these domains, ranging from the integration of symbolic reasoning and connectionist architectures to the study of emergent phenomena, and the whole organism approach. In the subsequent section, let’s explore the symbolic, connectionist, and neural-symbolic approaches.

## The symbolic approach

The symbolic approach relies on explicitly representing knowledge and reasoning using symbolic representations, such as logical statements, rules, and structured data formats. In this paradigm, the knowledge about a particular domain is manually encoded into the system using formal languages and logical formalisms. An example of symbolic representation could be “dogs have four legs.” This encoded knowledge forms a knowledge base, which acts as a repository of facts, concepts, relationships, and rules that define how the world works within that domain. The symbolic AI system then uses an inference engine, which is a component that applies logical operations and rules of reasoning to the knowledge base. This allows the system to derive new conclusions, make inferences, and solve problems by manipulating and combining the symbolic representations in a structured and logical manner.

For example, in a symbolic AI system designed for medical diagnosis, the knowledge base might contain rules that represent the relationships between symptoms, diseases, and treatments. The inference engine could then use these rules to analyze a patient’s symptoms and logically deduce the most likely diagnosis and appropriate treatment plan.

One of the key advantages of symbolic AI is its ability to provide explainable and interpretable reasoning. Since the knowledge and reasoning processes are explicitly represented, the system’s decision-making process can be traced and understood by humans, which is particularly important in domains such as finance, law, and healthcare, where transparency and accountability are crucial.

However, symbolic AI systems also face challenges, such as the knowledge acquisition bottleneck, where manually encoding vast amounts of knowledge can be time-consuming and labor-intensive. 

Additionally, these systems often struggle with handling ambiguity, uncertainty, and context-dependent knowledge, which are more easily tackled by other AI approaches, such as ML and neural networks.

![](OEBPS/Images/B20836_16_17.png)Figure 16.17: Symbolic approach 

One prominent example of symbolic projects is the Cyc project, which stands as one of the longest-running symbolic AI initiatives. This ambitious endeavor aims to construct a comprehensive ontology and knowledge base that captures common sense rules about how the world operates. The Cyc project employs formal logic as its primary mechanism for reasoning and inference.

While groundbreaking in its scope and ambition, the Cyc project also highlights key challenges inherent to the symbolic AI approach. These challenges include the knowledge acquisition bottleneck, which refers to the arduous task of manually encoding vast amounts of knowledge in the system. Additionally, the project grapples with issues of brittleness, where slight deviations from the encoded rules or representations can lead to unexpected or erroneous behavior.

Scalability concerns also arise, as the complexity of symbolic systems can rapidly escalate as the knowledge base expands, potentially leading to computational intractability. Furthermore, the robust handling of nuance, uncertainty, and context-dependent interpretations remains a formidable challenge within the symbolic paradigm.

Despite these obstacles, the Cyc project’s pioneering efforts have contributed significantly to the field of symbolic AI, pushing the boundaries of knowledge representation and reasoning capabilities. Its ongoing development continues to shed light on both the potential and limitations of the symbolic approach in the quest for artificial general intelligence.

While symbolic AI laid the crucial groundwork for establishing formal methods for knowledge representation and reasoning, many researchers believe that purely symbolic systems alone are unlikely to be sufficient for realizing the flexibility, robustness, and open-ended generalization required for general intelligence comparable to humans. 

The debate surrounding the extent to which symbolic approaches should be incorporated into AGI systems – whether as a core architecture or in a more complementary role – remains an active area of research with differing perspectives. Critics argue that the inherent limitations of symbolic systems, such as brittleness, scalability issues, and the knowledge acquisition bottleneck, pose significant challenges in capturing the nuanced, context-dependent, and continuously evolving nature of human intelligence. As a result, many advocate for a synergistic approach that combines the strengths of symbolic methods with other paradigms, leveraging the interpretability and strong generalization capabilities of symbolic reasoning while mitigating its weaknesses through complementary techniques, such as connectionist models or hybrid architectures.

## The connectionist/neural network approach

This approach focuses on constructing systems that emulate the human brain. Neural network systems, like the brain, employ extensive parallel processing across interconnected nodes or “neurons,” distributing knowledge across connections. Unlike explicit symbolic encodings or rules such as “a dog is an animal,” neural models rely on sub-symbolic distributed representations for the same concept. In sub-symbolic representation, which is used in approaches like neural networks and connectionist models, knowledge or concepts are represented not through explicit symbols or rules, but through patterns of features and characteristics.

Integrated neural network approaches aspire to develop comprehensive end-to-end cognitive architectures covering perception, reasoning, and action. The hypothesis is that scaling up neural networks in both architecture and training data may induce the emergence of general intelligence, resembling the neural connections in the brain. However, current neural nets face challenges, as they are often narrow, lack systematicity, and encounter difficulties with transfer learning.

![](OEBPS/Images/B20836_16_18.png)

Figure 16.18: Connectionist or neural network approach 

With the remarkable capabilities demonstrated by LLMs, a compelling question arises: Can these models, arguably the most advanced neural networks to date, pave the way toward AGI? This question has sparked contrasting viewpoints within the AI community. Yann LeCun, the chief AI scientist at Meta, contends that the current autoregressive approach employed by LLMs is unlikely to lead to AGI, as these models are primarily trained to predict the next token rather than engage in genuine planning or reasoning processes. According to LeCun, current LLMs lack the ability to truly comprehend and reason about knowledge; instead, they retrieve and generate information in an approximate manner.
