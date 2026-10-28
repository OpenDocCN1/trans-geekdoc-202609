
## Algorithm 1 DiscoverLinksAreaBased(Gₛ, Gₜ, r)
```
1: Input: Source KG Gₛ, Target KG Gₜ, Topological relation r
2: Output: Mapping : M = {(s,r,t) | s ∈ Gₛ, t ∈ Gₜ}
3: tree ← buildRtree(Gₛ)
4: Initialise M ← {}
5: for each MBB(t) t ∈ Gₜ do
6:   I ← queryRtree(tree, t)
7:   if r is disjoint then
8:     Add all pairs(s,r,t) ∀ s ∈ (Gₛ \ I) to M
9:   end if
10: for each MBB(s) s ∈ I do
11:   X ← Fₐ(MBB(s),MBB(t))
12:   Y ← Fₐ(MBB(t),MBB(s))
13:   Z ← X + Y
14:   if X,Y,Z match the respective values of the relation r in Table 1 then
15:     Add (s,r,t) to M
16:   end if
17: end for
18: end for
19: return M
```

## Algorithm 2 MatchTrees(sourceTree, targetTree)
```
1: Result ← {}
2: if area(sourceTree) < area(targetTree) then
3:   swap sourceTree and targetTree
4: end if
5: for each child of sourceTree do
6:   if child is leaf then
7:     Result = Result ∪ queryRtree(targetTree, MBB(child))
8:   else
9:     Result = Result ∪ MatchTrees(child, targetTree)
10:  end if
11: end for
12: return Result
```

## Indexing both Datasets.
In many cases swapping the source and target datasets results in different runtimes. In order to reduce the impact of dataset ordering on the runtime, we study the possibility of indexing both datasets instead of one. Instead of querying the R-tree for each target geometry, we use Algorithm 2 to match two R-trees to each other and recursively find all pairs that intersect. This approach removes the need to choose which dataset to index but comes with the price of increasing the memory footprint of our approach as we have to keep both datasets in memory.

## Splitting Polygons to Gain Accuracy.
We are able to improve the F-Measure of COBALT for some relations by splitting the geometries into multiple pieces before using the content measure functions to determine the relation. In particular, we split polygons recursively t times into four pieces using two different strategies: 1) Equal split, where

![](img/5368dd329bd72fa0bf97ac91d6cef632_198_0.png)

(a) Splitting the polygon into equal size parts two times　　　　　　　　　(b) Splitting the polygon into fitting parts two times

**Figure 3.** Different options to split polygons. The green triangle is the original polygon, the dark red lines are the splitting lines for the first split iteration, the light red lines are the splitting lines for the second split iteration. The blue rectangles indicate the MBB used for determining the second iteration splitting lines of the top left corner.

we are splitting the original polygon into equally sized parts. The resulting polygon parts are the intersection of a grid pattern over the original polygon and the original polygon itself. In some cases, this leads to some splits not achieving any additional information as their parts of the grid are empty. For instance in Figure **3a**, any further splits of the top left corner cell (the blue highlighted cell) would not increase the accuracy of **CoBALT** as the original polygon does not have any points within this cell. **2) Fitting split**, where we divide the polygon into equally sized parts but using the MBB of the current polygon part for further splitting. Splitting the top left corner cell of the same polygon of the previous example using this strategy will result in the splitting presented in Figure **3b**, where further splitting of the blue highlighted cell results in more detailed splits that fit better to the shape of the polygon. After splitting the polygons we compute the MBBs for all parts. Now as we have multiple polygon parts, we change the way the relation of the original polygon is determined. Let *t* be the number of splits into four parts. Let $A_{(i,j)}$ be the split part of geometry *A* at column *i* and row *j* and $B_{(k,l)}$ be the split part of geometry *B* at column *k* and row *l* for $\{(i,j,k,l) \in \mathbb{N}^{4} \mid 0 \leq i,j,k,l < 2^{t}\}$. The newly defined relations can be found in Table 2. In particular, every grid pattern $A_{(i,j)}$ must be equal to $B_{(k,l)}$ for the equals relation to hold. For the intersects relation, at least one $A_{(i,j)}$ has to intersect with at least one $B_{(k,l)}$. For the within relation, all $A_{(i,j)}$ have to be contained in the MBB of the union of all $B_{(k,l)}$ it intersects. For the contains relation, we swap *A* and *B* and then compute our relation instead. For the overlaps relation, the following three conditions must hold: 1) at least one $A_{(i,j)}$ is not within *B*, 2) at least one $B_{(k,l)}$ is not within *A*, and 3) at least one $A_{(i,j)}$ intersects with at least one $B_{(k,l)}$. For the touches relation, at least one $A_{(i,j)}$ must touch any $B_{(k,l)}$ and every $A_{(i,j)}$ is related to every $B_{(k,l)}$ by either touches or disjoint relation.

## 4. Evaluation & Results

### Datasets
We use two real-world datasets for evaluating **CoBALT**: 1) The *NUTS*<sup>2</sup> dataset from the *Eurostat* group describes the territory of countries in the European Union, (potential) candidate countries and countries belonging to the European Free

<sup>2</sup> https://ec.europa.eu/eurostat/de/web/gisco/geodata/reference-data/administrative-units-statistical-units/NUTS, accessed on 01.09.2022

| Relation | Definition |
|---|---|
| equals | ∀ {(i, j) ∈ ℕ²\|0 ≤ i, j < 2ᵗ}: A₍ᵢ,ⱼ₎ equals B₍ᵢ,ⱼ₎ |
| intersects | ∃ {(i, j, k, l) ∈ ℕ⁴\|0 ≤ i, j, k, l < 2ᵗ}: A₍ᵢ,ⱼ₎ intersects B₍ₖ,ₗ₎ |
| disjoint | ∀ {(i, j, k, l) ∈ ℕ⁴\|0 ≤ i, j, k, l < 2ᵗ}: A₍ᵢ,ⱼ₎ disjoint B₍ₖ,ₗ₎ |
| within | ∀ {(i, j) ∈ ℕ²\|0 ≤ i, j < 2ᵗ}: A₍ᵢ,ⱼ₎ within MBB({B₍ₖ,ₗ₎\|∀(k, l) ∈ ℕ²\|0 ≤ k, l < 2ᵗ}: A₍ᵢ,ⱼ₎ intersects B₍ₖ,ₗ₎}) |
| contains | swap A and B then compute within |
| overlaps | (∃ {(i, j, k, l) ∈ ℕ⁴\|0 ≤ i, j, k, l < 2ᵗ}: A₍ᵢ,ⱼ₎ equals B₍ₖ,ₗ₎) ∨ A₍ᵢ,ⱼ₎ within B₍ₖ,ₗ₎) ∨ A₍ᵢ,ⱼ₎ contains B₍ₖ,ₗ₎) ∨ A₍ᵢ,ⱼ₎ overlaps B₍ₖ,ₗ₎) ∧ (∃ {(i, j) ∈ ℕ²\|0 ≤ i, j < 2ᵗ}: A₍ᵢ,ⱼ₎ ¬within MBB({B₍ₖ,ₗ₎\|∀(k, l) ∈ ℕ²\|0 ≤ k, l < 2ᵗ}: A₍ᵢ,ⱼ₎ intersects B₍ₖ,ₗ₎})) ∧ (∃ {(i, j) ∈ ℕ²\|0 ≤ i, j < 2ᵗ}: B₍ᵢ,ⱼ₎ ¬within MBB({A₍ₖ,ₗ₎\|∀(k, l) ∈ ℕ²\|0 ≤ k, l < 2ᵗ}: B₍ᵢ,ⱼ₎ intersects A₍ₖ,ₗ₎})) |
| touches | (∃ {(i, j, k, l) ∈ ℕ⁴\|0 ≤ i, j, k, l < 2ᵗ}: A₍ᵢ,ⱼ₎ touches B₍ₖ,ₗ₎) ∧ ¬(∃ {(i, j, k, l) ∈ ℕ⁴\|0 ≤ i, j, k, l < 2ᵗ}: A₍ᵢ,ⱼ₎ equals B₍ₖ,ₗ₎) ∨ A₍ᵢ,ⱼ₎ within B₍ₖ,ₗ₎) ∨ A₍ᵢ,ⱼ₎ contains B₍ₖ,ₗ₎) ∨ A₍ᵢ,ⱼ₎ overlaps B₍ₖ,ₗ₎) |

**Table 2.** Topological relations based on multiple splits of polygons.

Trade Association. 2) The *Corine Land Cover (CLC)*³ [20] created by the *European Environment Agency*. CLC contains information about the land use of the 39 EEA39 countries⁴.

### Hardware & Software
All experiments were conducted on the *Noctua*⁵ cluster of the *Paderborn university*. Noctua consists of 256 compute nodes, each having two Intel Xeon Gold "Skylake" 6148 processors, which comes to a total of 40 cores with 2.4 GHz and 192 GiB main memory. All used algorithms were implemented in *Java*, and the compute nodes ran on *OpenJDK* version 11.0.2. For accurate runtime measurement, all experiments were started with all datasets already loaded into the main memory. Additionally, for linking each dataset pair, we ran the algorithms on the same compute node. All experiments were conducted with a memory limit of 30 GB. Unless otherwise stated, we use only one core for all the experiments.

### Experiments Settings
We use Cobalt_area, Cobalt_diagonal and Cobalt_mixed to dub the *area*, *diagonal* and the *mixed* measures of Cobalt, respectively. We use the following four baselines: i) Radon [5], ii) Radon with only the MBBs of the original polygons (dubbed Radon_MBB), iii) Gia.nt [7] and iv) Gia.nt with only the MBBs of the original polygons (dubbed Gia.nt_MBB). For a fair runtime comparison, we use a version of Gia.nt that computes only one relation at a time. We also implemented a space-indexing-based version of Cobalt, where we optimized the content-based measures based on the space tiling indexing of Radon [5]. We use Cobalt_area(R), Cobalt_diagonal(R) and Cobalt_mixed(R) to dub the *area*, *diagonal* and the *mixed* measures of the space-tiling-based indexing measures of Cobalt, respectively. We also used the *Douglas-Peucker* polygon simplification algorithm [21]. The simplification is ap-
