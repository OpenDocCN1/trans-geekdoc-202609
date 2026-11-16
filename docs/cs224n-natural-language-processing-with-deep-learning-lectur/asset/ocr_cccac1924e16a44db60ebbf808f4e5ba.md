# # CS224n: Natural Language Processing with Deep Learning
Lecture Notes: Part IV
Dependency Parsing
Winter 2019

**Keyphrases:** Dependency Parsing.

# ## 1 Dependency Grammar and Dependency Structure

Parse trees in NLP, analogous to those in compilers, are used to analyze the syntactic structure of sentences. There are two main types of structures used - constituency structures and dependency structures.

Constituency Grammar uses phrase structure grammar to organize words into nested constituents. This will be covered in more detail in following chapters. We now focus on Dependency Parsing.

Dependency structure of sentences shows which words depend on (modify or are arguments of) which other words. These binary asymmetric relations between the words are called dependencies and are depicted as arrows going from the **head** (or governor, superior, regent) to the **dependent** (or modifier, inferior, subordinate). Usually these dependencies form a tree structure. They are often typed with the name of grammatical relations (subject, prepositional object, apposition, etc.). An example of such a dependency tree is shown in Figure 1. Sometimes a fake ROOT node is added as the head to the whole tree so that every word is a dependent of exactly one node.

![](bbox=[0.66, 0.45, 0.9, 0.565])

Figure 1: Dependency tree for the sentence "Bills on ports and immigration were submitted by Senator Brownback, Republican of Kansas"

# ## 1.1 Dependency Parsing

Dependency parsing is the task of analyzing the syntactic dependency structure of a given input sentence S. The output of a dependency parser is a dependency tree where the words of the input sentence are connected by typed dependency relations. Formally, the dependency parsing problem asks to create a mapping from the input sentence with words S = w0w1...wn (where w0 is the ROOT) to its dependency tree graph G. Many different variations of dependency-based methods have been developed in recent years, including neural network-based methods, which we will describe later.

To be precise, there are two subproblems in dependency parsing (adapted from Kuebler et al., chapter 1.2):

+   1. **Learning**: Given a training set D of sentences annotated with dependency graphs, induce a parsing model M that can be used to parse new sentences.