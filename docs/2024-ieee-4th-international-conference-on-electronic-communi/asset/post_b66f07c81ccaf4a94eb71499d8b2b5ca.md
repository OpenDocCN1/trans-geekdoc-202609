
(3) Creating a rating set

$$V = \{V_1, V_2, \dots, V_n\}\tag{3}$$

(4) Single Factor Fuzzy Evaluation

$$\underline{R}_i = \left(\frac{r_{i1}}{V_1} + \frac{r_{i2}}{V_2} + \dots + \frac{r_{in}}{V_n}\right)\tag{4}$$

$$\underline{R} = \begin{pmatrix} r_{11} & r_{12} & \cdots & r_{1n} \\ r_{21} & r_{22} & \cdots & r_{2n} \\ \cdots \\ r_{m1} & r_{m2} & \cdots & r_{mn} \end{pmatrix}\tag{5}$$

(5) Fuzzy Comprehensive Evaluation

$$\underline{B} = \underline{A} \circ \underline{R}\tag{6}$$

$$\underline{B} = (a_1,a_2,\dots,a_m) \circ \begin{pmatrix} r_{11} & r_{12} & \cdots & r_{1n} \\ r_{21} & r_{22} & \cdots & r_{2n} \\ \cdots \\ r_{m1} & r_{m2} & \cdots & r_{mn} \end{pmatrix} = (b_1,b_2,\dots,b_n)\tag{7}$$

included among these

$$b_j = \bigvee_{i=1}^{m} (a_i \land r_{ij})\;(j = 1,2,\dots,n)\tag{8}$$

## 3. Methods

For the foundational design flow, we developed the stages of dispersion, iterative computation, convergence, and delivery in design. At each stage, outputs were used as inputs. In this approach, we used a multi-diamond model and employed the methodology in Section 2 for the research, analysis, and evaluation of the model’s feasibility.

### 3.1. Multi-Diamond Model

The design framework of the Multi-Diamond Model comprises seven stages: observation, requirement proposal, market research, design objectives, conceptual proposals, concept evaluation, and proposal validation. In the Double Diamond Model’s design process, the discovery phase corresponds to observation, requirements, and market analysis. The definition phase aligns with design objectives derived from market analysis, while the development phase corresponds to conceptual solutions. The delivery phase aligns with evaluating conceptual solutions, involving testing and feasibility assessment. The process starts with an input point, flowing through the diamond, generating an output (Figure 5). This output becomes the input for the next stage, continuing the process within the diamond. Iteration results in a complete result denoted by a bolded hollow circle, symbolizing integrated output and input. In the figure, arrows present the potential for backtracking and iteration when facing challenges.

In the observation phase, everyday experiences or Maslow’s hierarchy of needs are presented for inspiration. The emphasis is on identifying and exploring issues and understanding stakeholder perspectives using surveys, interviews, and the 5W1H technique. Simultaneously, market analysis and target trees are used to shape the final design. Utilizing image boards, design scripts, and scenario planning, conceptual design solutions are envisioned within specific contexts. By evaluating these solutions using merits, drawbacks, and feasibility, followed by prototyping for validation, the groundwork is established for subsequent development and assessment.

The questionnaire was designed to understand how customers chose hairstyles and colors, identified their problems, and validated the consistency of the requirements in the second stage. The questionnaire consisted of basic demographic information, a survey on face shape and hairstyle/hair color preferences, and customers’ feelings regarding their appearance. Integrating the findings, demands, and customer behavior patterns was confirmed as the final output.

According to the survey results (Figure 6), 80% of the respondents conducted research before visiting a hair salon. The primary methods included using social media and referencing hairstylist portfolios. Approximately 20% did not perform pre-research due to a lack of ideas or a preference for direct communication with hairstylists. These findings represent the customer experience process before visiting a hair salon.

![](img/8c60744401b2d3c0d4f32428cc43626b_192_0.png)

Figure 6. Flowchart of customer experience.

The design objective of the fourth diamond model was to confirm the ultimate purpose of the analysis by analyzing users’ understanding of their hairstyles, face shapes, and behaviors to explore their needs and entry points for hairstylists. The fifth to seventh diamond models involved a coherent operation that converted qualitative text into quantitative data. In the approach, the fuzzy logic of the fuzzy evaluation method was used to understand and analyze subjective user feedback involving qualitative concepts.

In the questionnaire, customers were asked about their understanding of their face shape, hairstyle, and hair color, as well as the difficulty in selecting a hairstyle and hair color. Scores of 0, 0.25, 0.5, 0.75, and 1 were used, ranging from “not at all understanding” to “very understanding,” and from “not at all difficult” to “very difficult.” Tables 1 and 2 present the percentage results of these scores.

Table 1. Understanding face shape, hairstyle, and hair color.

|  | Not at All Understanding | Not Understanding | Average | Well Understanding | Very Well Understanding |
|---|---|---|---|---|---|
| Face Shape | 0.15 | 0.15 | 0.26 | 0.43 | 0.11 |
| Hair Shape | 0.16 | 0.21 | 0.29 | 0.29 | 0.05 |
| Hair Color | 0.26 | 0.3 | 0.12 | 0.25 | 0.07 |

Table 2. Difficulty in choosing hairstyle and hair color.

|  | Very Little Difficult | Not Difficult | Average | Difficult | Very Difficult |
|---|---|---|---|---|---|
| Hair Style | 0.09 | 0.23 | 0.18 | 0.36 | 0.14 |
| Hair Color | 0.1 | 0.27 | 0.11 | 0.33 | 0.19 |

## 5. Results and Discussion

The fuzzy comprehensive evaluation was used as follows.

The customer’s knowledge of face shape, hairstyle, and hair color was analyzed.

(1) Factor set U1 = { Face Shape, Hair Style, Hair Color }

(2) Weight set A₁ = (0.3, 0.35, 0.35)

(3) Ratings V₁ = { Very unaware, unaware, average, aware, very aware }

(4) Single Factor Fuzzy Evaluation: Face Shape (x1), Hair Style (x2), Hair Color (x3), we get

R(x1) = (0.15 0.15 0.26 0.43 0.11)
R(x2) = (0.16 0.21 0.29 0.29 0.05)
R(x3) = (0.26 0.3 0.12 0.25 0.07)

Therefore, the one-factor evaluation matrix is given by

R₁ = [[0.15, 0.15, 0.26, 0.43, 0.11], [0.16, 0.21, 0.29, 0.29, 0.05], [0.26, 0.3, 0.12, 0.25, 0.07]]

(5) Fuzzy Comprehensive Evaluation B = A ∘ R

B = ( 0.26 / Very unaware + 0.21 / unaware + 0.29 / average + 0.3 / aware + 0.11 / very aware )

Since the sum of the values of the factors in the evaluation result exceeded 1, normalization was required.

∴ 0.26 + 0.21 + 0.29 + 0.3 + 0.11 = 1.17

The rating result was adjusted to

(0.22 0.18 0.25 0.26 0.09)

The results of this evaluation were as follows.

- In total, 22% of people did not understand their face shape and suitable hair style and color at all.
- In total, 18% did not understand their face shape and hair color.
- In total, 25% understood their face shape and hair color.
- In total, 26% understood their face shape and hair color well.
- In total, 9% understood their face shape and hair color very well.

The customer's difficulty in choosing their own hair style and color was as follows.

(1) Factor set U2 = { Hair Style, Hair Color }

(2) Weight set A₂ = (0.6, 0.4)

(3) Rating V₂ = { Very little difficult, not difficult, average, difficult, very difficult }

(4) Single Factor Fuzzy Evaluation: Hair Style (x4), Hair Color (x5), we get

(5) R(x₄) = (0.09 0.23 0.18 0.36 0.14)
R(x₅) = (0.1 0.27 0.11 0.33 0.19)

Therefore, the one-factor evaluation matrix is given by

R₂ = [[0.09, 0.23, 0.18, 0.36, 0.14], [0.1, 0.27, 0.11, 0.33, 0.19]]

(6) Fuzzy Comprehensive Evaluation $B=A\circ R$

$$B=\left(\frac{0.1}{\text{Very little difficult}}+\frac{0.27}{\text{not difficult}}+\frac{0.18}{\text{average}}+\frac{0.36}{\text{difficult}}+\frac{0.19}{\text{very difficult}}\right)$$

Since the sum of the values of the factors in the evaluation result exceeded 1, normalization was required.

$$\therefore\ 0.1+0.27+0.18+0.36+0.19=1.1$$

The rating result was adjusted to

$$(0.09\ 0.25\ 0.16\ 0.33\ 0.17)$$

The results of this evaluation were as follows.

- In total, 9% felt ‘very little difficulty’ choosing their hairstyles and colors.
- In total, 25% felt ‘no difficulty’ in choosing their hairstyles and colors.
- In total, 16% felt ‘average difficulty’ in choosing their hairstyles and colors.
- In total, 33% felt ‘difficulty’ in choosing their hairstyles and colors.
- In total, 17% felt ‘very difficult’ in choosing their hairstyles and colors.

## 6. Conclusions

In the multi-diamond design, services, event planning, and corporate operational decision-making need to be determined. This flexible and dynamic model provides a framework for adaptability based on different activities in various domains. Divergence, convergence, and iteration are emphasized at each stage, departing from traditional approaches. This approach adds granularity to the design process, enabling designers to address challenges more precisely and adapt to rapidly changing demands. The multi-diamond design model offers a framework for design thinking and integrates divergence, convergence, and iteration. This approach is a problem-solving method for innovation. This model can guide designers to successfully solve diverse challenges in different domains. Simultaneously, it encourages the exploration of new possibilities while solving problems.

**Author Contributions:** Conceptualization, S.-W.H. and Y.-J.T.; methodology, S.-W.H. and Y.-J.T.; validation, Y.-J.T.; formal analysis, S.-W.H. and Y.-J.T.; investigation, Y.-J.T.; resources, S.-W.H. and Y.-J.T.; data curation, S.-W.H. and Y.-J.T.; writing—original draft preparation, Y.-J.T.; writing—review and editing, S.-W.H. and Y.-J.T.; visualization, Y.-J.T.; supervision, S.-W.H. and Y.-J.T.; project administration, S.-W.H. and Y.-J.T. All authors have read and agreed to the published version of the manuscript.

**Funding:** This research received no external funding.

**Institutional Review Board Statement:** Not applicable.

**Informed Consent Statement:** Not applicable.

**Data Availability Statement:** The original contributions presented in the study are included in the article, further inquiries can be directed to the corresponding author.

**Conflicts of Interest:** The authors declare no conflicts of interest.

## References

- 1. Available online: https://www.designcouncil.org.uk/our-resources/the-double-diamond/ (accessed on 1 June 2023).
- 2. Suoheimo, M.; Määttä, K. Service Design Thinking Method for Educational Leaders. In *Educational Governance Research*; Springer Science and Business Media B.V.: Berlin/Heidelberg, Germany, 2024; pp. 81–100. [CrossRef]
- 3. Schleith, J.; Tsar, D. Triple Diamond Design Process. In *HCI International 2022—Late Breaking Papers. Design, User Experience and Interaction*; Kurosu, M., Yamamoto, S., Mori, H., Soares, M.M., Rosenzweig, E., Marcus, A., Rau, P.-L.P., Harris, D., Li, W.-C., Eds.; Springer International Publishing: Cham, Switzerland, 2022; pp. 136–146.
- 4. Jian, Z. *Methodology of Industrial Design*; Beijing University of Technology Press: Beijing, China, 1995. (In Chinese)
