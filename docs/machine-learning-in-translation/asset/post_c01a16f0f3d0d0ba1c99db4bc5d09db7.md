

Here Goldberg touched upon two different concepts: one is language data that people produce, the other is the rules that govern language. When examining the nature of rules, there are two primary considerations: (1) rules are not superficial occurrences like data; rather, they are further processed, hidden patterns or representations based on data; (2) rules can be constructed by both humans and machines, and while humans infer the rules using their intuitive reflections, machines use mathematical methods to capture the patterns of data. When Goldberg aims to hard code linguistic rules into a computer program, he notices that many human-constructed rules may not necessarily be machine friendly.

These two types of rules, namely human-constructed linguistic rules and machine-generated rules, lead to two general approaches to using machines:

- 1 In traditional computer programming – the symbolic approach to NLP in our case – the system receives input training data as well as rules and returns answers.
- 2 In an ML-driven system – the statistical approach to NLP in our case – which includes both traditional statistical methods and artificial neural network models, one starts with input data and answers (training data), both of which are concrete and visible, and the results generated are patterns or rules that machines have summarized (see Figure 1.1).

The former is driven by rules that are dynamically discovered or summarized as a result of human learning, whereas the latter generates its own machine rules and avoids human intuitive explanations of natural language, which is inefficient in a two-digit computer system. As Samuel (1959) stated, “a computer can be programmed so that it will learn to play a better game of checkers than can be played by the person who wrote the program” (p. 535). He added that “programming computers to learn from experience should eventually eliminate the need for much of this detailed programming effort” (p. 535). From his line of argumentation, we can see that machine learning gives computers the ability to learn without being explicitly programmed. In other words, machine learning allows computer programs to develop their own capability to create and generate new output, rather than simply memorizing what has been fed to them through traditional programming.

The use of machines to generate patterns with or without a minimum level of human intervention led to a philosophical question: “Can machines think?”, as Alan Turing (1950) asked in his article Computing Machinery and Intelligence. Turing supports the advantage of drawing a fairly sharp line between the physical and intellectual capacities of humans, proposing that machines can ‘learn’ similarly to how humans apply intellect by approaching what is visible. An important feature of a learning machine is that the rules get changed in the learning process, and its teacher will often be largely ignorant of what is going on inside, although still be able to some extent to predict the pupil’s behavior. Turing also introduces the famous Turing Test, originally called the imitation game in the aforementioned

![](img/ec5cbdd0549c7a4e25c06fc472c12208_37_0.png)

FIGURE 1.1 Two approaches to using machines

article, which aims to test a machine’s ability to exhibit intelligent behavior equivalent to, or indistinguishable from, that of a human. Turing’s work marks a new era of machine learning and artificial intelligence.

There is still much to explore in order to more fully understand aspects of how the human mind works in learning and inferencing processes. Yet apparently machine learning helps establish models to simulate a process generating results, and this simulation is concrete and visible to us. In the next section, we will explore how artificial neural networks simulate the representation of meaning.

## 1.4 Two approaches to meaning representation

As mentioned earlier, human language is a unique creation. A piece of naturally occurring text contains both multiple language units (e.g., words) and an order of these units. This is not a simple parts-to-whole problem, as underlying such a structured combination there is meaning, which is related to each unit but is more than the sum of the parts. Thus, meaning representation is a very complex activity for a computer program to simulate.

As discussed in the Introduction, artificial neural networks are able to combine statistical learning with various theories of representation. In particular, neural network language models, which are composed of large numbers of units (the analogs of neurons) together with weights that measure the strength of connections between the units (Buckner & Garson, 2019), can represent meaning in real value vectors. Specifically, in natural language processing, entities can be represented by activities of simple, neuron-like computing elements in an artificial neural network.

There are many representational schemes between a concept and its neuron(s), i.e., entities and computer elements. The most straightforward one uses one computing element (neuron) for each entity. This is called a local (or localist) representation. It entails a belief that there is a one-to-one correspondence between entities and hardware units. This representational scheme is easy to understand and implement because the structure of the physical hardware network mirrors the structure of the knowledge it contains (Hinton et al., 1986, p. 77), or rather, the surface structure of human knowledge.

In natural language processing, this one-to-one correspondence provides us with a gateway to start to understand language from what is tangible externally, from what we can see or hear in an actual piece of text or speech. By sampling real-life language occurrences and assembling a corpus, which is a large and principled collection of natural texts (Biber et al., 1998, p. 12), the researcher can observe specific linguistic forms at play. In terms of data type, textual data are categorical, rather than numerical, meaning they are discrete in nature, and arithmetic operations cannot be performed using these values. Just as with words on a piece of paper, each one is an entity unto itself – a separate kingdom – and mathematical operations using these linguistic forms is not possible.

This means that a machine cannot interpret the categorical data directly. They must be converted to numbers. For example, in order to study the language behavior of a small corpus that consists of two sentences – He is a good learner. He gathers insights from a machine learner. – we can label each unique word, or word type (Smith, 2019), with one unique decimal number. All unique words make up a vocabulary. In this case, if we ignore punctuation and capitalization, the length of the vocabulary or the total number of word types is 9, as shown in the first column of Table 1.1. In order to convert these word types to numbers, the simplest way is to assign a decimal number to each of them, as shown in the second column of Table 1.1. This is called label encoding (Chollet, 2017).

| Categorical textual data Unique word | Categorical decimal numbers Label encoding | Numerical data in a binary string One-hot encoding |
|---|---|---|
| He | 1 | 100000000 |
| Is | 2 | 010000000 |
| A | 3 | 001000000 |
| Good | 4 | 000100000 |
| Learner | 5 | 000010000 |
| Gathers | 6 | 000001000 |
| Insights | 7 | 000000100 |
| From | 8 | 000000010 |
| Machine | 9 | 000000001 |

Label encoding is very straightforward, indicating a one-to-one correspondence between entities, i.e., word form and hardware processing units (neurons). However, the numeric values can be misinterpreted by algorithms that are embedded with a hierarchy or order in them. This ordering issue is addressed in another common alternative approach called “one-hot encoding” (Harris & Harris, 2012; Chollet, 2017). This method is a binary representation of each word in a corpus, by which we use a vector of 9 bits to represent the unique words in our vocabulary, by simply making the 1st bit represent the word “He”, the second bit the word “is”, etc. (see column 3 in Table 1.1).

However, this method has some disadvantages in terms of using computer elements to represent words:

- 1 One-hot encoding is a vector, that is, a list of numbers, and the size of the vector can be extremely large as the size of vocabulary increases. For example, if the vocabulary size of a corpus is 10,000, each word’s numerical representation will be 10,000 digits.
- 2 Data are very sparse as vectors containing mostly 0s and only one 1 (thus the name *one-hot*).
- 3 These vectors do not have information on the relationships between words or meanings derived from these relationships. For example, we would not know how the word *he* (100000000) is related to *learner* (000010000) just by reading the one-hot coding.

One-hot encoding treats words as discrete, atomic units, rather than continuous. This is easy to understand when we consider a type of language in which one word form – the signifier – corresponds to one computer element or neuron. Yet, when considering the meaning of each word – the signified – this method is limited in expressing complex connotations. Neither label nor one-hot encoding changes the data type by simply assigning a number, decimal, or binary. They are still categorical, as adding or subtracting these numbers makes no sense. They are not real numbers as shown in a vector space.

Localist models are very inefficient whenever the correspondence between concepts – the signified, or meaning of a sign – and neurons is not one-to-one. In this case, the data have a componential structure. In our domain – language and translation – almost all data have componential structure: a word contains multiple sense components, like the word *father* includes the meaning of *parent* and *male*.

Componential analysis, also known as feature analysis or contrast analysis, is one of the cornerstones of semantics – the study of meaning (Leech, 1981; Love, 1983). Lyons (1995, pp. 106–108) points out that componential analysis is one approach to lexical semantics. It involves the analysis of the component parts of a lexeme. It has a long history of philosophical discussion and has been employed extensively by linguists. An alternative term for componential analysis is lexical decomposition. Here is an often used example: The words *man*, *woman*, *boy*, and *girl* all denote human beings. We can therefore extract from the sense of each of

