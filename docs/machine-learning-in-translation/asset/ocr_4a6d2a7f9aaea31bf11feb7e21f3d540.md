vectors. Specifically, in natural language processing, entities can be represented by activities of simple, neuron-like computing elements in an artificial neural network.

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