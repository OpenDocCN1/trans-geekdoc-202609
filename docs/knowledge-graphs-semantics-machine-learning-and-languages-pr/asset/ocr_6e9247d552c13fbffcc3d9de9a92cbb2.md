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

**Hardware & Software.** All experiments were conducted on the *Noctua*⁵ cluster of the *Paderborn university*. Noctua consists of 256 compute nodes, each having two Intel Xeon Gold "Skylake" 6148 processors, which comes to a total of 40 cores with 2.4 GHz and 192 GiB main memory. All used algorithms were implemented in *Java*, and the compute nodes ran on *OpenJDK* version 11.0.2. For accurate runtime measurement, all experiments were started with all datasets already loaded into the main memory. Additionally, for linking each dataset pair, we ran the algorithms on the same compute node. All experiments were conducted with a memory limit of 30 GB. Unless otherwise stated, we use only one core for all the experiments.

**Experiments Settings.** We use Cobalt_area, Cobalt_diagonal and Cobalt_mixed to dub the *area*, *diagonal* and the *mixed* measures of Cobalt, respectively. We use the following four baselines: i) Radon [5], ii) Radon with only the MBBs of the original polygons (dubbed Radon_MBB), iii) Gia.nt [7] and iv) Gia.nt with only the MBBs of the original polygons (dubbed Gia.nt_MBB). For a fair runtime comparison, we use a version of Gia.nt that computes only one relation at a time. We also implemented a space-indexing-based version of Cobalt, where we optimized the content-based measures based on the space tiling indexing of Radon [5]. We use Cobalt_area(R), Cobalt_diagonal(R) and Cobalt_mixed(R) to dub the *area*, *diagonal* and the *mixed* measures of the space-tiling-based indexing measures of Cobalt, respectively. We also used the *Douglas-Peucker* polygon simplification algorithm [21]. The simplification is ap-