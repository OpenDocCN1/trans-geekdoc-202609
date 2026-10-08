
## 246 BLOCKCHAIN IN HEALTH SCIENCES

**Table 11.2** Experimentation to find parameter setting.

| Parameter | Setting |
| --- | --- |
| Data size | 40KB |
| Length of AES key | 256 Bits |
| Length of RV | 256 Bits |
| Number of policies (Encryption & Decryption) | 1,2,5,10,20,40,80,100 |
| Number of policies (Policy update) | 20 |
| Number of Concurrent Policy Update Requests | 1,2,4,10,50,100,200,500,1000,1500,300,5000,10000,25000,50000,100000 |

Encryption and decryption for each scheme are broken by different entities, such as the Data Owner, Proxy/Fog node, and Data User, in Figures 11.2 and 11.3. This paper introduces a new data sourcing scheme to significantly reduce both encryption and decryption costs compared to existing solutions. Unlike the traditional methods, reliant on computationally expensive partial CP-ABE encryption, the proposed scheme leverages the more efficient AES encryption throughout. This strategic choice translates to notable performance improvements in two key areas: Encryption and Decryption efficiency.

Conventional schemes witness increasing encryption times at the data owner (DO) with more attributes. In contrast, the proposed scheme maintains consistently low encryption times regardless of attribute count. This efficiency stems from its exclusive reliance on AES encryption, dramatically more efficient than its bulkier counterparts. The proposed scheme shines in achieving the absolute lowest and most consistent decryption cost at the data user (DU) side. Once again, this efficiency stems from the preference for the nimble AES encryption, standing in stark contrast to the demanding full CP-ABE decryption employed by other methods.

Our scheme equipped with streamlined AES encryption, the lowest cost and generates a consistently low encryption time. In contrast, schemes [3] and [23], weighed down by partial CP-ABE encryption, incur a slightly higher cost at the DO side, and this further inflates with an increasing number of attributes in the access structure. The increasing number of attributes as a burden in methods [3] and [22] due to their reliance on full CP-ABE decryption, significantly inflating their decryption time. On the other hand, our scheme proudly maintains the lowest and most consistent decryption cost at the DU side, solidifying its position as the most efficient solution.

## 4) Updates to Policies throughout

A test was performed on a suggested policy update method for fog nodes. The experiment demonstrated that the suggested method could produce between 100 and 1,000 simultaneous policy update requests at a rate of up to 680 re-encryptions per second. Despite hardware restrictions, the system's high rate of 359.71 re-encryption per second was appropriate for scenarios involving large numbers of users.

The applicability and feasibility of the suggested system are examined in the discussion section, along with how well the scheme performs under various load scenarios. This analysis highlights the possible advantages of the suggested approach and highlights its significance in healthcare data management. Our suggested solution's effective encryption and decryption procedures are one of its main advantages, especially for end users, which include both data and users owners. Interestingly, this approach does not scale with the amount of attributes, which is a benefit that increases end-users' encryption and decryption efficiency. This feature becomes especially important when handling large amounts of private medical data that need to be accessed quickly and securely. Another essential function of healthcare data management is policy updates. Multiple end users may carry out these updates concurrently or at separate times. Our tests show that throughput is increasing even with more re-encryption processes, which frequently call for a significant amount of processing power.

### Policy Update Throughput

![](img/fea41dfefcdce94be900e86661d80689_257_0.png)

**Figure 11.3** Throughput of policy updating.

![](img/fea41dfefcdce94be900e86661d80689_258_0.png)

**Figure 11.4** Comparison of the proposed and existing methods regarding the encryption of 100 KB data.

Figure 11.4 illustrates how resilient the scheme is and how well it can handle the strain brought about by policy modifications. Notably, end users are relieved of performance-related worries because all encryption and decryption processes associated with Cipher text-policy attribute-based encryption (CP-ABE) take place at the fog layer. It is crucial to note that while our experiment simulates the fog layer using a single machine, this does not fully utilize the capabilities of fog computing. The capacity of fog computing to distribute and share resources among nearby fog nodes is a key benefit. This offers a fascinating field for further research on how to use fog computing capabilities to further improve our suggested plan. This conversation highlights the usefulness and efficiency of our method in the context of the proposal, especially when handling sensitive medical data. The suggested plan ultimately improves the effectiveness and integrity of healthcare data management by strengthening data security and streamlining end-users' data access. The design of this plan is in perfect harmony with the overarching goal of creating a patient-centered healthcare ecosystem that values confidentiality, data-driven decision making, and stakeholder collaboration. At the core of this shift is the secure exchange of healthcare data via blockchain, combined with the real-time data processing powers of fog computing. Patients and healthcare professionals can take care of their health with the help of the Personalized Health Insights Dashboard, which provides real-time insights, recommendations, and interactive data visualization. Fog computing concepts are aligned with the scheme, which streamlines coordination and delivers practicality, efficiency, and real-time processing capabilities. The plan is supported by literature that highlights the importance of encryption, blockchain, and efficient computing in healthcare data management. This creative idea signals the beginning of a collaborative, patient-centered era in healthcare and has the potential to be further improved by leveraging fog computing.

## 11.6 Conclusion

In conclusion, a fundamental change towards data protection and effective access has been made in healthcare with the integration of secure blockchain, fog computing, and EMR sharing. EMRs powered by IoT improve patient care and decision-making. However, issues with key security for IoT devices, CP-ABE implementation, and cloud data privacy still exist. The landscape is made more complex by recent access control policy revisions. The discussion of data privacy and access control benefits from this study review of available options. It lays the groundwork for more effective methods to secure EMR sharing, boosting the technology advancement of healthcare.

In the future, the system could become even more by investigating cutting-edge encryption methods, streamlining communication protocols, and utilizing cutting-edge innovations like homomorphic encryption, which enables safe computation on encrypted data. Furthermore, regular encryption algorithm changes and ongoing cooperation among the concerned parties would improve the system's overall posture. To create a more complete and integrated healthcare ecosystem, continuing research and development efforts should concentrate on improving user experience, scalability, and interoperability with other healthcare system.

## References

- 1. Tandon, A., Dhir, A., Najmul Islam, A.K.M., Mäntymäki, M., Blockchain in healthcare: A systematic literature review, synthesizing framework and future research agenda. Comput. Ind., 122, 103290, 2020. ISSN 0166-3615, mhtts://doi.org/10.1016/j.compind.2020.103290.
- 2. Bonomi, F., et al., Fog Computing: Principles, Architectures, and Applications, in: Internet of Things (IoT). Springer, 12 January 2016.
- 3. Chelladurai, U., Pandian, S., Ramasam, K., a blockchain based patient electronic health record storage and integrity management for e-Health systems. Health Policy Technol., 10, 4, 100513, 2021. ISSN 2211, https://doi.org/10.1016/j.hlpt.2021.100513.
- 4. Andrew, J., Israelvel, Martin Sagayam, K., Bhushan, B., Sei, Y., Eunice, J., Blockchain for healthcare systems: Architecture, security challenges, trends.
