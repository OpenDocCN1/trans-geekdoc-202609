
## 3.2.4 Combining Events in the ESP Experiment

To illustrate the potential usefulness of some of the concepts introduced to this point, suppose that Rachel does not have ESP and randomly guesses on every trial. If so, we would expect her to be 25% of the time in the long run because there are equally likely choices on each trial. In evaluating the strength of the evidence against guessing, we want to be able to translate our hypothesis that she is guessing on each trial into the probability that she makes a specific number of correct responses in a given number of trials. To do this, we need to consider all the possible sequences of correct and incorrect guesses that might occur. A useful conceptual tool for this purpose is a tree diagram like the one in Figure 3.1. Each branch of the diagram in Figure 3.1 represents a distinct combination of possible outcomes for a four-trial experiment.

Suppose that we want to compute the probability that Rachel makes exactly one correct in a four-trial experiment (i.e., 25% correct). To do this, we must analyze the various ways in which individual trial outcomes produce one correct result in four trials. Looking at Figure 3.1, we can distinguish four sequences of trial outcomes that correspond to one correct response: Rachel can be correct on the first trial, but wrong on the second trials 2 through 4 (call this "sequence 1"), or correct on the second trial (sequence 2), or on the third (sequence 3), or the fourth (sequence 4). Each of these sequences represents a joint event; e.g., (correct on trial 1) and (error on trial 2).

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_73_0.png)

Figure 3.1 Tree diagram for four trials with two possible responses on each trial (C = correct, E = error). The numerical subscripts represent trial number.

(error on trial 3) and (error on trial 4). We do not care on which trial the correct response occurs – the outcome of one correct response occurs if sequence 1 or sequence 2 or sequence 3 or sequence 4 is observed. Further, the four sequences are mutually exclusive events, the response of one correct in four trials can be represented as the union of four, mutually exclusive joint events (i.e., the four sequences of trial outcomes). This precise specification of the relationship between individual trial outcomes and one possible experimental outcome is necessary if we are to translate a hypothesis about the probability of a correct response on any trial into a probability (p) of a given experimental outcome.

## 3.3 Computing Probabilities

In probability theory, numbers are assigned to the events in a sample space. We will denote the probability of an event, A, by p(A). The assignment of probabilities to events follows some simple rules.

### 3.3.1 Some Basic Rules of Probability

The sample space, S, consists of all the elementary events, and the probabilities of the elementary events must sum to 1. This must be the case because the elementary events are, by definition, mutually exclusive and exhaustive. In the simplified ESP experiment, the set of events (0, 1, 2, 3, and 4 correct responses) are mutually exclusive and exhaustive, so their probabilities must also sum to 1. In general,

p(S)=1 (3.1)

It should be evident from the definition of probability in Equation 3.1 that a probability must have a value within the range from 0 to 1. More precisely,

0 ≤ p(A) ≤ 1 (3.2)

The sample space can be partitioned into two mutually exclusive and exhaustive sets of elementary events, call these A and Ā (“not-A”), which is called the “complement of A”. Given that p(S)=1, it follows that p(A or Ā) = p(A) + p(Ā) = 1, and therefore that

p(Ā) = 1 - p(A) (3.3)

For example, if event A is “zero correct responses” in the four-trial ESP experiment, then Ā is “one or more correct responses.” Given that p(S)=1, p(one or more correct) must equal 1 - p(zero).

Finally, it follows from the preceding rules that if we define a set of events that are mutually exclusive and exhaust the events in a sample space, then the sum of their probabilities will equal 1. If, the set of A, B, C, . . . constitute a partition of S, then

p(A or B or C...) = p(A) + p(B) + p(C) + ... = 1 (3.4)

### 3.3.2 Assigning Probabilities to Marginal Events

We have some simple rules that define properties of probabilities, but how do we assign probabilities to actual events in a meaningful way? In the case where all of the elementary events in a sample space are equally likely, the probability of event A is the ratio of the number of elementary events in A to the total number of events, $n(A)$, in the sample space, $n(S)$. That is, the probability of an event A is its relative frequency in the sample space:

$p(A) = \frac{n(A)}{n(S)} \quad (3.5)$

To concrete, let's return to Table 3.1 and the example of grades in a statistics class. Suppose we want to find the probability that a slip of paper randomly selected from the box B; $p(B)$ is simply the number of slips of paper with B divided by the total number of slips of paper:

$p(B) = \frac{60}{100} = .60$

In the preceding example, we computed the probability of a particular grade without regard to student. In Table 3.1, the number of students with As, Bs, and Cs and the numbers of psychology majors are presented in the margins of Table 3.1. Because of this, the probability of observing a particular value of some variable (e.g., grade) without respect to any other variable (e.g., major) is referred as marginal probability.

### 3.3.3 Joint Probabilities

The probability of obtaining a combination of events is referred as joint probability. The probabilities of elementary events are obtained by computing the relative frequency of the joint event in the sample space: for example, $p(A \text{ and } psychology)$, which is read as "the probability of A and psychology," is the probability of selecting a slip of paper with both "A" and "psychology major" on it.

$p(A \text{ and } psychology) = \frac{n(A \text{ and } psychology)}{n(S)} \quad (3.6)$

where $n(A \text{ and } psychology)$ is the number of elementary events that belong to both A and psychology. From Table 3.1 data, $p(A \text{ and } psychology) = 15/100 = .15$. Similarly, if the events B and linguistics correspond to "getting a grade of B" and "being a linguistics major," respectively, $p(B \text{ and linguistics}) = 24/100 = .24$. Note that $p(A)$ must always be as large as $p(A \text{ and } psychology)$ because the event A will always contain at least as many elementary events as the joint event <A, psychology>. clarified by reconsidering Table 3.1. Each column represents the event of a letter grade and has two nonoverlapping parts. For example, the column representing the event <A> consists of the joint events <A, psychology> and <A, linguistics>. Note that $n(A)=n(A \text{ and } psychology)+n(A \text{ and linguistics})$, and it follows from Equations 3.5 and 3.6 that $p(A)=p(A \text{ and } psychology)+p(A \text{ and linguistics})$.

### 3.3.4 Probabilities of Unions of Events

The union of two events consists of all the elementary events belonging to either or both of them. The elementary events forming the union of events A and psychology are the following cells of Table 3.1: <A, psychology>, <A, linguistics>, <B, psychology>, and <C, psychology>. The expression $p(A \text{ or } psychology)$ refers to the probability of obtaining an elementary event belonging to either A or psychology that falling into any of the cells just noted:

$p(A \cup psychology)=\frac{n(A \text{ or } psychology)}{n(S)}=\frac{12+15+36+9}{100}=.72\quad (3.7)$

because 100 elementary events belong to either A or psychology or both. Note that $n(A \text{ or } psychology)$ does not generally equal $n(A)+n(psychology)$. As should be clear from Table 3.1, this sums twice the 15 elementary events belong to both A and psychology. Verify for yourself that $p(A \text{ or } psychology)=p(A)+p(psychology)-p(A \text{ and } psychology)$. Also verify that $p(A \text{ or } linguistics)=55/100=.55$. In general, if $E_1$ and $E_2$ are two events,

$p(E_1 \text{ or } E_2)=p(E_1)+p(E_2)-p(E_1 \text{ and } E_2)\quad (3.8)$

We subtract $p(E_1)$ and $p(E_2)$ because $E_1$ and $E_2$ are not mutually exclusive. If they were, the probability of their intersection would be zero and Equation 3.8 would still be true.

### 3.3.5 Conditional Probabilities

We are interested in computing the probabilities of events when considering only a subset of events in a sample space. For example, we may be interested in the probability of obtaining a grade A if only the psychology majors are considered. This probability is called a conditional probability because it is the probability of A given the condition that psychology major occurs. It is represented by $p(A|psych major)$, and is read as "the probability of A given psychology major." There are 60 slips of paper labeled "psychology major" and 15 of them correspond to grades of A. Therefore, $p(A|psychology)=15/60=.25$. More generally, $p(A|psychology major)$ is the proportion of all elementary events in psychology that also belong to $A_i$; that is,

$p(A|psychology)=\frac{n(A \text{ and } psychology)}{n(psychology)}=\frac{p(A \text{ and } psychology)}{p(psychology)}\quad (3.9)$

Verify that for the current example, $p(B|psychology\ major)=36/60=.60$; $p(psychology\ major|A)=15/27=.56$; and $p(A|B)=0/60=0$.
