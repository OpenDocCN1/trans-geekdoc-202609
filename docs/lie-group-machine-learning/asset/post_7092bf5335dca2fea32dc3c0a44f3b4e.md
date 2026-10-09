
**Definition 15.4.** $\mathcal{J}$ is a small category. We call an arbitrary functor $D: \mathcal{J} \to \mathcal{C}$ as a $\mathcal{J}$ graph in $\mathcal{C}$. If $\mathcal{J}$ is a finite category (i.e., $\mathbf{ob}\mathcal{J}$ is a finite set), then the $\mathcal{J}$ graph is a finite graph. For each object $j$ in $\mathcal{J}$, we call $D(j)$ as vertex of $\mathcal{J}$ graph. For each morphism $\alpha$ in $\mathcal{J}$, we call $D(\alpha)$ as an edge of $\mathcal{J}$ graph.

**Definition 15.5.** $D: \mathcal{J} \to \mathcal{C}$ is a $\mathcal{J}$ graph, $A \in \mathbf{ob}\mathcal{C}$:
(1) If the morphism family $\{\lambda_j: A \to D(j) \mid j \in \mathbf{ob}\mathcal{J}\}$ satisfies the condition that for any morphism $\alpha: j \to j'$ in $\mathcal{J}$, $\lambda_{j'} = D(\alpha)\lambda_j$, i.e., the chart exchange
then we call $\{\lambda_j: A \to D(j) \mid j \in \mathbf{ob}\mathcal{J}\}$ as a cone on $D$, and $A$ is the vertex of this cone.
(2) If $\{\lambda_j: A \to D(j) \mid j \in \mathbf{ob}\mathcal{J}\}$ is a cone on $D$, any cone on $D$ is universal, i.e., is for any $B \in \mathbf{ob}\mathcal{C}$ and cone $\{\mu_j: B \to D(j) \mid j \in \mathbf{ob}\mathcal{J}\}$ on $D$ whose vertex is $B$, there exists a unique morphism $f: B \to A$ that satisfies $\mu_j = \lambda_j f$ for any $j \in \mathbf{ob}\mathcal{J}$. The chart exchange or cone $\{\lambda_j: A \to D(j) \mid j \in \mathbf{ob}\mathcal{J}\}$ is the limit of $\mathcal{J}$ graph $D$:

![](img/456a7a56403cbb2b5f1a261793529a51_439_0.png)

![](img/456a7a56403cbb2b5f1a261793529a51_439_1.png)

**Definition 15.6.** $D: \mathcal{J} \to \mathcal{C}$ is a $\mathcal{J}$ graph, $A \in \mathbf{ob}\mathcal{C}$:
(1) If the morphism family $\{p_j: D(j) \to A \mid j \in \mathbf{ob}\mathcal{J}\}$ satisfies the condition that for any morphism $r: j \to j'$ in $\mathcal{J}$, $p_{j'} = p_j D(r)$, i.e., the chart exchange
then we call $\{p_j: D(j) \to A \mid j \in \mathbf{ob}\mathcal{J}\}$ a surcone on $D$, and $A$ is the vertex of this surcone.
(2) If $\{p_j: D(j) \to A \mid j \in \mathbf{ob}\mathcal{J}\}$ is a surcone on $D$, any surcone on $D$ is universal, i.e., for any $B \in \mathbf{ob}\mathcal{C}$ and surcone $\{q_j: D(j) \to B \mid j \in \mathbf{ob}\mathcal{J}\}$ on $D$ whose vertex is $B$, there exists a unique morphism $g: A \to B$ that satisfies $q_j = g p_j$ for any $j \in \mathbf{ob}\mathcal{J}$. The following chart exchange or surcone $\{p_j: D(j) \to A \mid j \in \mathbf{ob}\mathcal{J}\}$ is the colimit of $\mathcal{J}$ graph $D$:

![](img/456a7a56403cbb2b5f1a261793529a51_439_2.png)

![](img/456a7a56403cbb2b5f1a261793529a51_439_3.png)

## Definition 15.7. If $\mathscr{J} = (\cdot \to \cdot \leftarrow \cdot)$, then a $\mathscr{J}$ graph in $\mathscr{C}$ is

![](img/456a7a56403cbb2b5f1a261793529a51_440_0.png)

If the limit of the $\mathscr{J}$ graph exists, then we can call an exchangeable square in $\mathscr{C}$ as a pullback square, and $\overline{g}$ is the pullback of $g$ along $f$. Similarly, $\overline{f}$ is the pullback of $f$ along $g$.

![](img/456a7a56403cbb2b5f1a261793529a51_440_1.png)

We can see from the definition of the limit that a square in $\mathscr{C}$ is a pullback square if and only if it is exchangeable and there is a unique morphism $h: \hat{P} \to P$ satisfying $p = th, q = rh$ for any commutative square.

![](img/456a7a56403cbb2b5f1a261793529a51_440_2.png)

![](img/456a7a56403cbb2b5f1a261793529a51_440_3.png)

![](img/456a7a56403cbb2b5f1a261793529a51_440_4.png)

If any graph such as $A \to C \leftarrow B$ in category $\mathscr{C}$ has a limit, then we say that the category has a pullback.

## Definition 15.8. $F: \mathscr{C} \to \mathscr{D}$ is a functor, and $\mathscr{J}$ is a small category. If any $\mathscr{J}$ graph $D: \mathscr{J} \to \mathscr{C}$ in $\mathscr{C}$ has the limit $\{\Lambda_j: A \to D(j) | j \in ob\mathscr{J}\}$ satisfying the condition that $\{F(\Lambda_j): F(A) \to FD(j) | j \in ob\mathscr{J}\}$ is the limit of $\mathscr{J}$ graph $FD: \mathscr{J} \to \mathscr{D}$, then we say that functor $F$ maintains the limit of $\mathscr{J}$ graph.

For any small category $\mathscr{J}$, if $F$ maintains the limit of $\mathscr{J}$ graph, then we say that $F$ maintains the limit.

Specifically, if $F$ maintains the limit of $\mathscr{J} = (\cdot \to \cdot)$, then we say that $F$ keeps the equivalent. If $F$ keeps the limits of discrete graphs, then we say that $F$ keeps the product. If $F$ keeps the limit of $\mathscr{J} = (\cdot \to \cdot \leftarrow \cdot)$, then we say that $F$ keeps the pullback.

![](img/456a7a56403cbb2b5f1a261793529a51_441_0.png)

**Fig. 15.3:** Abstract structure diagram of learning problems.

## 15.1.4 Proposed problem

Through the study and research of machine learning and its representation, it is easy to see that the representation of a learning problem is still an important problem. There are still many problems to be solved in this field. This chapter mainly solves the following problems:

- (1) How should we express knowledge better and more effectively in learning problems? For artificial intelligence problems, any complex solution technology cannot be separated from two aspects; one is to express, and the other is to search. Search is a very rough method, and this paper attempts to use scientific mathematical methods to solve the search problem, i.e., mapping methods.
- (2) How do you express a learning problem with an abstract structure? This is also one of the problems that need to be studied. As shown in Figure 15.3, each learning problem can be represented by expressions. Each expression is a data structure, and the set of these data structures can be studied by the knowledge of category theory, thus forming an abstract structure of the learning problem. This abstract structure is conducive to further research and application.
- (3) How to improve the performance of existing learning algorithms and improve the efficiency and accuracy of learning algorithms effectively? In the process of mass data processing, a learning algorithm needs considerable amounts of time and space resources. How to solve the problem faster under the existing conditions is another direction that needs to be studied in the mapping of learning expressions.

Therefore, this chapter chooses category theory to study the representation of a learning system. Using category theory to describe machine learning representation problems has two advantages. First, machine learning representation problems can be transformed into mathematical problems for solving. Research on mathematical problems can be summarised as research on the mapping between certain types of mathematical objects, which naturally form a category of thought. Second, category theory is a mathematical theory used in algebraic geometry. In the field of machine learning research, the algebraic and geometric expression patterns of machine learning have long been pursued.

## 15.2 Category representation of learning expressions

Expression is not only one of the ways in which human beings communicate but also an important part of human activities. Human interaction is difficult to imagine if there is no interaction between human beings. According to the relation between cognitive science and machine learning, expression plays an equally important role in the study of machine learning, and the research of expressions is an important problem for machines.

An expression is the same type of data (such as constants, variables, and functions) connected in a meaningful way with some symbolic rules.

At present, the mature methods of expression mainly include the following: regular expressions, S-expressions, inverse Polish expressions, and Polish expressions. A regular expression is usually called a pattern. A string is used to describe or match a series of syntactic rules. The S-expression is an agreement to express semi-structured data in human readable text. The inverse Polish expression is a type of book order of expression introduced by Polish mathematician Jan Łukasiewicz in 1920. In the inverse Polish representation, all operators are placed behind operands, also known as postfix notation. In the Polish notation, operators are placed in front of operands, also known as prefix notation.

In the field of machine learning, the mapping mechanism between expressions is studied to abstract various data structures. Using category theory to study and generalise the links between structures makes it easier to solve the problem of learning, which is one of the main concerns of this paper.

Category theory is a mathematical theory that abstractly deals with the connection between mathematical structures. A category is a mathematical structure for grasping the nature of a class of mathematical objects (such as groups in group theory). The category theory maintains the stability of the learning system and the accuracy of the learning efficiency by using the constant morphism property of the object structure between the mathematical objects.

### 15.2.1 Category representation of machine learning systems

According to the framework of machine learning systems and the basic concepts of category theory, a definition of a machine learning category is given first.
