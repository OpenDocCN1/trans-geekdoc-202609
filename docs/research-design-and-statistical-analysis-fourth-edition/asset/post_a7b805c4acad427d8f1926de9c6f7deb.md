
# Basic Concepts in Probability 57

Two important things about conditional probabilities should be noted. First, people have a tendency to confuse conditional probabilities with joint probabilities. Look carefully at Equations 3.6 and 3.9. The conditional probability $p(A | \text{psychology major})$ is the probability of selecting a slip of paper that is labeled “A” if the selection is made from the 60 slips labeled “psychology.” The joint probability $p(A \text{ and psychology})$ is the probability of selecting a slip labeled both “A” and “psychology” if selection is randomly made from all 100 slips of paper. A conditional probability must be at least as large – and generally larger than – the set from which we sample a subset of the entire sample. For example, when we calculate $p(A | \text{psychology})$, we divide by only the number of psychology majors, a number less than the size of the total sample. Bear in mind, although joint and conditional probabilities are not the same, they are related, as can be in Equation 3.9.

The second thing to note about conditional probabilities is that for any events

## 3.3.6 Mutually Exclusive and Independent Events

Two events $E_1$ and $E_2$ are mutually exclusive if they are incompatible; that is, if an elementary event belongs to $E_1$, it cannot belong to $E_2$. If they are mutually exclusive, $p(E_1) = p(E_2) = 0$, and $p(E_1 | E_2) = 0$. In our current example (Table 3.1), $p(A \text{ and B}) = 0$, because a student who receives a grade of A in the class did not receive a grade B. Earlier, we encountered the partitioning (Equation 3.4), in which we summed the probabilities of mutually exclusive events that summed in Equation 3.4; it is because the set of events in any partitioning is also exhaustive as the one used.

We introduced the concept of independence in discussing concepts for analyzing the structure of events. At that time, we said that events are independent if the occurrence of one event provides no information about the likelihood of the other event. Now that we have introduced the concept of conditional probabilities, we can state the concept of independence more precisely: $E_1$ and $E_2$ are independent if $p(E_1 | E_2) = p(E_1)$; i.e., that is, if the probability of $E_1$ is the same whether or not $E_2$ occurs.

We may ask such questions as “Getting a grade of A independent of the major of the student?” This is another way of asking whether the probability of getting an A is the same for linguistics majors and psychology majors. If there is independence, $p(A | \text{linguistics}) = p(A | \text{psychology}) = 15/60 = .25$, $p(\text{linguistics} | A) = 12/40 = .3$, and $p(A) = .27$. For this data set, getting A is not independent of being a psychology or linguistics major because $p(A | \text{psychology})$ is not equal to $p(A | \text{linguistics})$; therefore, $\langle A, \text{psychology major} \rangle$ and $\langle A, \text{linguistics major} \rangle$ are pairs of events that are not independent. On the other hand, $p(B | \text{psychology}) = p(B | \text{linguistics}) = p(B)$, so that for this data set, getting a grade of B is independent of the student’s major. For both psychology and linguistics students, the probability of getting a B is .60.

We may also wish to ask more general questions such as “Are the variables of grade and major independent of each other?” In order for the answer to be “yes”, each of the six pairs of events formed by combining levels of major and grade (specifically, $\langle A, \text{linguistics} \rangle, \langle A, \text{psychology} \rangle, \langle B, \text{linguistics} \rangle, \langle C, \text{linguistics} \rangle$, and $\langle C, \text{psychology} \rangle$) have to be independent. The major variables and grade are not independent of each other in this example, as we have already shown, $\langle A, \text{psychology} \rangle$ and $\langle A, \text{linguistics} \rangle$ are pairs of events that are not independent.

Two important points about independence should be noted. First, if $E_1$ and $E_2$ are independent events, $p(E_1, E_2) = p(E_1) \times p(E_2)$. To see why this is, consider the definition of conditional probability given by Equation 3.9:

$p(E_1 | E_2) = p(E_1 \text{ and } E_2) / p(E_2)$

Multiplying both sides of this equation by $p(E_2)$ yields

$p(E_1, E_2) \times p(E_2) = p(E_1 \text{ and } E_2)$

But we know that if $E_1$ and $E_2$ are independent, $p(E_1 | E_2) = p(E_1)$. Replacing $p(E_1 | E_2)$ in the equation above, we have that, if $E_1$ and $E_2$ are independent events,

$p(E_1, E_2) = p(E_1) \times p(E_2)$

The second important point is that if $E_1$ and $E_2$ are mutually exclusive, they cannot be independent. Therefore, if $E_1$ and $E_2$ are mutually exclusive, their joint probability and both conditional probabilities must be zero; that is

$p(E_1, E_2) = 0, p(E_1 | E_2) = 0$, and $p(E_2 | E_1) = 0$

In contrast, if $E_1$ and $E_2$ are independent and their probabilities are both greater than zero, then their joint probability is greater than zero.

## 3.3.7 The Additive Law for Compound Events

We are now ready to integrate much of what we have developed to this point into two useful probability laws. The first law is the additive law for compound events. We will often apply this law in the special case in which we have two or more mutually exclusive events, so we begin with that situation.

If $E_1$ and $E_2$ are mutually exclusive events,

$p(E_1 \text{ or } E_2) = p(E_1) + p(E_2)$

This can be extended to any number of mutually exclusive events:

$p(E_1 \text{ or } E_2 \text{ or... } E_n) = p(E_1) + p(E_2) + \dots + p(E_n)$

In English, the probability of the union of two or more mutually exclusive events is the sum of their individual probabilities.

# Basic Concepts in Probability 59

Of course, events are not always mutually exclusive. As we explained in Section 3.2, if $E_1$ and $E_2$ are not mutually exclusive, the probability of their union is usually greater than zero and must be taken into account, so

$p(E_1 \text{ or } E_2) = p(E_1) + p(E_2) - p(E_1 \text{ and } E_2)$

For example, in Table 3.1, $p(A \text{ or psychology major}) = p(A) + p(\text{psychology}) - p(A \text{ and psychology major}) = .27 + .60 - .15 = .72$.

## 3.3.8 The Multiplication Rule for Joint Events

As we did for the additive law, if $E_1$ and $E_2$ are independent,

$p(E_1 \text{ and } E_2) = p(E_1) \times p(E_2)$

The law can be extended to any number of independent events, $E_1, E_2, \dots, E_n$,

$p(E_1 \text{ and } E_2 \dots \text{ and } E_n) = p(E_1) \times p(E_2) \times \dots \times p(E_n)$

If two events are independent, then the probability of their joint occurrence is equal to the product of their individual probabilities. Note Equations 13 and 14 do not hold if the events are not independent. For example, $A$ and psychology major are not independent and $p(A \text{ and psychology}) = .15$, but $p(A)p(\text{psychology}) = .27(.60) = .162$. However, the multiplication rule can be extended to events that are not independent.

$p(E_1 \text{ and } E_2) = p(E_1) \times p(E_2 | E_1) = p(E_2) \times p(E_1 | E_2)$ (15)

Equation 15 follows directly from the definition of conditional probability, $p(E_i | E_j) = p(E_i \cap E_j)/p(E_j)$. Multiplying both sides of this equation by $p(E_j)$ yields $p(E_i \text{ and } E_j) = p(E_j) \times p(E_i | E_j)$. For example, applying Equation 15 to the data of 3.1, we can see that $p(A \text{ and psychology major}) = p(\text{psychology})p(A | \text{psychology}) = .60(15/60) = .15$.

## 3.3.9 Bayes' Rule

There is one more probability rule that is useful to know. In Section 3.3.5, we noted that $p(E_1 | E_2)$ and $p(E_2 | E_1)$ are not the same thing and that they usually have different values.
