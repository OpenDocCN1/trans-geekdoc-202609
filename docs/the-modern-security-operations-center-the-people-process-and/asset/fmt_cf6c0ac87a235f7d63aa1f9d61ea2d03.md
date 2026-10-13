
Reducing risk isn’t always a simple fix, because new risk can be introduced based on what is being changed. Also, there will be a cost associated with each risk reduction option. If the cost outweighs the fix, it will not be worth mitigating the risk, leading to the choice of risk rejection. Risk isn’t an all-or-nothing measurement, either. There are different models that can be used to calculate the amount of risk. One example is the expected monetary value (`EMV`) analysis. `EVM` analysis is a statistical technique that calculates the average outcome when the future includes scenarios that might or might not happen. `EMV` analysis takes the value of each possible outcome and multiplies it by its probability of occurrence. The probability-weighted values of the possible outcomes are later added together. This approach can be extremely valuable because you not only are able to see the total cost if all risk were to be exploited, but you can also generate a more realistic dollar value of the overall risk when considering multiple situations, which is more realistic.

### EMV Approach

Let’s work through an example of using the `EMV` approach to risk analysis. For this example, let’s say there are eight different risks that your `SOC` must decide to deal with. Your `SOC` sponsor wants to understand the dollar value associated with all of the risk. You can create an `EMV` chart that features all eight risk items. You can estimate what the probability of each risk occurring would be as well as estimate the cost if the risk was to be exploited. What is more important is understanding the cost compared against the risk actually occurring. Let’s say for this example that accounting for all eight risks results in a required risk budget of $118,000. This large dollar value can be a huge ask for many organizations regarding a risk contingency budget; however, computing that the risk reality, known as `risk contingency`, is $33,500 may be more reasonable considering the likelihood that all events will not occur. It would be more likely that a few events occur, such as events C and E occur, which would mean $28,000 would be needed. Using the `EVM` budget, the $28,000 would be pulled from the $33,500 planned budget. Using the `EVM` in this manner allows for justification of a reasonable risk contingency budget that nontechnical leaders will need to understand. [Table 3-3](#ch03.xhtml#ch03tab03) shows the numbers from this example.

**TABLE 3-3** EMV Calculation Example

| Risk | Risk Probability | Cost Impact | Risk Contingency |
| --- | --- | --- | --- |
| **A** | 80% | $10,000 | $8,000 |
| **B** | 30% | $30,000 | $9,000 |
| **C** | 50% | $8,000 | $4,000 |
| **D** | 10% | $40,000 | $4,000 |
| **E** | 30% | $20,000 | $6,000 |
| **F** | 25% | $10,000 | $2,500 |
| **Total** | | **$118,000** | **$33,500** |

### Risk Documentation

Another risk management technique is to properly document each risk so that estimates and decisions can be made regarding the associated impact. [Table 3-4](#ch03.xhtml#ch03tab04) is an example format you can use to ensure the risk management team captures each risk that the organization needs to address. The asset owner and security engineer will need to work together and agree on what goes into this form to ensure that the results are calculated accurately. If the input is not accurate, using risk calculations such as the `EMV` technique would not provide useful results. It is also important to point out that the expected input for the empty [Table 3-4](#ch03.xhtml#ch03tab04) template could be pages of details.

**TABLE 3-4** Risk Documentation Template

| Name of Risk | Description | Source (with Explanation) | Likelihood of Occurrence (with Justification) | Severity of Impact (with Justification) | Controllability (with Justification) |
| --- | --- | --- | --- | --- | --- |
| 1. | | | | | |
| 2. | | | | | |
| 3. | | | | | |
| 4. | | | | | |
| 5. | | | | | |
| 6. | | | | | |
| 7. | | | | | |
| 8. | | | | | |

Each risk must be tracked during its lifecycle within the risk management response process. This can be done using a `risk register` system, which documents essential information for each risk that is identified. There are different factors to consider including in the `risk register` you choose to create. Use the following template as a bare minimum of content that you will need to capture and successfully track risk events:

*   Tracking Number/Date
*   Assigned Engineer(s)
*   Description
*   Cause
*   Impact
*   Severity and Likelihood
*   Risk Response
*   Root Causes

#### Addressing Risk

The next risk management concept is addressing risk. For vulnerability management, the mitigation process will be technical, which can include patches or incorporating security tools to protect the vulnerable system. Risk management mitigation can be much broader since risk can be anything from environmental to physical in nature. To accommodate this wide range of potential mitigation options, the risk management team must be able to define a business contingency plan and a corresponding implementation plan.

There are many factors that can impact both plans depending on the type of risk, what it impacts directly and indirectly, compliance considerations, health factors, and other factors. The following two lists are examples of templates that can be used by a risk management team member to collect information that will be needed for the risk management team to make a proper response. Notice that these documents are much more detailed than what was collected in the risk documentation template. There are many variations of both the risk documentation template and the business contingency documentation that can be used and should be adjusted to the risk being addressed.

**Business Contingency Plan**

*   Strategic Pre-Incident Changes
    *   Sensitive Data
    *   Normal Data Protection
    *   Disruption Data Protection
    *   Ethical Use of Data
    *   Customer Records
    *   Normal Security Measures
    *   Disruption Security Measures
    *   Ethical Use Protections
    *   Communication Plan
    *   Stakeholders
    *   Stakeholder Communications
    *   Restoration of Operations

**Implementation of Contingency Plan**

*   Strategic Incident Changes
    *   Communication of the CP
    *   Monitoring and Testing of the CP
    *   Adjustment of the CP
    *   Communication of Changes

### Risk Heat Mapping

One popular approach to quantifying risk is to use heat mapping, which provides a simplified view of the potential impact of an event. One method is to use the risk heatmap template shown in [Figure 3-6](#ch03.xhtml#ch03fig06). This template compares the probability of an incident against the severity, the two critical factors to understand the true threat of a risk. For example, a catastrophic risk that is extremely rare is a concern but can be seen as moderate because it is unlikely to occur. More elaborate heatmaps can include associated dollar costs for impact and mitigation using the `EMV` approach to calculate estimated risk contiguously planning.

![FIGURE 3-6 Risk Heatmap Example](Images/03fig06.jpg)

**FIGURE 3-6** Risk Heatmap Example

There are more topics to cover that fall under risk management, including expectations for addressing and recovering from risk. [Chapter 6](#ch06.xhtml#ch06), “[Reducing Risk and Exceeding Compliance](#ch06.xhtml#ch06),” is dedicated to dealing with risk and risk recovery.

## SOC Service 2: Vulnerability Management
