
(2) Maximisation step: replace the current hypothetical object *H* with the maximum likelihood assumption object *H'* that maximises the object *Q*. Use the morphism representation as

$$g: Q \rightarrow H'$$

Here, morphism *f* can be reduced specifically to *f*: *E*[ln *P*(*Y*|*h*).* |h, X,*], and morphism *f'* can also be represented by morphism *f'*: $\int \log(L(\theta | X, y)) f(y | X, \theta')dy$. We can define that morphism *g* can be reduced to *g*: arg max${}_{h}^{'} Q$. Moreover, the object and the morphism of the machine learning domain satisfy the compound operation law, the combination law, and the unit morphism. Hence, the bias learning algorithm is also a machine learning category.

## 15.2.2 Category representation of learning expressions

First, we use categories to represent simple expressions, such as $y = x^2, x \in R$. The expression contains two sets: the defined domain and the range. Therefore, we can define two objects *A, B* in a category C, where the domain is defined as *A* and the range is expressed as *B*, and the expression can be represented as a category:

$$f: A \mapsto B \quad , \quad f \text{ is the corresponding morphism to } \mathfrak{C}(A, B) \quad . \quad (15.1)$$

For expressions in learning problems, we can obtain them progressively from the standard description of the learning problem. In [1], *T* and the performance metrics for a class of tasks *P* have been defined. If a computer program on *T* uses *P* to measure its performance as the experience *E*, then the computer program is said to be learning from the experience *E*. We can simplify the learning task into an operable description of the discovery of an ideal objective function, which can be done in the form of a learning expression.

The object *A* is the initial state set of the training sample, the object *B* is the intermediate state, and the object *M* is the final output state. Then, the learning process can be expressed as

$$f: A \mapsto B, g: B \mapsto C \quad . \quad (15.2)$$

*f, g* is the morphism of the corresponding objects. According to the complex operation law and the combination law of category,

$$gf: A \mapsto C \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (15.3)$$

![](img/456a7a56403cbb2b5f1a261793529a51_446_0.png)

The following is a linear expression to complete the learning process, e.g., to illustrate the category representation of learning expressions.

$f: W \times X \mapsto B$                                        (15.4)
$g: B \mapsto M$                                                   (15.5)
$h: B \times M \mapsto W.$                                (15.6)

Explanation: By (15.1), (15.4), and (15.5), the initial weight object *W* and the initial state object *X* are mappings by morphism *f* to get the intermediate state object *B*, and the intermediate state object *B* gets the end state object *M* by morphism g. By (15.4), (15.5), and (15.6), the minimum error is used to recalculate the weight and update the weight object to complete a round of the learning process.

Linear expressions can be linear equations or linear inequalities, and the learning process using linear expressions is called linear expression learning. We can see from the literature [16] that maximisation or minimisation of a linear function by a linear equality or inequality is a type of linear programming technique. It is assumed that the object *U* is an unknown object, which can be obtained by minimising the state of the linear objective function *f*, which is an $m \times 1$ vector of known cost objects *A*, $f: A \to U$, namely $z_{\min} = a^T \cdot u$, and $Bu \ge \beta$ holds, where object *B* consists of an $l \times m$ matrix and $\beta$ is an $l \times 1$ vector. Hence, this linear programming can be expressed as a category $\mathcal{A}$ of learning expressions. Figure 15.5 shows the transformations and relationships between the objects and the morphism. The surface of $z_{\min} = a^T \cdot u$ is shown in grey. The surface of $Bu \ge \beta$ is shown in red. The unknown objects *U* are obtained by iterating the morphism *f* and the constraints.

![](img/456a7a56403cbb2b5f1a261793529a51_447_0.png)

**Fig. 15.5:** Simple iteration of linear programming in the category of learning expressions.

## 15.2.3 Category Representation of the Learning Expression Functor

From the last section, we can see that the learning process can be expressed as an abstract algebraic structure of the category of learning expressions. Different learning processes belong to the same algebraic structure. Thus, there is a homomorphic relation between different learning processes, which forms the mapping mechanism between expressions, namely existence mapping $\varphi: X \to Y$ satisfies $\varphi (u \cdot v) = \varphi (u) \cdot \varphi (v)$.

**Definition 15.10.** Suppose that $\mathbb{C}$ and $\mathbb{D}$ are a learning expression category. A learning expression functor $F : \mathbb{C} \to \mathbb{D}$ consists of two mappings:

$\mathrm{ob} \mathbb{C} \to \mathrm{ob} \mathbb{D} : A \mapsto F(A)$ (15.7)

$\mathrm{Mor} \mathbb{C} \to \mathrm{Mor} \mathbb{D} : f \mapsto F(f)$ (15.8)

Explanation:

- (1) represents the mapping between objects in two categories of learning expressions, mapping each object $A$ that belongs to $\mathbb{C}$ to another object $B$ that belongs to $\mathbb{D}$, $B = F(A)$;
- (2) represents the mapping between morphisms in two learning expression categories, mapping each morphism $f$ belonging to $\mathbb{C}$ to another morphism $g$ belongs to $\mathbb{D}$, which can be represented as $g = F(f)$, and satisfies $F(gf) = F(g)F(f)$.

$\mathbb{C}$, $\mathbb{D}$ are learning expressions, and $F : \mathbb{C} \to \mathbb{D}$ is a learning expression functor. For any pair of objects $A, B$ in $\mathbb{C}$ and $f, g \in \mathbb{C}(A, B)$, we have

$F(f) = F(g) \Rightarrow f = g$

i.e., $F$ locates in $\mathbb{C}(A, B)$. If $\mathbb{C}(A, B) \to \mathbb{D}(F(A), F(B))$ is a single shot, then learning expression functor $F$ is a faithful learning expression functor.

If for any $g \in \mathbb{D}(F(A), F(B))$, there is $f \in \mathbb{C}(A, B)$ satisfying $F(f) = g$, i.e., $F$ locates in $\mathbb{C}(A, B)$, further, if $\mathbb{C}(A, B) \to \mathbb{D}(F(A), F(B))$ is a full shot, then learning expression functor $F$ is a full learning expression functor.

**Theorem 15.2.** There are functors between learning expression categories.

*Proof.* Let $\mathbb{C}, \mathbb{D}$ be learning expression categories. $W, X, B, M \in \mathrm{ob}\mathbb{C}$, $W', X', B'$, $M' \in \mathrm{ob}\mathbb{D}$, $f, g, h' \in \mathrm{Mor}\mathbb{C}$, $f', g', h' \in \mathrm{Mor}\mathbb{D}$. The objects in the category of learning expressions are determined by the set of training samples, and condition (15.7) is obvious:

$(W, X, B, M) \to F (W', X', B', M')$ .

Assume that $\cdot$ is the operator between morphisms, and mapping $F: X \to Y$ satisfies $F(u \cdot v) = F(u) \cdot F(v)$.

```
\begin{align*}
F(f \cdot f') &= F\left(\left(W \times X \to B\right) \cdot \left(W' \times X' \to B'\right)\right) \\
&= F\left(\left(W \times X \to B\right) \cdot \left(F(W) \times F(X) \to F(B)\right)\right) \\
&= F\left(W \times X \to B\right) \cdot F\left(F(W) \times F(X) \to F(B)\right) \\
&= F(f) \cdot F(f')
\end{align*}
```

Thus, learning expressions satisfy morphism mappings.

In summary, there are learning expression functors between two learning expression categories, i.e., there are mappings in category theory between learning expression categories. This provides a theoretical basis for further research on the mapping mechanism between learning expression categories.

## 15.2.4 Natural transformation

As can be seen from the previous section, the expression of the functor is studied to investigate the relationship between expressions of category learning. However, there exists relations between categories and between functors. Therefore, this section mainly introduces the study of relations between the expressions of functors, called natural transformation.

**Definition 15.11.** $\mathcal{C}$ and $\mathcal{D}$ are learning expression categories, and $F: \mathcal{C} \to \mathcal{D}$ and $G: \mathcal{C} \to \mathcal{D}$ are two functors corresponding to the learning expression categories. A natural Transformation $\alpha: F \to G$ is a mapping $\mathrm{ob}\mathcal{C} \to \mathrm{Mor}\mathcal{D}$:

$[ A \mapsto (\alpha_A: F(A) \to G(A)), A \in \mathrm{ob}\mathcal{C}, ]$

such that for any morphism $f: A \to B$ in $\mathcal{C}$, we have $G(f)\alpha_A = \alpha_B F(f)$, i.e., the following icon exchange:

![](img/456a7a56403cbb2b5f1a261793529a51_449_0.png)

**Example 15.4.** The classifier based on Bayesian decision theory obtains more forms and more methods through natural transformation, so that the classifier can be optimised.

By the definition of machine learning category, we can see that the classifier in the category is category $\mathcal{C}$. Data sets, feature vectors, prior probabilities, posterior prob-
