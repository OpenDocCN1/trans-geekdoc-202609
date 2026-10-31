
Step 11: According to the steps for calculating the main dimensions, the weights of the sub-indicators are calculated. Based on the weights of the main dimensions and the weights of the sub-indicators, the final global weights used in the assessment process of smart disaster response systems are calculated.

Step 12: Make a decision matrix (M) among the dimensions identified and the smart disaster response systems designated by the experts as presented in Eqs. (3.11) and (3.12), using semantic terms and TFNs, respectively, as in Table 3.2.

M = (y_ij)_{m×n} = 
      D1   D2   ...   Dn
SDRS1 [ y11  y12  ...  y1n ]
SDRS2   y21  y22  ...  y2n
   ⋮      ...  ...  ...  ...
SDRS_m  y_m1 y_m2 ... y_mn
(3.11)

M = (y_ij)_{m×n}
      D1          D2          ...          Dn
= [ SDRS1  ⟨l11,m11,u11⟩  ⟨l12,m12,u12⟩  ...  ⟨l1n,m1n,u1n⟩ ]
  SDRS2  ⟨l21,m21,u21⟩  ⟨l22,m22,u22⟩  ...  ⟨l2n,m2n,u2n⟩
    ⋮          ...          ...          ...          ...
  SDRS_m ⟨l_m1,m_m1,u_m1⟩ ⟨l_m2,m_m2,u_m2⟩ ... ⟨l_mn,m_mn,u_mn⟩ ]
(3.12)

where n is the number of dimensions, m is the number of the substitutes, and y_ij is the performance estimation of the i^th substitute SDRS1, SDRS2..., SDRS_m concerning the j^th dimension D1, D2..., D_n.

Step 13: Aggregate all decision matrices created by all experts among the dimensions identified and the smart disaster response systems designated into one matrix by applying Eq. (3.3).

Step 14: Defuzzify the fuzzy combined decision matrix into the crisp combined decision matrix by removing the TFNs by applying the GMIR method as presented in Eq. (3.4).

Step 15: Compute the AV_j that associated with all sub-indicators according to the definition of the EDAS technique by applying Eq. (3.13).

AV_j = (∑_{i=1}^m y_ij)/m where m is the number of substitutes (3.13)

Step 16: Compute the positive distance from average (PDA) matrix, which requests to be computed according to the minimum and maximum values of the matrix as exhibited in Eqs. (3.14) and (3.15).

PDA_ij = Max(0, (y_ij - AV_j)) / AV_j , for the advantageous dimensions. (3.14)

PDA_ij = Max(0, (AV_j - y_ij)) / AV_j , for the non-advantageous dimensions (3.15)

Step 17: Compute the negative distance from average (NDA) matrix, which requests to be computed according to the minimum and maximum values of the matrix as exhibited in Eqs. (3.16) and (3.17).

NDA_ij = Max(0, (AV_j - y_ij)) / AV_j , for the advantageous dimensions. (3.16)

NDA_ij = Max(0, (y_ij - AV_j)) / AV_j , for the non-advantageous dimensions. (3.17)

Step 18: Compute the weighted sum of PDA (SP_i) by applying Eq. (3.18) and the weighted sum of NDA (SN_i) according to Eq. (3.19).

SP_i = Σ_{j=1}^{n} w_j PDA_ij (3.18)

SN_i = Σ_{j=1}^{n} w_j NDA_ij (3.19)

Step 19: Compute the standardized values of SP_i and SN_i by applying Eqs. (3.20) and (3.21), respectively.

NSP_i = SP_i / max_i (SP_i) (3.20)

NSN_i = 1 - SN_i / max_i (SN_i) (3.21)

Step 20: Compute the assessment score ASi for all substitutes by applying Eq. (3.22). Then, rank the substitutes according to their assessment score ASi, where the highest value means the best substitute.

ASi = ½ (NSPi + NSNi), where 0 ≤ ASi ≤ 1 (3.22)

## 3.4 An Illustrative Example

The performance evaluation of smart disaster response systems is used to illustrate the suggested paradigm. In the notion of smart cities, human existence has grown more intelligent as a result of vast technological development. One of the concerns of smart cities is a catastrophe response system. It has become vital to incorporate intelligence into disaster response systems to improve citizens’ quality of life and achieve more effective disaster response systems. A smart disaster response system is identical to several intelligent systems that offer intelligent services. The performance of intelligent systems must be evaluated from several perspectives in order to evaluate the system’s overall functioning and user satisfaction. In this chapter, the performance of the intelligent disaster response system will be assessed based on three dimensions: system usability, results and data management, and user activity. Accordingly, several smart disaster response systems were used in the assessment process, namely, SDRS1, SDRS2, SDRS3, SDRS4, SDRS5, SDRS6, and SDRS7.

### 3.4.1 Model Implementation

Step 1: Initially, four experts related to smart systems and decision-making were selected to help and collaborate with the authors in completing the questionnaires and data compilation. Communication with experts was conducted several times, including offline through interviews and online via the Internet.

Step 2: The problem is organized in a hierarchical form between the objective, the main dimensions used, their sub-indicators, and the alternatives used, as presented in Figure 3.3.

Step 3: Semantic terms and corresponding TFNs appropriate to express ambiguity in the problem are identified. First, some variables were presented to determine the priorities and weights of the main dimensions and sub-indicators, as presented in Table 3.1. Secondly, some variables were presented to evaluate the smart disaster response systems selected, as exhibited in Table 3.2.

![](img/601db3e97ac605d993053e21bf375150_122_0.png)

## FIGURE 3.3

Hierarchy structure for smart disaster response system evaluation.

Step 4: Each expert constructed a pairwise comparison matrix between the main dimensions and itself according to Eq. (3.1) by using the semantic terms in Table 3.1 as presented in Table 3.3. Also, each expert constructed a pairwise comparison matrix between the main dimensions and itself according to Eq. (3.2) using TFNs in Table 3.1 as presented in Table 3.4.

## TABLE 3.3

Evaluation of Main Dimensions Using Semantic Variables by All Experts

| Expert_s | SUD₁ | FDD₂ | UAD₃ |
|---|---|---|---|
| SUD₁ | <NOE><NOE><NOE><NOE> | <HIE><HIE><VLE><HIE> | <VHE><HIE><VHE><LOE> |
| FDD₂ | <LOE><VLE><LOE><LOE> | <NOE><NOE><NOE><NOE> | <VLE><VLE><LOE><VLE> |
| UAD₃ | <HIE><HIE><HIE><VHE> | <LOE><LOE><LOE><LOE> | <NOE><NOE><NOE><NOE> |

## TABLE 3.4

Evaluation of Main Dimensions Using TFNs by All Experts

**Expert₁**
|  | SUD₁ | FDD₂ | UAD₃ |
|---|---|---|---|
| SUD₁ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.75, 1.00, 1.00⟩ |
| FDD₂ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.00, 0.25, 0.50⟩ |
| UAD₃ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ |

**Expert₂**
|  | SUD₁ | FDD₂ | UAD₃ |
|---|---|---|---|
| SUD₁ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.50, 0.75, 1.00⟩ |
| FDD₂ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.00, 0.25, 0.50⟩ |
| UAD₃ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ |

**Expert₃**
|  | SUD₁ | FDD₂ | UAD₃ |
|---|---|---|---|
| SUD₁ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.75, 1.00, 1.00⟩ |
| FDD₂ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.25, 0.50, 0.75⟩ |
| UAD₃ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ |

**Expert₄**
|  | SUD₁ | FDD₂ | UAD₃ |
|---|---|---|---|
| SUD₁ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ |
| FDD₂ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.00, 0.25, 0.50⟩ |
| UAD₃ | ⟨0.75, 1.00, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ |

## TABLE 3.5

Aggregated Decision Matrix of All Evaluations to Main Dimensions Using TFNs

| Expertₛ | SUD₁ | FDD₂ | UAD₃ |
|---|---|---|---|
| SUD₁ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.38, 0.63, 0.88⟩ | ⟨0.56, 0.81, 0.94⟩ |
| FDD₂ | ⟨0.19, 0.44, 0.69⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.06, 0.31, 0.56⟩ |
| UAD₃ | ⟨0.56, 0.81, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ |

Step 5: All expert decision matrices created by all experts were aggregated into one matrix by applying Eq. (3.3) as presented in Table 3.5. Then, defuzzify the fuzzy aggregated decision matrix into the crisp combined decision matrix by removing TFNs by applying the GMIR method is applied as shown in Eq. (3.4).

Step 6: The generalized direct relation matrix for main dimensions was developed by applying Eqs. (3.5) and (3.6) as exhibited in Table 3.6.

Step 7: The total relation matrix for main dimensions was computed according to Eq. (3.7), as exhibited in Table 3.7.

Step 8: The IRM of main dimensions was created based on the value of R and C, which was computed according to Eqs. (3.8) and (3.9) and presented in Table 3.7 and Figure 3.4. Also, the final weights of the main dimensions were computed by applying Eq. (3.10) as exhibited in Table 3.7 and Figure 3.5.
