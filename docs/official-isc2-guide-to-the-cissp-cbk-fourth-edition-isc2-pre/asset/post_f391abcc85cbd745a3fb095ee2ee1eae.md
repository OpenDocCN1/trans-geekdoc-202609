
Often, the risk assessment an organization conducts is a combination of qualitative and quantitative methods. Fully quantitative risk assessment may not be possible because there is always some subjective input present, such as the value of information. Value of information is often one of the most difficult factors to calculate.

It is clear to see the benefits, and the pitfalls, of performing a purely quantitative analysis. Quantitative analysis allows the assessor to determine whether the cost of the risk outweighs the cost of the countermeasure. Purely quantitative analysis, however, requires an enormous amount of time and must be performed by assessors with a significant amount of experience. Additionally, subjectivity is introduced because the metrics may also need to be applied to qualitative measures. If the organization has the time and manpower to complete a lengthy and complex accounting evaluation, this data may be used to assist with a quantitative analysis; however, most organizations are not in a position to authorize this level of work.

Three steps are undertaken in a quantitative risk assessment: initial management approval, construction of a risk assessment team, and the review of information currently available within the organization. Single Loss Expectancy (SLE) must be calculated to provide an estimate of loss. SLE is defined as the difference between the original value and the remaining value of an asset after a single exploit. The formula for calculating SLE is as follows:

**SLE = Asset Value (in $) × Exposure Factor**
**(loss due to successful threat exploit, as a %)**

Losses can include lack of availability of data assets due to data loss, theft, alteration, or denial of service (perhaps due to business continuity or security issues).

Next, the organization would calculate the Annualized Rate of Occurrence (ARO). ARO is an estimate of how often a threat will be successful in exploiting a vulnerability over the period of a year.

When this is completed, the organization calculates the Annualized Loss Expectancy (ALE). The ALE is a product of the yearly estimate for the exploit (ARO) and the loss in value of an asset after an SLE. The calculation follows:

**ALE = SLE x ARO**

Note that this calculation can be adjusted for geographical distances using the Local Annual Frequency Estimate (LAFE) or the Standard Annual Frequency Estimate (SAFE).

Given that there is now a value for SLE, it is possible to determine what the organization should spend, if anything, to apply a countermeasure for the risk in question. Remember that no countermeasure should be greater in cost than the risk it mitigates, transfers, or avoids. Countermeasure cost per year is easy and straightforward to calculate. It is simply the cost of the countermeasure divided by the years of its life (i.e., use within the organization). Finally, the organization is able to compare the cost of the risk versus the cost of the countermeasure and make some objective decisions regarding its countermeasure selection.

## Identify Threats and Vulnerabilities

### Identify Vulnerabilities

NIST Special Publication 800–30 Rev. 1, page 9, defines a vulnerability as "an inherent weakness in an information system, security procedures, internal controls, or implementation that could be exploited by a threat source."41

In the field, it is common to identify vulnerabilities as they are related to people, processes, data, technology, and facilities. Examples of vulnerabilities could include:

- Absence of a receptionist, mantrap, or other physical security mechanism upon entrance to a facility
- Inadequate integrity checking in financial transaction software
- Neglecting to require users to sign an acknowledgment of their responsibilities with regard to security, as well as an acknowledgment that they have read, understand, and agree to abide by the organization’s security policies
- Patching and configuration of an organization’s information systems are done on an ad hoc basis and, therefore, are neither documented nor up to date

Unlike a risk assessment, vulnerability assessments tend to focus on the technology aspects of an organization, such as the network or applications. Data gathering for vulnerability assessments typically includes the use of software tools, which provide volumes of raw data for the organization and the assessor. This raw data includes information on the type of vulnerability, its location, its severity (typically based on an ordinal scale of high, medium, and low), and sometimes a discussion of the findings.

Assessors who conduct vulnerability assessments must be expert in properly reading, understanding, digesting, and presenting the information obtained from a vulnerability assessment to a multidisciplinary, sometimes nontechnical audience. Why? Data that are obtained from the scanning may not truly be a vulnerability. False-positives are findings that are reported when no vulnerability truly exists in the organization (i.e., something that is occurring in the environment has been flagged as an exposure when it really is not); likewise, false-negatives are vulnerabilities that should have been reported and are not. This sometimes occurs when tools are inadequately "tuned" to the task, or the vulnerability in question exists outside the scope of the assessment.

Some findings are correct and appropriate but require significant interpretation for the organization to make sense of what has been discovered and how to proceed in remediation (i.e., fixing the problem). This task is typically suited for an experienced assessor or a team whose members have real-world experience with the tool in question. It is important for the security practitioner to understand that prioritization of the findings and assessment of their potential impact needs to be done by one or more qualified individuals, as opposed to attempting to automate this process. The reason for this is that many automated tools will assign ratings or rankings that are not consistent with the organization’s view, based on the BIA. For instance, if the organization interprets vulnerability "A" as a low impact, low priority vulnerability due to the outcome of the BIA, but the tool ranks vulnerability "A" as a high priority, medium impact vulnerability, then resources may be inappropriately tasked to remediate a vulnerability that is not important to the organization.

### Identify Threats

The National Institute of Standards and Technology (NIST), in Special Publication (SP) 800–30 Rev. 1, pages 7 – 8, defines threats as "any circumstance or event with the potential to adversely impact organizational operations and assets, individuals, other organizations, or the Nation through an information system via unauthorized access, destruction, disclosure, or modification of information, and/or denial of service". In the OCTAVE framework, threats are identified as the source from which assets in the organization are secured (or protected).

NIST, in Special Publication (SP) 800-30 Rev.1, page 8, defines a threat-source as either:

- 1. Intent and method targeted at the intentional exploitation of a vulnerability or
- 2. A situation and method that may accidentally trigger a vulnerability.

Threat sources can be grouped into a few categories. Each category can be expanded with specific threats, as follows:

- Human — Malicious outsider, malicious insider, (bio) terrorist, saboteur, spy,

| How to Qualify Likelihood | Rating |
|---|---|
| **Skill**<br>High Skill Level Required ⇔ Low or No Skill Required | 1=High Skill Required ⇔ 5=No Skill Required |
| **Ease of Access**<br>Very Difficult to Do ⇔ Very Simple to Do | 1=Very Difficult ⇔ 5=Simple |
| **Incentive**<br>High Incentive ⇔ Low Incentive | 1=Low or No Incentive ⇔ 5=High Incentive |
| **Resource**<br>Requires Expensive or Rare Equipment ⇔ No Resources Required | 1=Rare/Expensive ⇔ 5=No Resource Required |
| **Total**<br>Add Rating and Divide by 4 | 1=E  2=D  3=C  4=B  5=A |

Figure 1.15(b) – Qualified Likelihood Rating

Once the terms are defined, impact can be calculated. If an exploit has the potential to result in the loss of life (such as a bombing or bioterrorist attack), then the ranking will always be high. In general, groups such as the National Security Agency view loss of life as the highest-priority risk in any organization. As such, it may be assigned the top value in the impact scale. An example: 51 to 100 = high; 11 to 50 = medium; 0 to 10 = low.

## Determination of Risk

Risk is determined as the byproduct of likelihood and impact. For example, if an exploit has a likelihood of 1 (high) and an impact of 100 (high), the risk would be 100.42 As a result, 100 would be the highest exploit ranking available. These scenarios (high likelihood, high impact) should merit immediate attention from the organization.

As the risk calculations are completed, they can be prioritized for attention, as required. Note that not all risks will receive the same level of attention, based on the organization’s risk tolerance and its strategy for mitigation, transfer, or avoidance of risk. Figure 1.16 shows another view of risk.
