# 54 Research Design and Statistical Analysis

(error on trial 3) and (error on trial 4). We do not care on which trial the correct response occurs – the outcome of one correct response occurs if sequence 1 or sequence 2 or sequence 3 or sequence 4 is observed. Further, the four sequences are mutually exclusive events, the response of one correct in four trials can be represented as the union of four, mutually exclusive joint events (i.e., the four sequences of trial outcomes). This precise specification of the relationship between individual trial outcomes and one possible experimental outcome is necessary if we are to translate a hypothesis about the probability of a correct response on any trial into a probability (p) of a given experimental outcome.

# 3.3 Computing Probabilities

In probability theory, numbers are assigned to the events in a sample space. We will denote the probability of an event, A, by p(A). The assignment of probabilities to events follows some simple rules.

# 3.3.1 Some Basic Rules of Probability

The sample space, S, consists of all the elementary events, and the probabilities of the elementary events must sum to 1. This must be the case because the elementary events are, by definition, mutually exclusive and exhaustive. In the simplified ESP experiment, the set of events (0, 1, 2, 3, and 4 correct responses) are mutually exclusive and exhaustive, so their probabilities must also sum to 1. In general,

p(S)=1 (3.1)

It should be evident from the definition of probability in Equation 3.1 that a probability must have a value within the range from 0 to 1. More precisely,

0 ≤ p(A) ≤ 1 (3.2)

The sample space can be partitioned into two mutually exclusive and exhaustive sets of elementary events, call these A and Ā (“not-A”), which is called the “complement of A”. Given that p(S)=1, it follows that p(A or Ā) = p(A) + p(Ā) = 1, and therefore that

p(Ā) = 1 - p(A) (3.3)

For example, if event A is “zero correct responses” in the four-trial ESP experiment, then Ā is “one or more correct responses.” Given that p(S)=1, p(one or more correct) must equal 1 - p(zero).

Finally, it follows from the preceding rules that if we define a set of events that are mutually exclusive and exhaust the events in a sample space, then the sum of their probabilities will equal 1. If, the set of A, B, C, . . . constitute a partition of S, then

p(A or B or C...) = p(A) + p(B) + p(C) + ... = 1 (3.4)