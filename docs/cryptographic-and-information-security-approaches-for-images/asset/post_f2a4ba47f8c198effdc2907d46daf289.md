
## 15.2.2 Decision-Making Theory

This section presents a general overview of MCDM problems and the main steps for solving such types of problems using various MCDM methods. This section also provides a brief description of some MCDM methods.

### 15.2.2.1 General Overview of Decision-Making Problems

Decision-making is the study of solving the problems that are characterized as a choice among many alternatives to find the best one based on different criteria and decision-maker’s preferences. The importance of this study comes due to the difficulty to deal with traditional paradigm for analyzing decision making which is based on uni-dimensional and only one criterion to make a decision. Many problems in our life involve multiple objectives and criteria. These problems are related to the fields of engineering, industry, commercial, and human resource management.

MCDM is a branch of Operational Research (OR) field whose aim is to provide solutions for many complex decision-making problems. Some of these problems are related to high imprecise/uncertainty information and conflicting objectives. MCDM is divided into two categories: Multi-Objective Decision Making (MODM) and Multi-Attribute Decision Making (MADM). MODM relates to an infinite or numerous number of alternatives. It assumes a simultaneous evaluation with regard to a set of objectives that are optimized to a set of criteria in order to find the best alternative. In contrast, MADM is based on evaluation of a relative predetermined number of alternatives characterized by criteria; the evaluation process searches for how well the alternatives satisfy the objectives. Weighting the importance of selected criteria and assigning preference for alternatives are taken into account in MADM [15]. In this chapter MCDM methods refer to MADM category.

### 15.2.2.2 General Steps of MCDM Methods

There are many MCDM methods proposed in the literature to solve problems that are characterized as a choice among alternatives. All of these methods implement the same steps to solve the decision-making problem [15]. These main steps of any MCDM method are illustrated in the following:

- **Step 1: Defining the problem, the alternatives and the criteria.**  
  This step involves the analysis of the decision-making problem to define the multiple conflicting criteria, different measurement among the criteria and the possible alternatives.

- **Step 2: Assigning criteria weights.**  
  Most of MCDM methods require that attributes be assigned weights of importance. Usually, these weights are normalized so that their sum is one. This step manages the priorities of the criteria by assigning them proper weights. These weights show the relative importance of the selected criteria. The weights of the different criteria may be assigned by mutual consultation, pairwise comparison between criteria or by establishing a hierarchy of priorities using the Analytic Hierarchy Process (AHP).

  Several equations are used to normalize the values. Some often used equations are presented in 15.5 through 15.7.

  $$r_{ij} = \frac{x_{ij}}{\sqrt{\sum_{i=1,j=1}^{m,n} x_{ij}^2}},\ i=1,...,m;\ j=1,...,n \tag{15.5}$$

  $$r_{ij} = \frac{x_{ij} - min_j}{max_j - min_j},\ i=1,...,m;\ j=1,...,n \tag{15.6}$$

  $$r_{ij} = \frac{x_{ij}}{max_j},\ i=1,...,m;\ j=1,...,n \tag{15.7}$$

  where $m$ is the number of alternatives, $n$ is the number of criteria and $x_{ij}$ is the score of alternative $A_i$ when it is evaluated in terms of decision criterion $C_j$.

- **Step 3: Construction of the evaluation matrix.**  
  An MCDM problem can be expressed in a matrix format. A decision matrix $A$ is an $(m \times n)$ matrix in which the element $x_{ij}$ indicates the score of alternative $A_i$ when it is evaluated in terms of decision criterion $C_j$, $i = 1,2,...,m$ and $j = 1,2,...,n$.

  It is also assumed that the decision maker has determined the weights of relative performance of the decision criteria (denoted as $W_j$, for $j = 1,2,...,n$). This information is summarized in the following matrix.

  | Criteria | $C_1$ | $C_2$ | $\cdots$ | $C_n$ |
  |---|---|---|---|---|
  | $A_1$ | $x_{11}$ | $x_{12}$ | $\cdots$ | $x_{1n}$ |
  | $A_2$ | $x_{21}$ | $x_{22}$ | $\cdots$ | $x_{2n}$ |
  | $\vdots$ | $\vdots$ | $\vdots$ | $\ddots$ | $\vdots$ |
  | $A_m$ | $x_{m1}$ | $x_{m2}$ | $\cdots$ | $x_{mn}$ |

  $$A = \begin{bmatrix} x_{11} & x_{12} & \cdots & x_{1n} \\ x_{21} & x_{22} & \cdots & x_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ x_{m1} & x_{m2} & \cdots & x_{mn} \end{bmatrix}$$

- **Step 4: Selecting the appropriate method.**  
  In this step, the decision maker is responsible to select a proper MCDM method for selecting the preferred alternative. Based on the matrix illustrated in step 3, the MCDM method is used to determine the suitable alternative $A^*$ with the highest degree of desirability with respect to all relevant criteria.

- **Step 5: Ranking the alternatives.**  
  In the final step, the set of alternatives are ranked and the first ranked alternative with the highest value based on user's preferences is selected as an optimal solution.

### 15.2.2.3 General Description of Some MCDM Methods

Different methods are proposed in the literature to solve the problem of multi-criteria decision making. This section provides an abstract description for some of these methods.

#### 15.2.2.3.1 Weighted Sum Method (WSM)

WSM is a simple and most widely used MCDM. Basically, the WSM method starts by converting the intangible values into comparable values and then obtains the normalized decision matrix R (r_ij, i = 1,...,m and j = 1,...,n) according to Equations 15.8 and 15.9. Equation 15.8 is used if the jth criterion is a benefit criterion and Equation 15.9 is used if the jth criterion is a non-benefit criterion.

$$r_{ij} = x_{ij} / r_j^* \tag{15.8}$$
$$r_{ij} = r_j^- / x_{ij} \tag{15.9}$$

where $x_{ij}$ is the score of alternative i with respect to criterion j, $r_j^*$ is the maximum value of r in column j and $r_j^-$ is the minimum value of r in column j.

Afterward, the WSM method uses the additive aggregation of the criteria according to Equation 15.10 to calculate the score for each alternative.

$$A_i = \sum_{j=1}^n r_{ij} \times w_j \tag{15.10}$$

where $w_j$ is the criterion weight.

Based on the final scores, decision maker can rank all alternatives to select the best one, which has the maximum score value. Equation 15.11 presents the calculus of the best alternative A*.

$$A^* = \max(A_i), \quad i = 1,2,...,m \tag{15.11}$$

#### 15.2.2.3.2 Weighted Product Method (WPM)

This method is similar to WSM, but instead of addition the main mathematical operation is the product. Each alternative is compared with other alternatives by multiplying a number of ratios for each criterion. Each ratio is raised to the power of the relative weight of the corresponding criterion. Equation 15.12 is used to compare two alternatives ($A_p$ and $A_q$).

$$R(A_p / A_q) = \prod_{j=1}^n (x_{pj} / x_{qj})^{w_j} \tag{15.12}$$

where $n$ is the number of criteria, $w_j$ is the weight of the jth criterion, $x_{pj}$ is the actual value of the pth alternative in terms of the jth criterion, and $x_{qj}$ is the actual value of the qth alternative in terms of the jth criterion.

If the resulted ratio of $R(A_p / A_q)$ is greater than or equal to one, this indicates that the alternative $A_p$ is more desirable than alternative $A_q$. The alternative which is more desirable than all other alternatives is the best one.

#### 15.2.2.3.3 Analytic Hierarchy Process (AHP)

AHP is another MCDM method designed to solve complex problems involving multi-criteria. The advantage of AHP is that it is designed to handle situations in which the subjective judgments of individuals constitute an important part of the decision process. Initially, the AHP method starts by developing a hierarchy representation of the problem in terms of the overall goal, the decision criteria and the alternatives. Then, the relative weight for each decision criterion is specified in terms of its contribution to the achievement of the overall goal. The pairwise comparisons are used in AHP methods to rate the relative preferences for two criteria and then to assign proper weight for each criterion. Subsequently, the relative priorities of alternatives are determined, where both qualitative and quantitative information can be compared by using informed judgments to derive weights and priorities. The output of the AHP is a prioritized ranking indicating the overall preference for each of the decision alternatives.

#### 15.2.2.3.4 Technique for Order of Preference by Similarity to Ideal Solution (TOPSIS)

The TOPSIS method is a simple ranking method for solving the problems of large number of discrete alternatives [16]. It has the ability to allocate the scores to each alternative based on its geometric distance from the positive and negative ideal solutions. The closest alternative (the shortest geometric distance) to the positive ideal solution and the farthest (the longest geometric distance) to the negative ideal alternative is the best alternative among all alternatives. TOPSIS method assumes that we have m alternatives and n attributes/criteria, as well as the score of each alternative with respect to each criterion. Let $x_{ij}$ be the score of alternative i with respect
