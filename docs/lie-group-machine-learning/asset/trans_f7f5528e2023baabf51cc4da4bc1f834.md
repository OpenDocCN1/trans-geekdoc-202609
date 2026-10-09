

# 图 6.2：$M_{1}$ 和 $M_{2}$ 的交换图。

**证明。** 唯一性很容易证明。接下来的证明关于存在性。

设 \(\{w_{i}\}\) 是左不变形式 \(1\) 的基，使得 \(\psi^{*}\) 为 \(\psi\) 的转置。在 \(G \times H\) 上，形式 \(1\) 为 \(\{\delta\pi_{1}(\psi^{*}(w_{i})) - \delta\pi_{2}(w_{i})\}\)，其中 \(\pi_{1}\) 和 \(\pi_{2}\) 分别是 \(G \times H\) 到 \(G\) 和 \(H\) 的标准投影。该形式保持不变，且生成的理想 \(\mathcal{I}\) 是一个微分理想。因此，通过 \((e, e)\in G \times H\) 的 \(\mathcal{I}\) 的最大连通积分流形 \(I\) 是 \(G \times H\) 的一个覆盖簇，其维数等于 \(G\) 的维数。换言之，它是一个覆盖同态。

假设 \(G\) 是单连通的，因此 \(\left.\pi_{1}\right|_{I}: I \to G\) 是一个同构。定义 \(\varphi: G \to H\) 为 \(\varphi = \pi_{2} \circ (\left.\pi_{1}\right|_{I})^{-1}\)。那么，\(\varphi\) 是一个李群同态，且 \(\delta\varphi(w_{i}) = \psi^{*}(w_{i})\)。因此，\(d\varphi = \psi\)，定理得证。

**推论 6.3。** 如果单连通李群 \(G\) 和 \(H\) 具有同构的李代数，则 \(G\) 和 \(H\) 是同构的。

阿多定理（Ado theorem）指出，对于每个李代数，存在某个 \(n\)，使得在 \(\operatorname{GL}(n, R)\) 中存在忠实表示。根据该定理，如果 \(\frak{g}\) 是一个李代数，则存在一个李群，特别是单连通李群，以 \(\frak{g}\) 为其代数。鉴于此结果，我们有以下结论：

**定理 6.7。** 代数同构与单连通李群同构之间存在一一对应关系。

**证明。** 如果存在两条曲线 \(\varphi_{i}: [0, a] \to M\) \((i = 1, 2)\)，满足 \(\varphi_{1}(0) = \varphi_{2}(0)\)，且 \(\varphi_{1}(a) = \varphi_{2}(a)\)，在 \(M\) 中具有共同的起点和终点，那么 \(M\) 是单连通的。设 \(f: \tilde{M} \to M\) 为可微覆盖。成为万能覆盖的必要且充分条件是 \(\tilde{M}\) 是单连通的。此外，连通流形 \(M\) 是单连通的必要且充分条件是其没有非平凡覆盖。换句话说，如果 \(f_{1}: M_{1} \to M\) 是 \(M\) 上的覆盖映射，则 \(f\) 必须是一个同胚映射。

设 \(f: M_{1} \to M_{2}\) 为可微覆盖，\(\varphi: [0, a] \to M_{2}\) 为 \(M_{2}\) 中的连续参数曲线，且 \(p\) 为 \(f^{-1}(\varphi(0))\) 中任意选取的点。那么，存在唯一的连续映射 \(\tilde{\varphi}: [0, a] \to M_{1}\)，使得 \(\tilde{\varphi}(0) = p\)，\(f \circ \tilde{\varphi} = \varphi\)，如下面的示意图所示，其中 \(\tilde{\varphi}\) 被称为 \(\varphi\) 的覆盖曲线。

**定义 6.8。** 设 \(p: M \to N\) 为覆盖映射，且 \(f: I \to N\) 为 \(N\) 上的一条道路。那么，\(f\) 可以唯一提升为 \(M\) 中的道路 \(g: I \to M\)，使得 \(p(g) = f\)。

```
Algorithm 6.1: Judge the covering group
// Judge whether Lie group M is the covering group of the connected group
// Input: Lie group M, N
// Output: {0,1}
Procedure IsCovergroup(M,N)
If Isconnect(M) then
    For do
        If f and // At any point in M, a neighbourhood through f mapping belongs to N //
        then return 1;
        else
        return 0;
    endif
    endfor
else return 0;
endif
endprocedure
```

根据前面的描述，李群与其李代数之间存在一一对应关系。由于连通李群和单连通覆盖群的连通群在等价意义下是唯一的，因此只需要找到李群的通用覆盖群，就可以解决一系列问题。群流形上的每个点都与群元素一一对应，群流形中任意两点之间的连接可以通过参数空间的连续变形转换为群上的等价曲线。只要找到所有不等价不可约表示的覆盖，就能找到相应的李群。

# 定理 6.8。

连通群 G 必须是连通的，且单连通覆盖群 $(\hat{G}, f)$ 被称为 G 的万能覆盖群。进一步地，当且仅当 G 本身是单连通李群时，f 才是同构。

接下来，我们给出李群万能覆盖群的算法，并将李群问题简化为其覆盖问题。

```
Algorithm 6.2: Universal covering group algorithm for connected Lie group SCCG
//Input: Connected Lie group G
//Output: Universal covering group of G and covering mapping m
Step 1: Take the unit frame $(U, f)$. Create point set $\bigcup_{m=1}^{\infty} \overline{m(U \times U \times \cdots \times U)}$ starting from $U$.
Step 2: Take the elements $(u_1, u_2, \dots, u_m)$ and $(v_1, v_2, \dots, v_p)$ of this point set. According to $u, v, uv \in U$, we have the role $(u, v) = uv$. Further, $(u_1, u_2, \dots, u_m)$ changes with a limited step; check whether it can become $(v_1, v_2, \dots, v_p)$;
Step 3: The equivalence class of the element that satisfies the equivalent condition is denoted by $(u_1, u_2, \dots, u_m)^*$. Continue to select other elements;
Step 4: Make all the equivalence classes that fit the equivalence relation into a set of $\hat{G}$.
Step 5: If the covering mapping $f: (u_1, u_2, \dots, u_m)^* \longrightarrow u_1 u_2 \cdots u_m$ is established between the equivalence class set and $(u_1, u_2, \dots, u_m)$, then $(\hat{G}, f)$ is the coverage group of G.
```

覆盖群的构造表明，$df$ 给出了 $\tilde{G}$ 的李代数与 $G$ 的李代数之间的同构。原因是，对于 $\tilde{G}$ 和 $G$ 的单位元 $\tilde{e}$ 和 $e$，存在邻域 $\tilde{U}$ 的三维坐标的邻域坐标系，使得 $f$ 是 $\tilde{U}$ 到 $U$ 的同胚映射，且 $df$ 给出了李代数的代数同构。

在找到连通李群的覆盖群之后，对于覆盖群的不相等不可约表示，我们必须首先找到它们的所有不等不可约特征标，并将特征标列作为特征表。然后，我们找到不可约表示矩阵。由于群元素可以表示为生成元的乘积，因此找到生成元的表示矩阵就足够了。实际上，标准表中不可约表示的通用群，即标准形式矩阵和分解直接表示的不可约表示矩阵，可以在书中找到，只需将其应用于学习问题即可。

### 6.2.3 算法设计

学习的目的是找到从初始状态到目标状态的最优路径。如果将每个状态称为节点，它们可以形成一个群空间。群空间是单连通的，即每个状态都可以到达另一个状态。在每个连通状态中，每条弧代表一个算子，可以将一个状态定向到另一个状态。当然，根据具体问题，可以为算子设置特定的代价。如果起点是从初始节点出发，且存在一条通向目标节点的路径，那么我们可以说该学习问题是可解的。从初始状态到目标状态的一条路径形成一个覆盖。

为了更好地描述现实世界的问题，我们可以将样本数据集 $D$ 映射到一个新的李群结构。然而，各个元素之间的关系将保持不变，对应于原始群元素。一方面，我们可以将 $D'$ 视为由 $D$ 生成的新样本集，即样本集 $D$ 的覆盖不改变其本质特征，从而确保覆盖映射的正确性。另一方面，对于两个同构的样本集 $D$ 和 $D'$，可以使用相同的道路划分方法，从而避免重复学习。

例如，对于人脸中的单个点（眼睛、鼻子、嘴巴等），选取一些样本点及其邻域点。样本点之间映射的连续覆盖保持了原始的邻域关系，即在原始空间中，相邻的样本点在映射后的群中仍然相邻。

由于两个李群具有局部同构，原始李群的拓扑性质得以保持（两者具有相同的李代数）。我们知道李代数代表了生成元之间的相互关系；因此，这些群也具有相同的生成元。同时，李代数可以被理解为一个集合

