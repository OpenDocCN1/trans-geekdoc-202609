# 7 Ripple Down Rules and Classification

Eric Martin
School of Computer Science and Engineering, UNSW Sydney
Kensington, Australia

# 7.1 RIPPLE DOWN RULES AND CLASSIFICATION

Fields and subfields, often use variations on the same concepts and techniques, even if that is not always known to researchers working in their own domain of expertise. For instance, consider three subfields of Artificial intelligence: knowledge acquisition, knowledge representation, and . As particular techniques, they use Ripple Down Rules (RDR), belief revision based on preferential models, and learning in the limit with bounded mind changes, respectively. All three techniques are related to the topological concept known as the difference hierarchy. In this chapter, we show how developing a clear understanding of how RDR works, results in notions and questions on the basis of which such relationships naturally emerge.

# 7.2 PRACTICAL RIPPLE DOWN RULES

One aspect of knowledge acquisition is capturing human expertise. Recognising that it is an iterative process, that now and then requires revisions to what has been gathered so far, it is important to first, design a framework that makes the exercise as easy and effective as possible. Ripple Down Rules (RDR) is such a framework, developed at the School of Computer Science and Engineering (CSE) at the University of New South Wales (UNSW) by a former Head of School, Paul Compton [1]. Adapted from [5], Figure 7.2 shows an example of an RDR tree, the key structure of the RDR framework, at a very early stage of knowledge acquisition from medical experts.

Each node of the tree comes with a set of conditions, meant to be evaluated as either true or false, and a conclusion—here, a reference to a particular diagnosis. That set is empty for the root of the tree, associated with a default conclusion. Each node has up to two children, connected to their parent either with an elif edge or with an unless edge; the latter kind of edge and only the latter leaves from the root. Decision trees only have implicit elif edges between siblings. This is illustrated in Figure 7.1 w.r.t. to the toy example of deciding whether to play golf: if the outlook is sunny then consider the level of humidity, elif it is overcast then decide to play, elif it is rainy then consider the strength of the wind.