# 12.3. Empirical risk minimization

+   (i) it holds for all x ∈ E that 𝔼[|Zₓ|] ≤ D < ∞,

+   (ii) it holds that Ω ∋ η ↦ sup_{x∈E}|Zₓ(η) − 𝔼[Zₓ]| ∈ [0, ∞] is ℱ/ℬ([0, ∞])−measurable, and

+   (iii) it holds that
𝔼(sup_{x∈E}|Zₓ − 𝔼[Zₓ]| ≥ ε) ≤ 2𝔠^{ℰ(δ, ε/√𝔡)} exp(−ε²M/2D²)  (12.161)

(cf. Definition 4.3.2).

**Proof of Lemma 12.3.7.** First, observe that the triangle inequality and the assumption that for all x, y ∈ E, m ∈ {1, 2, …, M} it holds that |Y_{x,m} − Y_{y,m}| ≤ ℒδ(x, y) imply that for all x, y ∈ E it holds that

```
|Zₓ − Z_y| = | (1/M) Σ_{m=1}^M Y_{x,m} − (1/M) Σ_{m=1}^M Y_{y,m} | = (1/M) | Σ_{m=1}^M (Y_{x,m} − Y_{y,m}) |
≤ (1/M) Σ_{m=1}^M |Y_{x,m} − Y_{y,m}| ≤ ℒδ(x, y).  (12.162)
```

Next note that the assumption that for all x ∈ E, m ∈ {1, 2, …, M}, ω ∈ Ω it holds that |Y_{x,m}(ω)| ∈ [0, D] ensures that for all x ∈ E it holds that

```
𝔼[|Zₓ|] = 𝔼[ (1/M) Σ_{m=1}^M |Y_{x,m}| ] = (1/M) Σ_{m=1}^M 𝔼[|Y_{x,m}|] ≤ D < ∞.  (12.163)
```

This proves item (i). Furthermore, note that item (i), (12.162), and Lemma 12.3.5 establish item (ii). Next observe that (12.160) shows that for all x ∈ E it holds that

```
|Zₓ − 𝔼[Zₓ]| = | (1/M) Σ_{m=1}^M Y_{x,m} − 𝔼[ (1/M) Σ_{m=1}^M Y_{x,m} ] | = (1/M) Σ_{m=1}^M |Y_{x,m} − 𝔼[Y_{x,m}]|  (12.164)
```

Combining this with Corollary 12.1.21 (applied with (Ω, ℱ, 𝔼) ↝ (Ω, ℱ, 𝔼), N ↝ M, ε ↝ ε/√𝔡, (a₁, a₂, …, a_N) ↝ (0, 0, …, 0), (b₁, b₂, …, b_N) ↝ (D, D, …, D), (Xₙ)_{n∈{1,2,…,N}} ↝ (Y_{x,m})_{m∈{1,2,…,M}} for x ∈ E in the notation of Corollary 12.1.21) ensures that for all x ∈ E it holds that

```
𝔼(|Zₓ − 𝔼[Zₓ]| ≥ ε/√𝔡) ≤ 2 exp(−2[ε/√𝔡]²M² / MD²) = 2 exp(−ε²M / 2D²).  (12.165)
```

Combining this, (12.162), and (12.163) with Lemma 12.3.6 establishes item (iii). The proof of Lemma 12.3.7 is thus complete. ∎