
## TABLE 8.2

Linguistic Terms and Their Equivalent IFNs for Rating Alternatives

| Linguistic Terms | Abbreviations | $\mathcal{U}$ | $\vartheta$ |
|---|---|---|---|
| Absolutely low value | ABV | 0.10 | 0.85 |
| Very low value | VLV | 0.20 | 0.75 |
| Low value | LOV | 0.30 | 0.65 |
| Medium low value | MLV | 0.40 | 0.55 |
| Approximate value | APV | 0.50 | 0.45 |
| Medium high value | MHV | 0.60 | 0.35 |
| High value | HIV | 0.70 | 0.25 |
| Very high value | VEV | 0.80 | 0.15 |
| Absolutely high value | AHV | 0.90 | 0.05 |

## TABLE 8.3

Decision Matrix Based on IFNs According to Expert E_k

| Criteria | Alternatives |  |  |
|---|---|---|---|
|  | SMS$_1$ | SMS$_2$ | ... | SMS$_m$ |
| C$_1$ | $[\mathcal{U}_{11k}^C, \vartheta_{11k}^C]$ | $[\mathcal{U}_{12k}^C, \vartheta_{12k}^C]$ | ... | $[\mathcal{U}_{1mk}^C, \vartheta_{1mk}^C]$ |
| C$_2$ | $[\mathcal{U}_{21k}^C, \vartheta_{21k}^C]$ | $[\mathcal{U}_{22k}^C, \vartheta_{22k}^C]$ | ... | $[\mathcal{U}_{2mk}^C, \vartheta_{2mk}^C]$ |
| $\vdots$ | $\vdots$ | $\vdots$ | $\ddots$ | $\vdots$ |
| C$_n$ | $[\mathcal{U}_{n1k}^C, \vartheta_{n1k}^C]$ | $[\mathcal{U}_{n2k}^C, \vartheta_{n2k}^C]$ | ... | $[\mathcal{U}_{nmk}^C, \vartheta_{nmk}^C]$ |

## TABLE 8.4

Combined Decision Matrix Based on IFNs

| Criteria | Alternatives |  |  |
|---|---|---|---|
|  | SMS$_1$ | SMS$_2$ | ... | SMS$_m$ |
| C$_1$ | $[\mathcal{U}_{11}^C, \vartheta_{11}^C]$ | $[\mathcal{U}_{12}^C, \vartheta_{12}^C]$ | ... | $[\mathcal{U}_{1m}^C, \vartheta_{1m}^C]$ |
| C$_2$ | $[\mathcal{U}_{21}^C, \vartheta_{21}^C]$ | $[\mathcal{U}_{22}^C, \vartheta_{22}^C]$ | ... | $[\mathcal{U}_{2m}^C, \vartheta_{2m}^C]$ |
| $\vdots$ | $\vdots$ | $\vdots$ | $\ddots$ | $\vdots$ |
| C$_n$ | $[\mathcal{U}_{n1}^C, \vartheta_{n1}^C]$ | $[\mathcal{U}_{n2}^C, \vartheta_{n2}^C]$ | ... | $[\mathcal{U}_{nm}^C, \vartheta_{nm}^C]$ |

IFWG($\widetilde{SMS}_1,\widetilde{SMS}_2,...,\widetilde{SMS}_n$) = $\left( \prod_{i=1}^{n} \mathcal{U}_{\widetilde{SMS_i}}^{w_i}, \left(1-\prod_{i=1}^{n}(1-\vartheta_{\widetilde{SMS_i}})^{w_i}\right) \right)$ (8.1)

Step 7: Describe the degrees of correlation between criteria. For this, the decision matrix is predominantly defuzzified by utilizing Eqs. (8.2) and (8.3) by considering the criteria nature, which can be the advantage and non-advantage categories. Then, the standard deviation for each criterion is calculated by utilizing Eq. (8.4), and the correlation relationship of each criterion with other criteria is determined by applying Eq. (8.5).

φ_ij = [1 - (U_ij × U_- + ϑ_ij × ϑ_- + π_ij × π_-)/(U_ij² ∨ U_-² + ϑ_ij² ∨ ϑ_-² + π_ij² ∨ π_-²)] / [1 - (U_- × U_+ + ϑ_- × ϑ_+ + π_- × π_+)/(U_-² ∨ U_+² + ϑ_-² ∨ ϑ_+² + π_-² ∨ π_+²)], (8.2)
i = 1,2,...,m; j = 1,2,...,n, for positive attributes

φ_ij = [1 - (U_ij × U_+ + ϑ_ij × ϑ_+ + π_ij × π_+)/(U_ij² ∨ U_+² + ϑ_ij² ∨ ϑ_+² + π_ij² ∨ π_+²)] / [1 - (U_- × U_+ + ϑ_- × ϑ_+ + π_- × π_+)/(U_-² ∨ U_+² + ϑ_-² ∨ ϑ_+² + π_-² ∨ π_+²)], (8.3)
i = 1,2,...,m; j = 1,2,...,n, for negative attributes

σ_j = sqrt( sum_{i=1}^{m} (φ_ij - overline{φ_j})² / m ), j = 1,2,...,n. (8.4)

r_jk = [ sum_{i=1}^{m} (φ_ij - overline{φ_j})(φ_ik - overline{φ_k}) ] / [ sqrt( sum_{i=1}^{m} (φ_ij - overline{φ_j})² ) sqrt( sum_{i=1}^{m} (φ_ik - overline{φ_k})² ) ], j = 1,2...n; k = 1,2...n. (8.5)

where $\mathcal{U}_-$, $\mathcal{U}_+$, ϑ_-, and ϑ_+ are the lowest and highest grades of membership and non-membership, respectively.

Step 8: Calculate the criterion weights through the standard deviation of each criterion and its correlation between other criteria by utilizing Eq. (8.6). Then, the objective weights of criteria were standardized, and the weight of each criterion is computed by applying Eq. (8.7).

C_j = σ_j sum_{k=1}^{n} (1 - r_jk), j = 1,2...n. (8.6)

w_j = C_j / sum_{j=1}^{n} C_j (8.7)

**Step 9:** Construct the appraisal judgment matrix by each expert specifically (E_k) between the identified criteria and the selected alternatives to analyze and evaluate the smart card systems by applying the linguistic terms presented in Table 8.2 and then applying the IFNs in Table 8.2 according to Table 8.5.

**Step 10:** Collect the appraisal judgment matrix by each expert specifically (E_k) between the identified criteria and the selected alternatives to analyze and evaluate the smart card systems into a single matrix by applying IFWG as presented in Eq. (8.1) as exhibited in Table 8.6.

**Step 11:** Defuzzification of the intuitionistic fuzzy combined appraisal judgment matrix into the crisp combined decision matrix by removing the IFNs by applying Eq. (8.8) according to Table 8.7. Also, Eq. (8.8) was mentioned in detail in the previous chapter. For better understanding, readers are advised to read Chapter 7, particularly the explanation corresponding to Eq. (7.5).

$\mathfrak{I}(\widetilde{SMS})=\mathcal{U}_{SMS}+\left(\frac{\mathcal{U}_{SMS}\vartheta_{SMS}e^{(1-\mathcal{U}_{SMS}-\vartheta_{SMS})}}{2}\right)^{2},\text{ where }\mathfrak{I}(\widetilde{SMS})\in[0,1]\quad(8.8)$

## TABLE 8.5

Decision Matrix for Substitutes in Terms of Criteria Based on IFNs

| Criteria | SMS₁ | SMS₂ | ... | SMSₘ |
|---|---|---|---|---|
| C₁ | [𝒰₁₁ₖᶜ, ϑ₁₁ₖᶜ] | [𝒰₁₂ₖᶜ, ϑ₁₂ₖᶜ] | ... | [𝒰₁ₘₖᶜ, ϑ₁ₘₖᶜ] |
| C₂ | [𝒰₂₁ₖᶜ, ϑ₂₁ₖᶜ] | [𝒰₂₂ₖᶜ, ϑ₂₂ₖᶜ] | ... | [𝒰₂ₘₖᶜ, ϑ₂ₘₖᶜ] |
| ⋮ | ⋮ | ⋮ | ⋱ | ⋮ |
| Cₙ | [𝒰ₙ₁ₖᶜ, ϑₙ₁ₖᶜ] | [𝒰ₙ₂ₖᶜ, ϑₙ₂ₖᶜ] | ... | [𝒰ₙₘₖᶜ, ϑₙₘₖᶜ] |

## TABLE 8.6

Combined Decision Matrix for Substitutes in Terms of Criteria Based on IFNs

| Criteria | SMS₁ | SMS₂ | ... | SMSₘ |
|---|---|---|---|---|
| C₁ | [𝒰₁₁ᶜ, ϑ₁₁ᶜ] | [𝒰₁₂ᶜ, ϑ₁₂ᶜ] | ... | [𝒰₁ₘᶜ, ϑ₁ₘᶜ] |
| C₂ | [𝒰₂₁ᶜ, ϑ₂₁ᶜ] | [𝒰₂₂ᶜ, ϑ₂₂ᶜ] | ... | [𝒰₂ₘᶜ, ϑ₂ₘᶜ] |
| ⋮ | ⋮ | ⋮ | ⋱ | ⋮ |
| Cₙ | [𝒰ₙ₁ᶜ, ϑₙ₁ᶜ] | [𝒰ₙ₂ᶜ, ϑₙ₂ᶜ] | ... | [𝒰ₙₘᶜ, ϑₙₘᶜ] |

## TABLE 8.7

Defuzzified Decision Matrix for Alternatives in Terms of Sub-Factors

| Criteria | Alternatives |  |  | |
|---|---|---|---|---|
|  | SMS₁ | SMS₂ | ... | SMSₘ |
| C₁ | x₁₁ = [u₁₁ᶜ, θ₁₁ᶜ] | x₁₂ = [u₁₂ᶜ, θ₁₂ᶜ] | ... | x₁ₘ = [u₁ₘᶜ, θ₁ₘᶜ] |
| C₂ | x₂₁ = [u₂₁ᶜ, θ₂₁ᶜ] | x₂₂ = [u₂₂ᶜ, θ₂₂ᶜ] | ... | x₂ₘ = [u₂ₘᶜ, θ₂ₘᶜ] |
| ⋮ | ⋮ | ⋮ | ⋱ | ⋮ |
| Cₙ | xₙ₁ = [uₙ₁ᶜ, θₙ₁ᶜ] | xₙ₂ = [uₙ₂ᶜ, θₙ₂ᶜ] | ... | xₙₘ = [uₙₘᶜ, θₙₘᶜ] |

Step 12: Compute the normalized decision matrix according to Eq. (8.9) for advantageous criteria and Eq. (8.10) for non-advantageous criteria.

$$X_{ij}=\frac{[x_{ij}-Min(x_{ij})]}{[max(x_{ij})-Min(x_{ij})]}$$ (8.9)

$$X_{ij}=\frac{[max(x_{ij})-x_{ij}]}{[max(x_{ij})-Min(x_{ij})]}$$ (8.10)

Step 13: Compute the evaluative dissimilarities of i th substitute for other substitutes.

Step 14: Calculate the preference function for the normalized decision matrix P_j(a, b) according to Eqs. (8.11) and (8.12).

$$P_j(a,b)=0\text{ if }R_{aj}\le R_{bj}$$ (8.11)

$$P_j(a,b)=(R_{aj}-R_{bj})\text{ if }R_{aj}>R_{bj}$$ (8.12)

Step 15: Compute the weighted preference matrix according to Eq. (8.13) and the combined preference function according to Eq. (8.14).

$$w_j p_j(a,b)$$ (8.13)

$$\pi(a,b)=\frac{\sum_{j=1}^{n} w_j p_j(a,b)}{\sum_{j=1}^{n} w_j},\text{ where }p_j(a,b)\text{ is the preference function}$$ (8.14)

Step 16: Calculate the outflowing ranking (leaving or optimistic) for i th alternative according to Eq. (8.15) and the inflowing ranking (entering or pessimistic) for i th alternative according to Eq. (8.16).

φ⁺ = 1/(M−1) Σ_{b=1}^m π(a,b),  a ≠ b;  (8.15)

φ⁻ = 1/(M−1) Σ_{b=1}^m π(b,a),  a ≠ b;  (8.16)

where m refers to the number of substitutes.

Step 17: Calculate the net outranking flow for each substitute according to Eq. (8.17). Then, classify the substitutes in descending order of the values of φ(SMS).

φ(SMS) = φ⁺(SMS) − φ⁻(SMS)  (8.17)

## 8.3 Model Implementation

The purpose of this chapter is to differentiate and verify some of the benefits of smart card systems that have been described in the literature. This will be accomplished by accurately comparing the old fare and smart card systems using opposing criteria. In light of this, the MCDM analysis takes into consideration not only the conventional system but also four other smart card systems, each of which has a distinct set of capabilities. In order to conduct an objective analysis, the technological parameters of the contactless smart cards have been standardized.

Step 1: The problem was studied, and the main objective was determined, which is the analysis and evaluation of smart card systems, in addition to determining the main criteria that affect the selection of the best smart card system. Also, four experts agreed to participate in data collection, and an effective weight for each expert was determined as 0.2, 0.3, 0.3, and 0.2.

Step 2: A set of five alternatives have been identified to be used in the evaluation process, including the traditional fare system and four smart card systems, namely, traditional fare system, smart card system 1, smart card system 2, smart card system 3, and smart card system 4 which are referred to by the following abbreviations SMS₁, SMS₂, SMS₃, SMS₄, and SMS₅, respectively. Also, a set of criteria were defined to evaluate the selected alternatives, as mentioned in Table 8.8.
