response to a given input. This across-application variability frustrates efforts to obtain concise and generalisable solution principles. Nevertheless, it is perhaps useful to view interactions of this type as being a kind of pseudo-programming task. This level of abstraction provides a useful frame for identifying the commonality.

We propose six key solution principles for the design of the IML interface:

+   (1) Make task goals and constraints explicit
+   (2) Support user understanding of model uncertainty and confidence
+   (3) Capture intent rather than input
+   (4) Provide effective data representations
+   (5) Exploit interactivity and promote rich interactions
+   (6) Engage the user

These principles cover multiple aspects across the different activities performed in the IML workflow. They also have specific implications for the interface components described in Section 4. Each is discussed in detail in the remainder of this section.

# 6.1 Make task goals and constraints explicit

Establishing clear task goals is an important part of Interactive Machine Learning for non-experts given that the process is largely user driven. Similarly important is an understanding of what is not possible, i.e. the constraints in the process. The iterative model refinement paradigm implies that users work in pursuit of some desired goal state. For users to construct effective strategies in pursuit of this goal state, it is necessary that they understand their task and its constraints.

This solution principle is largely a response to two of the key challenges for IML introduced in Section 1: users can be imprecise and inconsistent, and training is open ended. In terms of the first challenge, constructing explicit task goals and constraints can aid in focusing user efforts and improving consistency. Many recommender systems exploit user input for dual purposes, i.e. a like provides a signal of interest to a social group but may also inform predicted recommendations. While dual-purpose input with unclear objectives may be suitable for recommender system, we hypothesise that being explicit when requesting user input, whether singular, or multi-purpose, is preferable. It stands to reason that when asking a user to serve as a component in a closed feedback loop, understanding the information presented and actions required is paramount. However, too much information can also be confusing and detrimental to performance.

If user effort and attention is considered as a resource with limited supply then it is sensible to ensure that all expended effort is in pursuit of the goal state. However, this goal state must be clearly defined. For example, Amershi et al. [2011a] observed that when a model reliability metric plot was introduced to the CueFlik interface to provide feedback on quality, users began to focus on maximising this quantity as their primary objective. Careful framing of the task goals and awareness of the interface features that may promote or hinder this understanding is required. The literature has explored and discussed the role that model and prediction explanations may have on the understanding and mental models of users ([Kulesza et al. 2013], [Sarkar 2015]) but there has been less attention given to the effect that prior framing of the task may have on users. It is not unreasonable to hypothesise that supporting user perception of the global task and constraints may improve their ability to select model refinement actions although this should be investigated.

The second challenge revisited above (i.e. the fact that training is open ended) can also be mitigated in part through improved user understanding of goals and constraints. Interaction with machine learning models differs from more conventional computer interactions in that the user may have limited direct control over the behaviour exhibited. A key limitation of machine learning is that false positives/negatives produced are typically difficult to eradicate. For example, a user