
## 5.3 Model

This section presents the steps of a hybrid MCDM approach for evaluating multiple cloud service providers (CSPs). The approach consists of two MCDM approaches: the entropy and the combined compromised solution (CoCoSo). The applied approach was carried out under the q-ROFS environment and using q-rung orthopair fuzzy numbers (q-ROFNs). Figure 5.2 shows the steps of the approach used in evaluating several CSPs. The approach is divided into three parts: data aggregation, determination of criteria weights using the entropy technique, and arranging the used alternatives according to their importance using the CoCoSo technique. In this regard, we provide a brief overview of the methods used in applying the case study for this chapter. This section is divided into several parts as follows.

![](img/601db3e97ac605d993053e21bf375150_176_0.png)

FIGURE 5.2

Diagrammatic representation of the applied approach for choosing cloud services.

### 5.3.1 Entropy Method

Shannon and Weaver came up with the idea for the entropy weight technique in 1947, which is a weighing approach that evaluates the value dispersion that occurs during decision-making (Chodha et al., 2022). The entropy weight approach is used to determine the objective weights of the criteria and characteristics. Probability theory is used whenever uncertain information has to be computed (entropy) (Vaid et al., 2022). It evaluates the significance of each answer parameter independently, without taking into account the preferences of the individual making the decision. A higher weight index value is considered to have a greater value than a lower weight index value from the standpoint of the entropy weight measuring system. This method begins with determining the objectives (decision matrix), followed by determining the normalized decision matrix, the probability of the criteria or attribute occurring, the entropy value of the criteria or attribute, the degrees of divergence produced by each response, and finally, the entropy weight.

### 5.3.2 CoCoSo Method

In the CoCoSo technique, options are ranked according to compromise methods derived from the Weighted Sum Model (WSM) and Weighted Product Model (WPM) (Deveci, Pamucar, and Gokasar, 2021). As a result of a compromise, the final criteria function on which the ranking of alternatives is based was determined. It demonstrates that a combination of compromise tactics delivers objective outcomes when the ratings of options in the initial choice matrix have consistent values. However, when extreme values arrive at the location of the most important criterion in the initial choice matrix, the values of the WSM and WPM functions undergo drastic modifications (Torkayesh et al., 2021). This results in a disproportionate rise in the value function of the criteria for the evaluated option. Extreme values in the first choice matrix may develop for a variety of causes, including, but not limited to, disproportional disparities between the examined options, measurement mistakes, and biased specialist judgments (deliberate or accidental). Another drawback of WSM and WPM aggregation is that they disregard the interrelationships and reciprocal impact between the criteria.

### 5.3.3 Computational Steps of the Applied Approach

The computational steps of the approach used in the problem presented in this chapter are presented as follows:

**Step 1:** The target case is carefully studied from all directions, and the most important key dimensions that affect the evaluation of cloud service providers are identified. Then, some specialists are negotiated to help the authors compile the data needed to solve the problem. Accordingly, some criteria have been set on the basis of which specialists are selected (SPs), such as the scientific degree and the number of years of experience. Also, the most appropriate ways to communicate with experts are identified.

**Step 2:** The most important main dimensions affecting the selection of cloud service providers are determined based on expert surveys and previous studies. D_j = {D1, D2, ..., Dn}, with j=1, 2, ..., n. Let ω = (ω1, ω2, ..., ωn) be the vector set applied for identifying the dimension weights, where ωj > 0 and ∑_{j=1}^n ωj = 1.

**Step 3:** The most important available alternatives that can be used in the evaluation process are determined, in addition to preparing a final list of these alternatives according to the opinions of specialists. The group CSP_i = {CSP1, CSP2, ..., CSPm}, having i=1, 2..., m substitutes, is assessed by n decision dimensions of group D_j = {D1, D2, ..., Dn}, with j=1, 2..., n.

**Step 4:** After studying the main dimensions of the case study and identifying the most important aspects affecting the problem, all the parties used are organized in the form of a hierarchical structure.

**Step 5:** According to the evaluation process conducted by the specialists, this requires the presence of linguistic terms that help them in carrying out the various evaluations, whether to determine the weights of the main dimensions or to arrange the selected alternatives as in Tables 5.1 and 5.2.

**Step 6:** Form the judgment matrices rendering to specialists’ preferences (SPs) to assess the dimensions of each specialist by utilizing linguistic terms as presented in Table 5.1, and then by utilizing q-ROFNs as exhibited in Table 5.3.

### TABLE 5.1
Linguistic Terms and Their Equivalent q-ROFNs for Evaluating Factors

| Linguistic Terms | Abridgments | u | ϑ |
|---|---|---|---|
| Exceedingly low | EXL | 0.11 | 0.99 |
| Very low | VEL | 0.22 | 0.88 |
| Low | LOW | 0.33 | 0.77 |
| Medium low | MLO | 0.44 | 0.66 |
| Medium | MED | 0.55 | 0.55 |
| Medium well | MEW | 0.66 | 0.44 |
| Well | WEL | 0.77 | 0.33 |
| Very well | VRL | 0.88 | 0.22 |
| Exceedingly well | EWL | 0.99 | 0.11 |

### TABLE 5.2
Linguistic Terms and Their Equivalent q-ROFNs for Rating Substitutes

| Linguistic Terms | Abridgments | $\mathcal{U}$ | $\vartheta$ |
|---|---|---|---|
| Exceedingly little | EDL | 0.11 | 0.99 |
| Very little | VRL | 0.22 | 0.88 |
| Little | LTT | 0.33 | 0.77 |
| Intermediate little | TNL | 0.44 | 0.66 |
| Intermediate | INE | 0.55 | 0.55 |
| Intermediate great | ING | 0.66 | 0.44 |
| Great | GRE | 0.77 | 0.33 |
| Very great | VEG | 0.88 | 0.22 |
| Exceedingly great | EGT | 0.99 | 0.11 |

### TABLE 5.3
Evaluation Matrix for Criteria Based on q-ROFN with Respect to Experts

| Dimensions | SP$_1$ | SP$_2$ | SP$_3$ | SP$_4$ |
|---|---|---|---|---|
| D$_1$ | $[u_{1SP_1}, \vartheta_{1SP_1}]$ | $[u_{1SP_2}, \vartheta_{1SP_2}]$ | $[u_{1SP_3}, \vartheta_{1SP_3}]$ | $[u_{1SP_4}, \vartheta_{1SP_4}]$ |
| D$_2$ | $[u_{2SP_1}, \vartheta_{2SP_1}]$ | $[u_{2SP_2}, \vartheta_{2SP_2}]$ | $[u_{2SP_3}, \vartheta_{2SP_3}]$ | $[u_{2SP_4}, \vartheta_{2SP_4}]$ |
| $\vdots$ | $\vdots$ | $\vdots$ | $\vdots$ | $\vdots$ |
| D$_n$ | $[u_{nSP_1}, \vartheta_{nSP_1}]$ | $[u_{nSP_2}, \vartheta_{nSP_2}]$ | $[u_{nSP_3}, \vartheta_{nSP_3}]$ | $[u_{nSP_4}, \vartheta_{nSP_4}]$ |

Step 7: Combine the assessments on dimensions and weights. The distinct specialist assessments were aggregated by applying q-ROFWG presented in Eq. (5.23). At this point, $(\omega_j)_{1\times n}$ introduces q-ROF weight of $j^{th}$ dimension.

Step 8: Calculate the entropy values of all q-ROFN of the collected specialists’ assessments by applying Eqs. (5.28) and (5.29).

kE$_{q,ij}(y) = \frac{1}{\sqrt{2}} \left( \left((\mathcal{U}(y))^q\right)^2 + \left((\vartheta(y))^q\right)^2 + \left((\mathcal{U}(y))^q + (\vartheta(y))^q\right)^2 \right)^{0.5} \tag{5.28}

EN$_{q,ij}(y) = 1 - kE_{q,ij}(y) = 1 - \left( \left((\mathcal{U}(y))^q\right)^2 + \left((\vartheta(y))^q\right)^2 + \left((\mathcal{U}(y))^q + (\vartheta(y))^q\right)^2 \right)^{0.5} \tag{5.29}

Step 9: Compute the key dimension weights based on the entropy values according to Eq. (5.30).

ω_j = (1 - ξ_j) / Σ_{j=1}^n (1 - ξ_j) ; j = 1,2,...,n. (5.30)

where ξ_j = Σ_{i=1}^m EN_{q,ji} / Σ_{i=1}^m Σ_{j=1}^n EN_{q,ij} indicates the q-ROF entropy value.

Step 10: Generate the assessment judgment matrix by each specialist separately (SP_s) between the determined key dimensions and the available alternatives to assess the cloud service providers by utilizing the linguistic terms as presented in Table 5.2, then by applying the q-ROFNs in Table 5.2 as exhibited in Table 5.4.

Step 11: Aggregate the assessment judgment matrix by each specialist separately (SP_s) between the determined key dimensions and the available alternatives to assess the cloud service providers into one matrix by applying q-ROFWG as exhibited in Eq. (5.23) as presented in Table 5.5.

### TABLE 5.4
Judgment Assessment Matrix for Substitutes in Terms of Dimensions Based on q-ROFN

| Dimensions | Substitutes |  |  | |
|---|---|---|---|---|
|  | CSP₁ | CSP₂ | ... | CSPₘ |
| D₁ | [u₁₁SP , ϑ₁₁SP] | [u₁₂SP , ϑ₁₂SP] | ... | [u₁mSP , ϑ₁mSP] |
| D₂ | [u₂₁SP , ϑ₂₁SP] | [u₂₂SP , ϑ₂₂SP] | ... | [u₂mSP , ϑ₂mSP] |
| ⋮ | ⋮ | ⋮ | ⋱ | ⋮ |
| Dₙ | [uₙ₁SP , ϑₙ₁SP] | [uₙ₂SP , ϑₙ₂SP] | ... | [uₙmSP , ϑₙmSP] |

### TABLE 5.5
Aggregated Assessment Matrix for Alternatives in Terms of Dimensions Based on q-ROFN

| Dimensions | Alternatives |  |  | |
|---|---|---|---|---|
|  | CSP₁ | CSP₂ | ... | CSPₘ |
| D₁ | [u₁₁ , ϑ₁₁] | [u₁₂ , ϑ₁₂] | ... | [u₁m , ϑ₁m] |
| D₂ | [u₂₁ , ϑ₂₁] | [u₂₂ , ϑ₂₂] | ... | [u₂m , ϑ₂m] |
| ⋮ | ⋮ | ⋮ | ⋱ | ⋮ |
| Dₙ | [uₙ₁ , ϑₙ₁] | [uₙ₂ , ϑₙ₂] | ... | [uₙm , ϑₙm] |
