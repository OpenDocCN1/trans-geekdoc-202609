
## 2.3.1 Example of Developing a Corporate Cyber Risk Management Methodology

![Figure 2.38 Corporate risk management.](Images/fig00160.jpg)

**Figure 2.38** Corporate risk management.

Currently, there are more than a hundred ways to manage (evaluate and optimize) cyber risks (Figures 2.38–2.40) [34, 133, 244]. For example, the `ISO 31010` standard offers about three dozen ways. However, modern digital enterprises prefer to develop their own cyber risk management techniques. The fact is that the known models and methods of risk management are not always well adapted to the significant number of enterprise business processes. Many times, methods that require a detailed and accurate value assessment of assets are eliminated first. The fact is that the value of assets changes daily, and assessing this dynamic is not a trivial task, given that a digital enterprise's activities, its business processes and operations, are supported by hundreds of complex technological subsystems and related services. Classical cyber-risk scenario analysis methods are not always suitable here [34].

![Figure 2.39 The role and place of cyber security risk management.](Images/fig00161.jpg)

**Figure 2.39** The role and place of cyber security risk management.

![Figure 2.40 Cyber risk consequences.](Images/fig00162.jpg)

**Figure 2.40** Cyber risk consequences.

The probability of a cyber security incident is equal to the product of the probabilities of all the events that ultimately lead to it (Figures 2.41–2.43). The mentioned models and methods have proven to be effective in analyzing failures and `accessibility` problems; however, they are not suitable for assessing, for example, the risk of information leakage. The common methods of assessing cyber risks, based on scoring, require some additions, since they do not allow combining many factors influencing the risk into a single assessment.

![Figure 2.41 System of risk factors.](Images/fig00163.jpg)

**Figure 2.41** System of risk factors.

![Figure 2.42 Criteria for assessing the risk factors' probability indicator.](Images/fig00164.jpg)

**Figure 2.42** Criteria for assessing the risk factors' probability indicator.

![Figure 2.43 Criteria for assessing risk factors of damage index.](Images/fig00165.jpg)

**Figure 2.43** Criteria for assessing risk factors of damage index.

Thus, there is often a need to develop one's own model and methods for managing cyber risks with acceptable reliability and complexity. It is necessary to solve the following problems for that:

1.  Develop an adequate cyber risk assessment model that allows allocating company resources, primarily for managing cyber risks at a critical level.
2.  Build a simple and at the same time convenient process for evaluating cyber risks. This is especially relevant for cyber security experts working in the framework of `Agile` development techniques for various pilots, where development and implementation processes are significantly accelerated, requirements for the final product can change every week, and there is no possibility to allocate a large amount of time for the risk assessment process itself (more than five minutes).
3.  Give the ability to take into account the views of many experts from various areas. It is necessary to envisage the possibility of attracting specialists from various fields, including business, IT, and cyber security, to assess cyber risks to obtain an objective result.
4.  Create a universal model for identifying and evaluating cyber risks. This allows aggregating the assessment results of cyber risks into a single rating, comparing cyber risks, and assigning priority.
5.  Monitor the dynamics of the cyber risk level in changing internal or external factors of enterprise development. Here, the levels of cyber risks change with the transformation of cyber threats and the state of protective measures, as well as with business development. In practice, the impact of decisions made on the risk landscape is evaluated, and the patterns of the relationship between changes in the magnitude of risks and the recorded actual damage are studied in order to study the dynamics of changes in the cyber risk levels.

As a rule, the classical risk formula is taken as the basis for developing a cyber risk management model—this is the probability of an incident multiplied by the damage from its implementation [[128]–130, 133]. Next, the list of risk factors that affect these two key parameters is determined. It is taken into account that the probability is influenced by the list of actual threats and vulnerabilities of the relevant technological platform of the enterprise, as well as by the potential attacker and the effectiveness of corporate protection to ensure cyber security. The damage parameter is influenced by the criticality (inadmissibility of downtime) of the information asset, the data being processed, the disruption of the normal functioning of processes, as well as the dissatisfaction of customers and partners, possible reputational losses, and regulatory sanctions.

As a result, there are three main steps to cyber risk assessment.

*   **Step 1. Formation of a risk factor system for the assessed type of cyber risk**
    Here, for each type of cyber risk, experts determine a list of current threats, vulnerabilities, organizational and technical protection measures.
*   **Step 2. Expert assessment of risk factors**
    At this step, the experts independently assess each risk factor on a four-level scale (Figures 2.43 and 2.44). At the same time, the critical criteria are developed, taking into account the specifics and scale of business. The weight of each risk factor is also determined here in order to reduce the impact of non-critical factors on the final risk indicator. For example, for the risk of information leakage, the damage assessment from the process malfunction can be ignored, and the "information category" parameter acts as decisive and its weight should be large. The weights of the factors themselves are ranked on a scale from 1 to 9.
*   **Step 3. Cyber risk rating calculation**
    Here, the key difference between the proposed model and the cyber risk management method and the well-known qualitative methods is as follows. It is possible to combine a large number of opinions and weights in one risk rating value, whereas the classical tabular method, where the risk level is at the intersection of the corresponding probability row and the damage column, does not allow managing so many expert opinions. A matrix calculation method is used to calculate the final risk rating, which aggregates all of the qualitatively assessed factors into one quantitative value. This allows taking into account the total number of experts participating in the process and the range of their opinions, as well as the value difference, which increases the assessment objectivity. The result of the assessment is the `R` risk rating, expressed as a number from `0` to `1`, and the corresponding risk level, as defined in Table 2.11.

![Figure 2.44 Differences between discrete and continuous scales of risk level.](Images/fig00166.jpg)
