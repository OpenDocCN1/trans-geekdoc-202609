
## 1.4. Convolutional ANNs (CNNs)

Exercise 1.4.2. Let
\begin{align*} \Phi = \left( \left( (W_{1,n,m})_{(n,m) \in \{1,2,3\} \times \{1\}}, (B_{1,n})_{n \in \{1,2,3\}}, \right. \right. \left. \left. ((W_{2,n,m})_{(n,m) \in \{1\} \times \{1,2,3\}}, (B_{2,n})_{n \in \{1\}}) \right) \in ((\mathbb{R}^{3}^{3 \times 1} \times \mathbb{R}^{3}) \times ((\mathbb{R}^{2})^{1 \times 3} \times \mathbb{R}^{1}) \end{align*} \
\tag{1.29}

satisfy
\begin{equation} W_{1,1,1} = (1,1,1), \quad W_{1,2,1} = (2, -2, -2), \end{equation} \tag{1.30}
\begin{equation} W_{1,3,1} = (-3, -3, 3), \quad (B_{1,n})_{n \in \{1,2,3\}} = (3, -2, -1), \end{equation} \tag{1.31}
\begin{equation} W_{2,1,1} = (2, -1), \quad W_{2,1,2} = (-1, 2), \quad W_{2,1,3} = (-1, 0), \text{ and } B_{2,1} = -2 \end{equation} \tag{1.32}

and let $v \in \mathbb{R}^{9}$ satisfy $v = (1, -1, 1, -1, 1, -1, 1, -1, 1)$. Specify
\begin{equation} \langle \mathcal{R}_{\Phi}^{\mathbf{C}} \rangle(v) \end{equation} \tag{1.33}

explicitly and prove that your result is correct (cf. Definitions 1.2.4 and 1.4.5)!

Exercise 1.4.3. Prove or disprove the following statement: For every $a \in \mathcal{C} \in \mathbb{R} \in \mathbb{R}$, $\Phi \in \mathbb{N}$ there exists $\Psi \in \mathbf{C}$ such that for all $x \in \mathbb{R}^{\mathcal{I}(\Phi)}$ it holds that $\mathbb{R}^{\mathcal{I}(\Phi)} \subseteq \operatorname{Domain}(\mathcal{R}_{a}^{\Psi})$ and
\begin{equation} \langle \mathcal{R}_{a}^{\mathbf{C}}(\Psi) \rangle(x) = \langle \mathcal{R}_{a}^{\mathbf{N}}(\Phi) \rangle(x) \end{equation} \tag{1.34}

(cf. Definitions 1.3.1, 1.3.4, 1.4.2, and 1.4.5).

Definition 1.4.7 (Standard scalar products). We denote by $\langle \cdot, \cdot \rangle : [\coprod_{d \in \mathbb{N}} (\mathbb{R}^{d} \times \mathbb{R}^{d})] \to \mathbb{R}$ the function which satisfies for all $d \in \mathbb{N}$, $x = (x_{1}, x_{2}, \dots, x_{d})$, $y = (y_{1}, y_{2}, \dots, y_{d}) \in \mathbb{R}^{d}$ that
\begin{equation} \langle x, y \rangle = \sum_{i=1}^{d} x_{i} y_{i}. \end{equation} \tag{1.35}

Exercise 1.4.4. For every $d \in \mathbb{N}$ let $\mathbf{e}_{1}^{(d)}, \mathbf{e}_{2}^{(d)}, \dots, \mathbf{e}_{d}^{(d)} \in \mathbb{R}^{d}$ satisfy $\mathbf{e}_{1}^{(d)} = (1, 0, \dots, 0)$, $\mathbf{e}_{2}^{(d)} = (0, 1, 0, \dots, 0)$, $\dots$, $\mathbf{e}_{d}^{(d)} = (0, \dots, 0, 1)$. Prove or disprove the following statement: For all $a \in \mathcal{C} \in \mathbb{R} \in \mathbb{R}$, $\Phi \in \mathbf{N}$, $D \in \mathbb{N}$, $x = ((x_{i,j})_{j \in \{1,2,\dots,D\}})_{i \in \{1,2,\dots,I(\Phi\}} \in (\mathbb{R}^{D})^{I(\Phi)}$ it holds that
\begin{equation} \langle \mathcal{R}_{a}^{\mathbf{C}}(\Phi) \rangle(x) = \langle (\langle \mathbf{e}_{k}^{(\sigma(\Phi))}, \langle \mathcal{R}_{a}^{\mathbf{N}}(\Phi) \rangle(x_{i,j})_{j \in \{1,2,\dots,I(\Phi)\}} \rangle)_{j \in \{1,2,\dots,D\}} \rangle_{k \in \{1,2,\dots,\sigma(\Phi\}} \end{equation} \tag{1.36}

(cf. Definitions 1.3.1, 1.3.4, 1.4.5, and 1.4.7).

## 1.5 Residual ANNs (ResNets)

In this section we review ResNets. Roughly speaking, plain-vanilla feedforward ANNs can be seen as having a computational structure consisting of sequentially chained layers in which each layer feeds information forward to the next layer (cf., for example, Definitions 1.1.3 and 1.3.4 above). ResNets, in turn, are ANNs involving so-called skip connections in their computational structure, which allow information from one layer to be fed not only to the next layer, but also to other layers further down the computational structure. In principle, such skip connections can be employed in combinations with other ANN architecture elements, such as fully-connected layers (cf., for instance, Sections 1.1 and 1.3 above), convolutional layers (cf., for example, Section 1.4 above), and recurrent structures (cf., for instance, Section 1.6 below). However, for simplicity we introduce in this section in all mathematical details feedforward fully-connected ResNets in which the skip connection is a learnable linear map (see Definitions 1.5.1 and 1.5.4 below).

ResNets were introduced in He et al. [190] as an attempt to improve the performance of deep ANNs which typically are much harder to train than shallow ANNs (cf., for example, [30, 153, 328]). The ResNets in He et al. [190] only involve skip connections that are identity mappings without trainable parameters, and are thus a special case of the definition of ResNets provided in this section (see Definitions 1.5.1 and 1.5.4 below). The idea of skip connection (sometimes also called shortcut connections) has already been introduced before ResNets and has been used in earlier ANN architecture such as the highway nets in Srivastava et al. [384, 385] (cf. also [264, 293, 345, 390, 398]). In addition, we refer to [191, 206, 404, 417, 427] for a few successful ANN architectures building on the ResNets in He et al. [190].

### 1.5.1 Structured description of fully-connected ResNets

Definition 1.5.1 (Structured description of fully-connected ResNets). We denote by $\mathbf{R}$ the set given by
$$\mathbf{R} = \bigcup_{L \in \mathbb{N}} \bigcup_{n_0, l_1, \dots, l_L \in \mathbb{N}} \bigcup_{S \subseteq \{(r,k) \in \mathbb{N}_0: r < k \le L \}} \left( \bigtimes_{k=1}^{L} (\mathbb{R}^{l_k \times l_{k-1}} \times \mathbb{R}^{l_k}) \right) \times \left( \bigtimes_{(r,k) \in S} \mathbb{R}^{l_k \times l_r} \right) \tag{1.137}$$

Definition 1.5.2 (Fully-connected ResNets). We say that $\Phi$ is a fully-connected ResNet if and only if it holds that
$$\Phi \in \mathbf{R} \quad \tag{1.138}$$
(cf. Definition 1.5.1).

**Lemma 1.5.3** (On an empty set of skip connections). Let $L \in \mathbb{N}$, $l_{0}, l_{1}, \ldots, l_{L} \in \mathbb{N}$, $S \subseteq\left\{(r, k) \in\left(\mathbb{N}_{0}\right)^{2}: r<k \leq L\right\}$. Then
$$\#\left(\prod_{(r, k) \in S} \mathbb{R}^{l_{k} \times l_{r}}\right)=\begin{cases}1 & : S=\emptyset \\ \infty & : S \neq \emptyset .\end{cases} \tag{1.139}$$

Proof of Lemma 1.5.3. Throughout this proof, for all sets $A$ and $B$ let $F(A, B)$ be the set of all functions from $A$ to $B$. Note that
$$\#\left(\prod_{(r, k) \in S} \mathbb{R}^{l_{k} \times l_{r}}\right)=\#\left\{f \in F\left(S, \cup_{(r, k) \in S} \mathbb{R}^{l_{k} \times l_{r}}\right) : \forall(r, k) \in S: f(r, k) \in \mathbb{R}^{l_{k} \times l_{r}}\right\} . \tag{1.140}$$

This and the fact that for all sets $B$ it holds that $\#(F(\emptyset, B)) = 1$ ensure that
$$\#\left(\prod_{(r, k) \in \emptyset} \mathbb{R}^{l_{k} \times l_{r}}\right)=\#(F(\emptyset, \emptyset))=1 . \tag{1.141}$$

Next note that $(1.140)$ assures that for all $(R, K) \in S$ it holds that
$$\#\left(\prod_{(r, k) \in S} \mathbb{R}^{l_{k} \times l_{r}}\right) \geq \#\left(F\left(\left\{\{(R, K)\right\}, \mathbb{R}^{\{K\} \times \{L R\}}\right)\right)=\infty . \tag{1.142}$$

Combining this and $(1.141)$ establishes $(1.139)$. The proof of Lemma 1.5.3 is thus complete. $\Box$

### 1.5.2 Realizations of fully-connected ResNets

**Definition 1.5.4** (Realizations associated to fully-connected ResNets). Let $L \in \mathbb{N}, l_{0}, l_{1}$, $\ldots, l_{L} \in \mathbb{N}, S \subseteq\left\{(r, k) \in\left(\mathbb{N}_{0}\right)^{2}: r<k \leq L\right\}, \Phi=\left(\left(W_{k}, B_{k}\right)_{k \in\{1,2, \ldots, L\}},\left(V_{r, k}\right)_{(r, k) \in S}\right) \in$ $\left(\prod_{k=1}^{L}\left(\mathbb{R}^{l_{k} \times l_{k-1}} \times \mathbb{R}^{l_{k}}\right)\right) \times\left(\prod_{(r, k) \in S} \mathbb{R}^{l_{k} \times l_{r}}\right) \subseteq \mathbf{R}$ and let $a : \mathbb{R} \rightarrow \mathbb{R}$ be a function. Then we denote by
$$\mathcal{R}_{a}^{\mathbf{R}}(\Phi): \mathbb{R}^{l_{0}} \rightarrow \mathbb{R}^{l_{L}} \tag{1.143}$$
the function which satisfies for all $x_{0} \in \mathbb{R}^{l_{0}}, x_{1} \in \mathbb{R}^{l_{1}}, \ldots, x_{L} \in \mathbb{R}^{l_{L}}$ with
$$\forall k \in\{1,2, \ldots, L\}:$$
$$x_{k}=\mathfrak{M}_{a \mathbf{1}_{\{0, L\}}(k) + \operatorname{idx}_{\{1, L\}}(k)} W_{k}\left(W_{k} x_{k-1} + B_{k} + \sum_{r \in \mathbb{N}_{0}, (r, k) \in S} V_{r, k} x_{r}\right) \tag{1.144}$$
that
$$(\mathcal{R}_{a}^{\mathbf{R}}(\Phi))(x_{0})=x_{L} \tag{1.145}$$
and we call $\mathcal{R}_{a}^{\mathbf{R}}(\Phi)$ the realization function of the fully-connected ResNet $\Phi$ with activation function $a$ (we call $\mathcal{R}_{\boldsymbol{a}}^{\mathbf{R}}(\Phi)$ the realization of the fully-connected ResNet $\Phi$ with activation $a$) (cf. Definitions 1.2.1 and 1.5.1).
