(2) Maximisation step: replace the current hypothetical object *H* with the maximum likelihood assumption object *H'* that maximises the object *Q*. Use the morphism representation as

$$g: Q \rightarrow H'$$

Here, morphism *f* can be reduced specifically to *f*: *E*[ln *P*(*Y*|*h*.)* |h, X,*], and morphism *f'* can also be represented by morphism *f'*: $\int \log(L(\theta | X, y)) f(y | X, \theta')dy$. We can define that morphism *g* can be reduced to *g*: arg max${}_{h}^{'} Q$. Moreover, the object and the morphism of the machine learning domain satisfy the compound operation law, the combination law, and the unit morphism. Hence, the bias learning algorithm is also a machine learning category.

# 15.2.2 Category representation of learning expressions

First, we use categories to represent simple expressions, such as $y = x^2, x \in R$. The expression contains two sets: the defined domain and the range. Therefore, we can define two objects *A, B* in a category C, where the domain is defined as *A* and the range is expressed as *B*, and the expression can be represented as a category:

$$f: A \mapsto B \quad , \quad f \text{ is the corresponding morphism to } \mathfrak{C}(A, B) \quad . \quad (15.1)$$

For expressions in learning problems, we can obtain them progressively from the standard description of the learning problem. In [1], *T* and the performance metrics for a class of tasks *P* have been defined. If a computer program on *T* uses *P* to measure its performance as the experience *E*, then the computer program is said to be learning from the experience *E*. We can simplify the learning task into an operable description of the discovery of an ideal objective function, which can be done in the form of a learning expression.

The object *A* is the initial state set of the training sample, the object *B* is the intermediate state, and the object *M* is the final output state. Then, the learning process can be expressed as

$$f: A \mapsto B, g: B \mapsto C \quad . \quad (15.2)$$

*f, g* is the morphism of the corresponding objects. According to the complex operation law and the combination law of category,

$$gf: A \mapsto C \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (15.3)$$

![](bbox=[0.42, 0.84, 0.57, 0.89])