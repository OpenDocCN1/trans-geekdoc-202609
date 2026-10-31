
## Step 8: Construct the influential relation map (IRM) by computing the sum of rows and columns from the matrix T~ , stated as vector R~ and C~ , respectively, in Eqs. (4.6) and (4.7). The IRM will be calculated by computing the ordered pairs (R~+C~, R~-C~).

R~ = (R~_i)_{1x n} = [ sum_{j=1}^{n} T~_{ij} ]_{1x n} (4.6)

C~ = (C~_i)_{1x n} = [ sum_{i=1}^{n} T~_{ij} ]_{1x n} (4.7)

where R~ and C~ indicate the total of rows and columns of the total-effect matrix, respectively. R~_i and C~_i indicate the total of rows and columns of ith barrier, respectively.

## Step 9: Defuzzify the (R~+C~, R~-C~) to the crisp value ((R~+C~)^{def}, (R~-C~)^{def}) by removing the triangular fuzzy numbers by applying the graded mean integration representation (GMIR) method (Zhao and Guo 2015) as exhibited in Eq. (4.8).

x_{ij}^{def} = (x_{ij}^{l} + 4 x_{ij}^{m} + x_{ij}^{u}) / 6 (4.8)

## Step 10: Compute the threshold value (alpha) by adding the average of all the numbers presented in the total-effect matrix and dividing by the number of items present in the matrix as presented in Eq. (4.9).

alpha = sum_{i=1}^{n} sum_{j=1}^{n} T_{ij} / n^2 (4.9)

where n^2 means the whole number of elements in the total-effect matrix.

## Step 11: Compute the weights of ith IoT barriers to waste management in smart cities w_i by applying Eq. (4.10).

w_i = [ ((R~+C~)^{def})^2 + ((R~-C~)^{def})^2 ]^{1/2} / sum_{i=1}^{n} [ ((R~+C~)^{def})^2 + ((R~-C~)^{def})^2 ]^{1/2} (4.10)

## 4.4 Model Implementation

In this chapter, semi-structured interviews were conducted with industry professionals, extensive evaluations were conducted of the development plans for smart cities, and waste management reports and databases were analyzed. The goal of the chapter is to establish a holistic model. A qualitative research technique is used in this chapter because its primary purpose is to construct a study framework of IoT adoption obstacles to waste management in smart cities using the expertise and experience of industry professionals, as well as the findings of prior studies.

### Step 1:
In this chapter, we applied the fuzzy DEMATEL method to analyze IoT barriers to waste management in smart cities. The implementation of the fuzzy DEMATEL method in this chapter differs from the previous chapter. In this chapter, all the steps of the fuzzy DEMATEL method without defuzzification are applied from the beginning, unlike in the previous chapter.

### Step 2:
We formed a panel of four domain experts and requested their assistance in evaluating the IoT adoption obstacles to waste management in smart cities. Two specialists from the IT area, one from the smart cities’ development project and one from waste management, comprise the three experts. Two scientists verified the stated obstacles to adoption. The majority of their time is spent creating the smart cities’ project and constructing infrastructure.

### Step 3:
Linguistic variables and corresponding appropriate TFNs have been created to prioritize IoT barriers to waste management in smart cities, as presented in Table 4.1.

### Step 4:
A pairwise comparison matrix among the barriers and itself by all experts was created according to Eq. (4.1) by using the linguistic variable as presented in Table 4.2 and then by using TFNs according to Eq. (4.2) as presented in Table 4.3.

## TABLE 4.2

Assessment of IoT Barriers to Waste Management in Smart Cities Using Linguistic Variables by All Experts

| Expert₁ | IoTB₁ | IoTB₂ | IoTB₃ | IoTB₄ | IoTB₅ | IoTB₆ | IoTB₇ | IoTB₈ | IoTB₉ | IoTB₁₀ |
|---|---|---|---|---|---|---|---|---|---|---|
| IoTB₁ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨VHL⟩ | ⟨LFL⟩ | ⟨LFL⟩ |
| IoTB₂ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ |
| IoTB₃ | ⟨VHL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ |
| IoTB₄ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ |
| IoTB₅ | ⟨VLF⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨VLF⟩ |
| IoTB₆ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ |
| IoTB₇ | ⟨NFL⟩ | ⟨VHL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨VHL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ |
| IoTB₈ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨VHL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ |

## TABLE 4.2 (Continued)

Assessment of IoT Barriers to Waste Management in Smart Cities Using Linguistic Variables by All Experts

| Expert₁ | IoTB₁ | IoTB₂ | IoTB₃ | IoTB₄ | IoTB₅ | IoTB₆ | IoTB₇ | IoTB₈ | IoTB₉ | IoTB₁₀ |
|---|---|---|---|---|---|---|---|---|---|---|
| IoTB₉ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VHL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨LFL⟩ |
| IoTB₁₀ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨VHL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨NFL⟩ |
| Expert₂ | IoTB₁ | IoTB₂ | IoTB₃ | IoTB₄ | IoTB₅ | IoTB₆ | IoTB₇ | IoTB₈ | IoTB₉ | IoTB₁₀ |
|---|---|---|---|---|---|---|---|---|---|---|
| IoTB₁ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨VHL⟩ | ⟨LFL⟩ | ⟨LFL⟩ |
| IoTB₂ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨HFL⟩ |
| IoTB₃ | ⟨VHL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ |
| IoTB₄ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ |
| IoTB₅ | ⟨VLF⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨VLF⟩ |
| IoTB₆ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ |
| IoTB₇ | ⟨NFL⟩ | ⟨VHL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨VHL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ |
| IoTB₈ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨VHL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ |
| IoTB₉ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VHL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨LFL⟩ |
| IoTB₁₀ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨VHL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨NFL⟩ |
| Expert₃ | IoTB₁ | IoTB₂ | IoTB₃ | IoTB₄ | IoTB₅ | IoTB₆ | IoTB₇ | IoTB₈ | IoTB₉ | IoTB₁₀ |
|---|---|---|---|---|---|---|---|---|---|---|
| IoTB₁ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨VHL⟩ | ⟨LFL⟩ | ⟨LFL⟩ |
| IoTB₂ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ |
| IoTB₃ | ⟨VHL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ |
| IoTB₄ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ |
| IoTB₅ | ⟨VLF⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨VLF⟩ |
| IoTB₆ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ |
| IoTB₇ | ⟨NFL⟩ | ⟨VHL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨VHL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ |
| IoTB₈ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨VHL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ |
| IoTB₉ | ⟨HFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VHL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨LFL⟩ |
| IoTB₁₀ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨VHL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨NFL⟩ |
| Expert₄ | IoTB₁ | IoTB₂ | IoTB₃ | IoTB₄ | IoTB₅ | IoTB₆ | IoTB₇ | IoTB₈ | IoTB₉ | IoTB₁₀ |
|---|---|---|---|---|---|---|---|---|---|---|
| IoTB₁ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨VHL⟩ | ⟨LFL⟩ | ⟨LFL⟩ |
| IoTB₂ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨VLF⟩ |
| IoTB₃ | ⟨VHL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ |
| IoTB₄ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ |
| IoTB₅ | ⟨VLF⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨HFL⟩ | ⟨NFL⟩ | ⟨VLF⟩ |
| IoTB₆ | ⟨VLF⟩ | ⟨VLF⟩ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨VLF⟩ |
| IoTB₇ | ⟨NFL⟩ | ⟨VHL⟩ | ⟨VLF⟩ | ⟨VLF⟩ | ⟨VHL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ |
| IoTB₈ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨VHL⟩ | ⟨HFL⟩ | ⟨VLF⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ |
| IoTB₉ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VHL⟩ | ⟨NFL⟩ | ⟨NFL⟩ | ⟨LFL⟩ | ⟨VLF⟩ | ⟨NFL⟩ | ⟨LFL⟩ |
| IoTB₁₀ | ⟨LFL⟩ | ⟨LFL⟩ | ⟨NFL⟩ | ⟨VHL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨HFL⟩ | ⟨LFL⟩ | ⟨HFL⟩ | ⟨NFL⟩ |

## TABLE 4.3

Valuation of IoT Barriers to Waste Management in Smart Cities Using TFNs by All Experts

| Expert₁ | IoTB₁ | IoTB₂ | IoTB₃ | IoTB₄ | IoTB₅ |
|---|---|---|---|---|---|
| IoTB₁ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ |
| IoTB₂ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.00, 0.00, 0.25⟩ |
| IoTB₃ | ⟨0.75, 1.00, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.25, 0.50⟩ |
| IoTB₄ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.00, 0.00, 0.25⟩ |
| IoTB₅ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.00, 0.00, 0.25⟩ |
| IoTB₆ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.50, 0.75, 1.00⟩ |
| IoTB₇ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.75, 1.00, 1.00⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.75, 1.00, 1.00⟩ |
| IoTB₈ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.75, 1.00, 1.00⟩ | ⟨0.50, 0.75, 1.00⟩ |
| IoTB₉ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.75, 1.00, 1.00⟩ | ⟨0.00, 0.00, 0.25⟩ |
| IoTB₁₀ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.75, 1.00, 1.00⟩ | ⟨0.50, 0.75, 1.00⟩ |

| Expert₁ | IoTB₆ | IoTB₇ | IoTB₈ | IoTB₉ | IoTB₁₀ |
|---|---|---|---|---|---|
| IoTB₁ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.75, 1.00, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.25, 0.50, 0.75⟩ |
| IoTB₂ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.25, 0.50, 0.75⟩ |
| IoTB₃ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.50, 0.75, 1.00⟩ |
| IoTB₄ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ |
| IoTB₅ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.00, 0.25, 0.50⟩ |
| IoTB₆ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.25, 0.50, 0.75⟩ |
| IoTB₇ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.25, 0.50, 0.75⟩ |
| IoTB₈ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.50, 0.75, 1.00⟩ |
| IoTB₉ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.25, 0.50, 0.75⟩ |
| IoTB₁₀ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.00, 0.00, 0.25⟩ |

| Expert₂ | IoTB₁ | IoTB₂ | IoTB₃ | IoTB₄ | IoTB₅ |
|---|---|---|---|---|---|
| IoTB₁ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ |
| IoTB₂ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.00, 0.00, 0.25⟩ |
| IoTB₃ | ⟨0.75, 1.00, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.25, 0.50⟩ |
| IoTB₄ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.00, 0.00, 0.25⟩ |
| IoTB₅ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.00, 0.00, 0.25⟩ |
| IoTB₆ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.50, 0.75, 1.00⟩ |
| IoTB₇ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.75, 1.00, 1.00⟩ | ⟨0.00, 0.25, 0.50⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.75, 1.00, 1.00⟩ |
| IoTB₈ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.50, 0.75, 1.00⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.75, 1.00, 1.00⟩ | ⟨0.50, 0.75, 1.00⟩ |
| IoTB₉ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.75, 1.00, 1.00⟩ | ⟨0.00, 0.00, 0.25⟩ |
| IoTB₁₀ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.25, 0.50, 0.75⟩ | ⟨0.00, 0.00, 0.25⟩ | ⟨0.75, 1.00, 1.00⟩ | ⟨0.50, 0.75, 1.00⟩ |
