we aggregate need not be fixed to be n; rather it equals the number of gradients the server chooses to aggregate at any given iteration. Furthermore, as the indices can be assigned arbitrarily to the nodes, the output of an aggregation rule is usually oblivious to the order of the input vectors g_t^(1),..., g_t^(n). In other words, for any permutation mapping τ : [n] → [n], we have

F(g_t^(1),..., g_t^(n)) = F(g_t^(τ(1)),..., g_t^(τ(n))). (4.1)

Lastly, note that, because adversarial nodes might deviate from the algorithm, the instructions of Robust DMGD only apply to honest nodes. Throughout this chapter, we denote the set of honest nodes by H ⊆ [n]. It is important to note that the identity of H (i.e., the honest nodes) remains a priori unknown to the server; otherwise, the problem of robustness is rendered trivial. We present in Algorithm 5 the schematic of Robust DMGD with a generic aggregation rule F.

# Algorithm 5 Robust DMGD

The server initializes the procedure by choosing an initial model θ1 ∈ R^d, which can be done in a manner similar to the DMGD method described in Chap. 3. In each iteration t ∈ {1,2,...}, the server maintains a model parameter θt that is broadcast to all the nodes. The rest of the iteration is as follows:

+   1. Local Phase. Each honest node i ∈ H independently and randomly samples a set of b data points, denoted by S_t^(i), from the local training sample S_t (without replacement), and computes the local gradient estimate
+   
+   g_t^(i) := 1/b Σ_(x,y)∈S_t^(i) ∇_θ ℓ(h_θt(x), y). (4.2)
+   
+   2. Global Phase. Each node i returns to the server a gradient g_t^(i). If node i is honest, then g_t^(i) is computed as per (4.2). Otherwise, g_t^(i) can be an arbitrary vector in R^d. Upon receiving the gradients from all the nodes, the server computes their aggregate
+   
+   ĝ_t := F(g_t^(1),..., g_t^(n)). (4.3)
+   
+   Using the aggregate gradient ĝ_t, the server updates the current model θ_t to
+   
+   θ_{t+1} := θ_t - γ_t ĝ_t,
+   
+   where γ_t is the learning rate at iteration t.