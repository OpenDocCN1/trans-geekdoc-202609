
## 2. Procedural Response
When solving a problem, the system can create and execute a procedure (program synthesis system, automatic programming). This is a very interesting and promising direction that is attracting the attention of a large number of researchers.

## 3. Conceptual Response
The answer is the law, not a solution is built but a scheme for solving a class of problems that may not even be feasible on a computer. Full implementations are not known at this time.

Let's give examples of answers at different levels using the paradigm with sorting numbers from paragraph 0 (remember, the problem is as follows: we want the computer to sort a set of three numbers in ascending order).

**(0)** `2 5 7` → `yes`  
`5 2 7` → `no`

**(1)** `5 2 7` → `2 5 7`

**(2)** `{ x, y, z }?{ x < y < z }` → `Sort3`

### (3) `sort { x i }` → `∀ i, j ( i < j → x i < xj )`

At level 0 we present a sequence and the system only checks if it is sorted or not. At level 1 we present a sequence and the system obediently sorts it. At level 2, the system creates a sorting procedure similar to that shown in paragraph 0. Finally, at level 3, the hypothetical system tells us what it means to sort an array of numbers [[23]](#part0005.xhtml#_ftn23).

### 1.4.5. Classification according to the degree of universality

First, each new idea of knowledge representation tied to a specific subject area is born. The fact is that in the field of AI it is common to accompany the publication of new ideas with at least one concrete practical example that demonstrates the advantages of the novelty. If the idea is good, it finds new applications in related areas and grows into a problem-oriented method. In the future, there will be a temptation to make the knowledge representation system as universal as possible for solving a wide variety of problems. However, this wish is practically useless, since with increasing universality the applicability of such knowledge representations decreases sharply.

Let's explain in more detail the terminology we use [[24]](#part0005.xhtml#_ftn24).

**Universality** (of a given knowledge representation system in a given subject) is the proportion of representable tasks in the subject.

Therefore, we call **universal** (in a particular subject) a way of representing knowledge that allows us to formulate all tasks.

**Applicability** (of a given knowledge representation system in a given domain) is the fraction of representable problems in the domain that can be solved.

Therefore, we call **applicable everywhere** or **total** (in a certain subject) such a way of representing knowledge that allows us to solve all problems considering real quantitative constraints. It is clear that universal and at the same time total knowledge representation systems are hardly possible for sufficiently broad subject areas. Furthermore, observations show that there is an inverse relationship between universality and applicability.

The concept of representing the world in discrete states and looking for a sequence of transformations from the initial state to the target state is surprisingly broadly applicable. The graph search algorithm is applicable in all cases. However, this versatility comes at the cost of sheer search inefficiency.

![Relationship between universality and applicability](Images/image00336.jpeg)

*Note: The original text contained a caption "Rice. Mistake! The text of the specified style in the document absence. .13. Relationship between universality and applicability" which appears to be an artifact. The image is referenced as Figure 13.*

Note that in practice, neither in databases, nor in application packages, nor in applied artificial intelligence systems, the goal of achieving universality is usually set. Typically, the goal is to increase applicability, even at the cost of reducing versatility. The reasons are very simple. First, the possibilities of manipulating knowledge depend on the subject, and only by taking into account the characteristics of the subject one can hope to build a compact representation of knowledge that will provide effective solution to problems and increase applicability. Second, meta-knowledge (management strategy) is weak in universal systems; Knowledge of the order in which certain rules should be applied, what is important and what can be neglected when solving a problem.

### 1.4.6. Classification by architecture and tools

When analyzing the architecture of applied systems with elements of artificial intelligence, it is logical to single out:

*   **System manipulated objects** (other given words);
*   **Actions** by these manipulations produced (what can be done with this data);
*   **Control strategy** that determines when and what manipulations to perform (in what order, on what objects, what actions to apply).

Such an idea of the architecture of an artificial intelligence system is not a dogma—it arises from the analysis of typical modern artificial intelligence systems. Highly specialized systems sometimes have a different architecture. This means a logical analysis and not an analysis at the machine code level, where the architectural structure is already indistinguishable.

Now we are talking about these three components (especially if they are clearly separated in the software implementation): **data** (object properties), **algorithms** (object methods in the sense of object-oriented programming) and **meta-knowledge**.

The first work in the field of AI already showed the need for special tools for the development of applied systems. This is due to a number of features of the software implementation of artificially intelligent systems, some of which we will discuss in the third chapter. Be that as it may, for the development of applied artificial intelligence systems, various programming languages and tools have been and are used, which cannot escape a given system. The tool used in the development of the AI system is a classification feature.

## Conclusions on Chapter 1

1.  **Artificial intelligence** is a branch of science that has a clearly defined theme – the modeling of thinking, understood as rational behavior, using a range of methods from computer science and mathematics.
2.  The history of the development of artificial intelligence shows that the time for reorientation is over and the time for practical application is now upon us.
3.  An analysis of the achievements of artificial intelligence shows that the most important methods for practical application are methods of knowledge representation.

# Chapter 2. Knowledge Representation Through Product Systems

**Knowledge representation by production systems** (Production Rules Knowledge Representation) is one of the most frequently used knowledge representation mechanisms in intelligent systems. This mechanism is conceptually simple, its idea is naturally perceived and easily implemented in software.

In fact, there is no sharp boundary between artificial intelligence applications and other software. Production systems are just another way for a computer to organize a process of information processing. This method is fundamentally different from the usual procedural and object-oriented programming, but has no fewer features.

## 2.1. Product Systems

Several definitions of **production systems** (or **production systems** or **rules-based systems**) are proposed [[25]](#part0005.xhtml#_ftn25), viewed from different angles. Ultimately, different definitions lead to the same object, although they come from different angles and differ in some details. We consider three definitions:

*   **Production systems in their structure**;
*   **Production systems from an algorithmic point of view**;
*   **Production systems as a logical calculation**.
