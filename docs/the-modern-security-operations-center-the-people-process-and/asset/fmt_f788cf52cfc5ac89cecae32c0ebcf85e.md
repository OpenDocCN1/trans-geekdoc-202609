
I find that when a SOC overstaffs a SOC service, it always has other SOC services that can use more help. In contrast, I constantly hear how SOC teams feel understaffed and overwhelmed with work. Based on these observations, if you have the ability to recruit more people for a SOC service, I advise you to take those people while you can. It’s a better option than later needing more people and not having them available!

### Service Maturity: If You Build It, They Will Come

Maturity is a critical component of a SOC service. A SOC doesn’t just obtain a service, they build it using internal or outsourced resources. For example, if I advise an organization to develop a vulnerability management service, doing so will take more than purchasing a vulnerability scanner. [Figure 3-5](#ch03.xhtml#ch03fig05) is a maturity model example taken from ISACA’s COBIT 2019 guideline. Not having a vulnerability management service would mean a grade zero maturity ranking for the vulnerability management SOC service. Acquiring a vulnerability scanner would allow for ad hoc scanning, raising the maturity of the vulnerability management service to grade one. As a repeatable program is developed, the maturity will also increase.

![FIGURE 3-5 Maturity Grading Scale Example](Images/03fig05.jpg)

**FIGURE 3-5** Maturity Grading Scale Example

Using a maturity measuring system is critical to the success of any SOC service for a few reasons:

*   You have a way to explain to nontechnical decision-makers why continuous investments are required to make a service successful. This will help overcome statements such as “we already bought you the tools you need.”
*   You can create improvement goals, which can include reward systems when goals are achieved. Reward systems lead to career growth and employee dedication to the SOC’s mission.
*   Maturity models can provide a potential roadmap to improve the quality of a service.
*   Maturity models highlight the important impact of people, process, and technology on a service, because all are required to meet higher-level maturity categories.

As you develop SOC services, you will need to evaluate at what maturity level they are operating. You can validate the results with the SOC sponsor, set goals for improving services, and plan for requirements in people, process, and technology to accomplish such improvements. Using this approach will allow for all technical and nontechnical parties to understand the current and potential future status of a SOC service. [Chapter 1](#ch01.xhtml#ch01) covered how to evaluate SOC maturity.

Let’s move into reviewing the eight fundamental services of mature SOC practices.

### SOC Service 1: Risk Management

Found in most SOCs around the world, risk management is a fundamental service because it deals with all forms of risk. This means other services are essentially a subset of risk management. For example, vulnerability management deals only with technical vulnerabilities, while risk management covers all forms of risk including nontechnical vulnerabilities such as the risk of social engineering attacks and the risk of physical security breaches.

#### Four Responses to Risk

Every organization has various forms of risk. The responsibility of the risk management team is to provide a response to encountered risk. An organization can take essentially four options as it responds to risk:

> **Note**
>
> There are other similar risk models that include the five options I have provided for responding to risk. [Chapter 9](#ch09.xhtml#ch09) highlights how ISO 27005-2018 suggests four options for responding to risk using similar language: risk retention, risk avoidance, risk modification, and risk sharing. As with all guidelines, the language might be different, but the concepts are the same.

*   **Reduce:** Apply a service, tools, or other countermeasures to reduce the risk
*   **Accept:** Identify that the risk is acceptable and do nothing
*   **Reject:** Identify that the risk is not acceptable but still do nothing
*   **Transfer:** Share or outsource the risk

> **Note**
>
> Accepting risk and rejecting risk are similar but there is a key difference. *Rejecting* doesn’t agree or accept the risk, however, nothing is done, while *accepting* the risk means the risk is within acceptable boundaries, so nothing needs to be done.

*Reducing* risk is likely what you expect as a response to risk. Reducing risk can be any type of people, process, or technology change that lowers the level of risk. Ideally, you want to remove the risk through measures such as patching a vulnerable server. If a patch isn’t available, you could place a security appliance in front of the vulnerable system, essentially preventing any external threat from exploiting the vulnerable server. Another option could be assigning a team to monitor traffic to the vulnerable server, allowing for a lower risk of the system being exploited without being noticed. [Chapter 9](#ch09.xhtml#ch09) reviews how to choose which is the best option for addressing vulnerabilities.

*Accepting* risk means the risk is at a tolerable level. An example of this is not buying earthquake insurance for a building located where there are not any earthquakes such as the state of Florida. Yes, an earthquake could occur in Florida, but it hasn’t happened in many years and likely will not happen anytime soon.

*Rejecting* the risk means the event is not acceptable but mitigation isn’t worth the effort. Looking back at the earthquake example, imagine your office is located where there are frequent earthquakes, such as California. Your SOC will have to decide if it’s worth mitigating the risk of earthquake damage, which can become extremely costly considering all that is required to secure a building. If it cost three times the effort to secure a building from earthquake damage, the decision could be made to reject the risk, meaning you do not accept it as within tolerance but it is not worth mitigating and, therefore, your SOC will deal with the potential damages if the threat occurs.

Keeping with our earthquake example, what many organizations do when faced with reducing the risk of natural disasters is *transfer* the risk through acquiring insurance. Rather than securing the building, the organization can acquire coverage that will reimburse losses if the event occurs, essentially transferring any concerns of the threat to another party, which in this case is the insurance company.

> **Note**
>
> I am often asked for my thoughts on cyber insurance. Personally, I believe that most organizations that don’t have cyber insurance eventually will. The main reason for this belief is the fact that no C-level executives for an organization would want to report they didn’t think they needed insurance following a major cyber incident. C-level execs would rather say “Yes, we have a partner that provides that service,” because when it comes to the public’s view of who is responsible for a cyber breach, all eyes are on the C-level team. Does every organization have cyber insurance today? Certainly not; however, the trend I am seeing is a hypergrowth in the issuance of cyber insurance policies as organizations learn about the option to use cyber insurance. [Chapter 9](#ch09.xhtml#ch09) looks closer at best practices for evaluating cyber insurance.

#### Reducing Risk
