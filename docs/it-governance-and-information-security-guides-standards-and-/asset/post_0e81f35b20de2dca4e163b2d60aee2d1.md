
| VARIABLE | LABEL |
| --- | --- |
| ACTIONS | Translation of the concept into concrete actions |
| NB_PRIORITY | Number of priority areas for engagement in a governance approach to information security |
| TECHNO | Safety-related technology choices |
| ALIGN | Aligning information security with organizational strategy |
| RISQUE | Risk management and reduction of potential impacts to an acceptable level |
| RESSOURCE | Management of information resources |
| PERF | Evaluation of performance through the monitoring of safety indicators |
| CREAT | Creating value through optimization of security investments |

## Appendix 2

TABLE A.3 The Determinants of the Adoption of Information Security Governance (Logit Model)

| VARIABLE | MODEL 1 | MODEL 2 | MODEL 3 | MODEL 4 | MODEL 5 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Constante | -0.6983 (0.7184) | -1.0383 (0.7556) | -0.8540 (0.7376) | -0.8863 (0.7183) | **-1.3922*** (0.8330) |
| INDUS | -0.7934 (0.6144) | -0.8387 (0.6465) | -0.8684 (0.5454) | -0.9198 (0.5674) | **-0.9606*** (0.5735) |
| SERV FINA | Référence 0.5037 (0.6239) | Référence 0.5275 (0.6538) | Référence 0.4239 (0.6666) | Référence 0.4853 (0.6844) | 0.5987 (0.7237) |
| TURNO | 0.3165 (0.5239) | 0.3389 (0.5330) | 0.3490 (0.5373) | 0.3156 (0.5333) | 0.2554 (0.5479) |
| NB_INVOLVED | **0.5983*** (0.1736) | **0.6254*** (0.1773) | **0.5867*** (0.1717) | **0.5993*** (0.1739) | X |
| INVOLVED | X | X | X | X | **1.5375*** (0.5569) |
| COMPETITORS | X | X | X | X | **1.1348*** (0.5654) |
| NB_BENEF | **0.3875*** (0.1350) | **0.3397*** (0.1336) | **0.3935*** (0.1440) | **0.3098*** (0.1335) | **0.2548*** (0.1203) |
| NB_CHALL | -0.3223 (0.2129) | X | X | X | X |
| MANAGEMENT | X | X | **-1.2745*** (0.6844) | -1.2000 (0.7198) | X |
| ACTIONS | X | **-1.9048*** (0.8893) | X | **-1.8085*** (0.9912) | **-2.1447*** (0.9564) |
| NB_PRIORITY | 0.1763 (0.2763) | 0.1117 (0.2579) | -0.1153 (0.2530) | 0.1346 (0.2534) | 0.1734 (0.2634) |
| Number of observations | 836 | 836 | 836 | 836 | 836 |
| % concordance | 87.4 | 87.6 | 87.4 | 88.4 | 87.7 |

Significance threshold: ***1%; %5%; %10%.
Coefficient, the standard deviation in parentheses.

![](img/62b08fcc83049d99252c223afe5d1c9e_232_0.png)

# Information Security Governance: A Maturity Framework Based on ISO/IEC 27001

## 7.1 INTRODUCTION

Many organizations today face a global governance revolution that could directly impact their information management practices. Information security has become an integral part of daily life, and organizations must ensure that their information security systems are an integral part of everyday life. In distributed and dynamic services, security must not be limited to providing a strategy taking into account business, organizational, and technical dimensions (Nassar et al., 2009). Besides, security must be seen as an ongoing process that aims to optimize security investments and ensure the sustainability of the measures implemented (Lomas, 2010).

However, IT security governance is a real challenge in an open service environment (Maleh et al., 2018). We propose approaching the problem of security by a practical approach of governance, allowing us to identify various aspects of IT security and propose adequate security measures to the context (Huang et al., 2007). Improving security has emerged as one of the priorities across all business lines, as the aerospace industry and strategic resources can be ideal targets for espionage by nation-states (Williams et al., 2006).

Many malicious actors no longer content themselves with thwarting the means of protection. Instead, they survey and exploit various weaknesses in the targeted environment (Galliers & Leiden, 2014). IT and security executives have to make complex calculations and decisions about security with limited information (Dhillon et al., 2016). They need to make decisions based on analyzing opportunities, risks, and security. Information security governance (ISG) issues are at the forefront of any discussions for organization's information assets, which includes considerations for managing risks, data and costs.

The problem is that the security governance framework designed to guide organizations in their IT security strategy but does not define the practical framework for implementation or measure the organization's engagement in IS security (NIST, COBIT, ISACA and international standards like ISO 27000 and ISO 15408). The first reports or articles in academic journals that evoke the governance of information security date back to the early 2000s. The proposed best practices are designed to guide organizations in their IT security governance (Yassine Maleh et al., 2021). The main contributions of the proposed frameworks are as:

- It includes standards, methodologies, and processes that align policy, business, and technological approaches to address information security governance;
- It provides a prioritized, flexible, repeatable, performance-based, and cost-effective approach, including information security measures and controls, to help owners and operators of critical infrastructure identify, assess, and manage information security;
- It identifies areas for improvement to be addressed through future collaboration with particular standards and standard-developing organizations;
- It is consistent with voluntary international standards (ISO27000, NIST, COBIT, ISACA).

This chapter proposes a practical maturity framework to evaluate the organization's maturity state and improve the IS security governance level according to their needs and resources. This chapter is structured as follows: Section 2 presents the theoretical framework and describes the proposed maturity framework for information security governance. Section 3 discusses the results of the implementation through a practical use case. Finally, section 4 presents the summary of this chapter.

## 7.2 THEORET FRAMEWORK

ISG frameworks can be successfully implemented by adopting best practices (Williams, 2001). Von Solms (2005) indicated that companies realize that instead of establishing information security governance environment on an ad hoc basis, it is preferable to follow an internationally recognized framework. Several resources can be used as a guide for information security governance, for example:

- Control Objectives for Information Technology and Related Technologies (COBIT) that help mitigate risk, assess the maturity of strategic alignment and value of IT delivery (Mataracoglu & Ozkan, 2011; Rau-Kounovsky et al., 2010; Saetang & Haider, 2011; Simmonson et al., 2008)
- National Institute of Standards and Technology (NIST) IT Governance 2008 (Dlamini et al., 2009)
- International Organization for Standardization (ISO/International Electromechanical Commission (IEC) 27000 family of safety standards (ITG, 2008) that are ISO17799 (Spafford, 2003) and ISO27001 (Mataracoglu & Ozkan, 2011)
- Certified Information Systems Professional (CISSP) (Harris, 2007)

Von Solms (2005) discussed the advantages and disadvantages of COBIT and ISO17799 and stated that both are good for information security governance and are complementary, when used together, can bring benefits to the organization. COBIT allows information security to be integrated into a broader IT framework, which means that it is available if the company decides to integrate the rest of the framework. WORKBIT focuses on what needs to be done but does not provide detailed guidelines on how to do it, but only addresses information security and is not integrated into a broader IT governance framework. ISO17799, on the other hand, provides more detailed guidance on how things should be done, is the only framework that allows an organization to obtain third-party audit certification (Saint-Germain, 2005).
