
# Fuzzy Systems for Multicriteria Optimization

- **Structural Health Monitoring**: To evaluate the state of bridges, buildings, and other infrastructure, fuzzy logic is employed in structural health monitoring. To identify abnormalities, evaluate structural integrity, and forecast maintenance requirements, fuzzy inference can interpret sensor data.

- **Traffic Control Systems**: Intelligent transportation systems use fuzzy logic to optimize routes, manage traffic, and control traffic signals. By shifting traffic circumstances, fuzzy inference can lessen congestion and enhance overall traffic flow.

- **Communication Networks**: In the field of telecommunications, fuzzy logic is employed for fault detection, quality of service management, and dynamic bandwidth allocation. Fuzzy inference can enhance the efficiency of communication systems and maximize network resources.

- **Aerospace Engineering**: Autopilot systems, guiding, navigation, and control are among the functions in aerospace systems where fuzzy logic is utilized. Fuzzy inference can adjust to changing conditions and manage uncertainty in flight situations.

These examples show the flexibility of fuzzy inference for handling challenging engineering problems in various fields. For engineers looking for reliable and flexible solutions in practical applications, fuzzy logic is an invaluable tool due to its capacity to represent and manage uncertainty.

# 2.4 FUZZY MCDM

Fuzzy multicriteria decision-making (MCDM) is a sophisticated approach that combines fuzzy logic with decision-making strategies to tackle intricate issues with multiple criteria (Kaya et al., 2019). With this method, fuzzy sets are used to define criteria and alternatives, enabling decision-makers to communicate vague and subjective information using language.

Decision-makers can genuinely evaluate the links between criteria and alternatives by fuzzy pairwise comparisons and fuzzy weights, which are used to express the ambiguity in the importance of various criteria. Because the input data is fuzzy, fuzzy aggregation combine these individual evaluations to get overall fuzzy ratings for each option. Fuzzy MCDM approaches, including TOPSIS (technique for order of preference by similarity to ideal solution) and fuzzy analytic hierarchy, address language expressions and judgments. The method is particularly useful in real-world situations when there is a lot of uncertainty, inconsistency, and qualitative evaluations. Many industries, such as banking, environmental management, project selection, and resource allocation, have successfully used fuzzy multicriteria cost-benefit analysis. This technique makes decision-makers an effective tool for negotiating challenging decision-making scenarios.

# Multi-Criteria Decision-Making with Machine Learning

### 2.4.1 THE CONCEPT OF MCDM

MCDM was developed to handle circumstances in which there are multiple, frequently opposing, criteria or elements to consider. Traditionally, choices are usually made without explicitly taking into account the interdependencies between a group of criteria. On the other hand, MCDM offers a structured methodology for assessing and ranking options based on a variety of criteria, acknowledging the complexity of decision problems. The following are important aspects related to MCDM:

- **Multiple Criteria**: MCDM addresses decision-making situations in which decision-makers must take into account multiple factors. These standards can take multiple forms, encompassing quantitative and qualitative elements, expenses, advantages, and additional pertinent characteristics.

- **Decision Alternatives**: MCDM entails assessing and contrasting a range of possibilities or decision alternatives. These options stand for various plans of action, approaches, initiatives, or for a certain issue.

- **Criteria Weights**: Not all MCDM have the same weight. Weights are assigned by decision-makers to factors to indicate their relative importance. The significance of every criterion in the decision-making process is measured by these weights.

- **Pairwise Comparisons**: Decision-makers frequently have to state what they believe to be more important than others in the decision-making process. When comparing two sets of criteria by side, pairwise comparisons are used to determine which is preferred or of more value.

- **Ranking and Scoring**: MCDM offers a system for ranking or scoring for the alternatives based on the allocated weights and criteria evaluations. The aim is to find the most preferred or ideal option according to the decision-maker's objectives.

- **Decision Matrix**: An essential MCDM tool, a decision matrix arranges and displays data on criteria assessments, weights, and alternative ranks. It presents the choice problem in an organized manner.

- **Decision Support Systems**: To facilitate the evaluation and analysis of alternatives according to a range of criteria, MCDM employs decision support systems, including computational models and software tools. These tools support decision-makers in navigating difficult decisions.

- **Sensitivity Analysis**: By using MCDM, one can assess how changes to the values or weights of criteria affect the final rankings. This aids in decision-makers' comprehension of how resilient their choices are in various situations.

- **Subjectivity and Stakeholder Involvement**: MCDM promotes stakeholder involvement while acknowledging the subjectivity that is a part of decision-making. The preferences, values, and viewpoints of stakeholders are vital in determining the criteria, weights, and general decision-making process.

MCDM is used in many different domains, including engineering, project management, business, finance, and environmental management. It gives decision-makers a clear, methodical framework for managing intricate decision-making situations involving multiple, frequently incompatible criteria.

### 2.4.2 TRADITIONAL MCDM METHODS AND Limitations

Decision-makers have long relied on traditional MCDM techniques to help them assess and choose options based on a variety of criteria (Taherdoost & Madanchian, 2023). These techniques do have certain restrictions, though here are a few popular MCDM techniques along with their disadvantages:

- **Weighted Sum Model**: This model calculates the total score for each alternative multiplying the weights by the normalized scores. Each criterion is given a weight that indicates its significance. The subjectivity of weight assignment, possible bias, and the presumption of linear connections among criteria are some of the shortcomings.

- **Weighted Product Model**: The normalized scores for each criterion increased to their corresponding weight and multiplied to determine the total score for each choice in the Weighted Product Model. Sensitivity to extreme values, the presumption of criteria independence, and difficulties determining additive weights are some of the limitations.

- **Simple Additive Weighting**: The third method is called additive weighting, which combines criteria by multiplying the normalized score of each criterion by its weight and adding the results. Sensitivity to weight fluctuations and the presumption that criteria are equally significant within a given weight category are two limitations.

- **Analytic Hierarchy**: Analytic hierarchy creates a structured framework for decision-making by comparing criteria in pairs. The process reduces the possibilities for inconsistency, the difficulty of achieving consistent judgments in paired comparisons, and other limitations in handling a large number of criteria.

- **ELECTRE (Elimination et Choice Traduisant en Recherche)**: This group of outranking techniques evaluates substitutes to how well or poorly meet predetermined standards. Sensitivity to shifts in preference thresholds, challenges with imprecise information, and the possibility of rank reversal are some of the limitations.

- **TOPSIS**: TOPSIS offers options considering how close they are to the positive ideal solution and how far they are from the negative ideal solution. Sensitivity to the normalization method used, reliance on predetermined ideal solutions, and susceptibility to extreme values are some of the limitations.

- **Compromise Programming**: This technique looks for solutions that strike a balance between opposing requirements. Limitations include the impact of decision-makers' differing tastes and the challenge of identifying a suitable option.

- **Limitations across Traditional MCDM Methods**:

- **Subjectivity**: The dependability of the results might be impacted by the subjectivity introduced by traditional approaches, which frequently rely on
