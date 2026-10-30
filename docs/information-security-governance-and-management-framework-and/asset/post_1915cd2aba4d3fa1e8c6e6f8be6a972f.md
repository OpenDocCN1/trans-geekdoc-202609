
![](img/90693339cd50db9a18259ad447383b45_205_0.png)

Figure 9.3 Modeling operational costs.

![](img/90693339cd50db9a18259ad447383b45_205_1.png)

Figure 9.4 Confidence interval for ROI.

operational costs of the new solution. ROI will therefore be calculated as the difference in operational costs between the current solution (status quo) and the new solution.

Another advantage of a model like this is its simulation capabilities. We can observe changes in the BE point and the evolution of ROI by changing parameters such as the cost of the project and the evolution of operational expenses. In the absence of accurate measurements, this will highlight trends and also an ROI confidence interval (Figure 9.4).

There are numerous IS change projects requiring profitability modeling, such as setting up a team responsible for operations and security monitoring, introducing a new intrusion detection system, introducing new means of authentication, etc. All these cases involve determining the evolution of real costs or the cost–benefit ratios of the new solution compared with the old one.

**EXAMPLE**

A new role-based access rights management system will

- Improve efficiency in granting privileges
- Automatically propagate privileges to target platforms
- Validate privileges at regular frequencies
- Offer more flexibility for new needs

A simple calculation of ROI can be made based on the following data: project cost, annual operational cost of the new solution, and annual operational cost of the current solution for the same volume of processed access rights (same result). Operational costs will be obtained by adding labor costs, infrastructure costs, and indirect costs (e.g. errors). Since it is difficult to accurately estimate the operational benefit of a new solution, some assumptions and simulations can be made to arrive at an ROI confidence interval as shown in Figure 9.4.

*Can we answer the question “How is our security?”*

## 9.4 Measuring the State of Security

Security program posture, capacity, and maturity are synonyms for means that allow the state of security to be presented in a concise and standardized way. The need to answer the question “How is our security?” has spurred security managers to develop different measuring and presentation tools. Governance requires simple, standardized ways to visualize the state of security. To make an analogy, analyzing risks allows us to understand our “enemies” (threats), while security posture allows us to understand our “weapons” (quality of the controls).

As already mentioned, being compliant with a standard does not mean having adequate security. The different standards or good practices can, however, be used under certain conditions to assess security posture. The standards present the processes that are required but do not propose evaluation criteria or gradations of conformity. There are also no recommendations on how to satisfy the requirements.

**EXAMPLE**

Control objective A.8.3 Media handling in ISO 27002 recommends controls to “prevent unauthorized disclosure, modification, removal or destruction of information stored on media”. The standard presents objectives and good practices but does not give indications on how it should be implemented. This process can have different levels of maturity in companies ranging from “non-existent” to “optimized” through all intermediate levels.

Some standards provide criteria for evaluating the security level. ISO 15408—Evaluation criteria for IT security (Common Criteria) enables the security certification of a computer system or product. A system that meets the requirements of a certain level also meets the requirements of a lower level. A similar approach to measuring resilience is proposed in the Software Engineering Institute “Measures for Managing Operational Resilience”, Allen, Curtis, SEI, 2011. Resilience is assessed as being at a certain level if it meets the requirements of that level, including the requirements of the previous levels.

### 9.4.1 Maturity Models

Maturity models generally evaluate processes according to a scale of values. Standards such as International Organization for Standardization (ISO) 27001 or National Institute of Standards and Technology (NIST) may be used to establish a list of processes or control objectives for which maturity will be assessed. The maturity model then proposes evaluation criteria for each process on a scale of values. Many examples of value scales exist, such as the one proposed by ISO/International Electrotechnical Commission (IEC) 15504 Information technology—Process assessment (Figure 9.5).

Evaluation criteria for assigning a maturity value to a process or control objective must be designed to avoid the risk of arbitrary choice. They must be sufficiently explicit and, above all, unambiguous. The quality of a maturity model therefore depends on the quality of the evaluation criteria that are proposed for each process or objective being evaluated. An example of evaluation criteria for Control objective 5 Information security policies of the ISO 27001 standard is given in Table 9.1.

![](img/90693339cd50db9a18259ad447383b45_207_0.png)

Figure 9.5 Different process maturity levels according to ISO 15504.

**Table 9.1 Example of Maturity Evaluation Criteria**

| Evaluation Objective | Evaluation Criteria 0: Incomplete, 1: Performed, 2: Managed, 3: Established, 4: Predictable, 5: Optimizing | Maturity Level |
|---|---|---|
| Information security policies | 0: There is no security policy<br>1: Some formal instructions exist and are applied<br>2: Security policy exists formally and covers the entire IS<br>3: The security policy exists, and its application is controlled<br>4: The security policy is applied and updated<br>5: The security policy is regularly adapted to the risks and needs of the business units | 2 |

![](img/90693339cd50db9a18259ad447383b45_210_0.png)

**Figure 9.7** Metrics associated with assumptions.

To facilitate metric definition, a strategy would be to subdivide the initial assumption into subassumptions and then define the metrics in relation to these subassumptions so as to be able to confirm or refute them (Figure 9.7).

Different assumption-based measuring methods exist, such as the “McKinsey Diagnostic Method”, Goal–Question–Metric (GQM) (The Goal Question Metric Approach, Basili, Caldiera, Rombach, University of Maryland, 1994).

**EXAMPLE**

To ensure that all critical processes are taken into account as part of disaster recovery procedures following major incidents, it was decided to check whether service-level agreements (SLAs) were defined and tested.

| Assumption/Objective | Subassumption | Metrics |
|---|---|---|
| There is a clear SLA on the time to recovery for critical processes | All critical processes are formally identified | Number of critical processes identified/total number of critical processes |
|  | There is an SLA for time to recovery for all identified critical processes | Number of critical processes without an adequate SLA |
|  | Recovery tests include all critical processes | Number of critical processes tested during a period |

*How are security goals set and progress toward them measured?*

## 9.6 Measuring Progress toward Security Goals

The balanced scorecard (BSC) is a popular tool for tracking performance and advancing toward goals that support the business strategy [The Balanced Scorecard: Translating Strategy into Action, Robert S. Kaplan, David P. Norton, Harvard Business Review Press, 1996]. As a well-known management tool, it provides a formal basis to establish and communicate results. It can be used to monitor security performance, thereby helping to position security as an equal partner with other business units. As a tool for monitoring security objectives, it can also facilitate management’s appreciation of security issues.

Financial performance alone does not provide all the information needed to assess the contribution of a unit to the consolidated results of the company. The BSC approach advocates benchmarking according to the objectives set in the following four perspectives: Operations, Client Relationship, Evolution (Learning and Growth), and Finance. The four perspectives must contribute to supporting the company’s strategy and vision (Figure 9.8). A core question is associated with each perspective to guide the user in choosing the objectives and performance indicators that will be applied.

BSC best practices in the field of security mention in particular the importance of aligning objectives with those of the business. The security strategy as defined earlier should serve as a high-level reference when developing measurement objectives and the indicators that will be associated with them. Strategic objectives can be complemented by more detailed objectives in each of the BSC perspectives. Following are some recommendations for the development of BSCs for security governance.

**Operations Perspective:** “How can we improve our security processes?”

We will measure to improve the performances of our security processes to better support the business and align with the company’s strategy. We will measure process efficiency and associated costs.

![](img/90693339cd50db9a18259ad447383b45_211_0.png)

Figure 9.8 Four perspectives in the balanced scorecard.
