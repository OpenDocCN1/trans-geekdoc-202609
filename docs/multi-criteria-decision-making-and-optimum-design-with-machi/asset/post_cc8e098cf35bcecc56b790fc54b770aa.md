
# Enhancing Multicriteria Decision-Making

Converting the cipher text $c^* = 30$ into a trapezoidal fuzzy number $< 10, 20, 30, 40>$. For $x$, choose between $(10,40)$, Let $x = 38$.

```
$\mu_m(38) = \frac{\frac{d-x}{d-c}}{\frac{40-38}{40-30}} = 0.2$
```

Now the cipher text is $(10,20,0.2,40)$; Key = 38; Range = 10

- (a) First-level decryption

```
$\mu_m(38) = \frac{Encrypted fuzzy number \times Range}{d-c^*}$
$mu_m(38) = \frac{0.2 \times 10}{d-c} \text{ where } d-c^* = range$

$40 - c^* = 10$
```

- (b) Second-level decryption

```
$m_{17} = \frac{30^1(mod \ 17) + 15}{3} = 9.3$
$m_{19} = \frac{30^1(mod \ 19) + 15}{3} = 8.6, m_{23} = \frac{30^1(mod \ 23) + 15}{3} = 7.3$
$m_{29} = \frac{30^1(mod \ 29) + 15}{3} = 5.3, m_{31} = \frac{30^1(mod \ 31) + 15}{3} = 15$
$m_{27} = \frac{30^1(mod \ 37) + 15}{3} = 15$
$
$:. m = m_{31} = m_{37} = \dots = 15$
```

Hence the original message is found as 15

# 17.4 APPLICATIONS

In the realm of MCDM, the RSA cryptosystem finds application primarily in sensitive data and communication channels within decision-making processes that involve multiple stakeholders, criteria, and sensitive information. MCDM involves the exchange of critical and confidential information among multiple parties. RSA encryption can be employed to secure these communications, ensuring that the criteria, evaluations, and decisions remain confidential and protected from unauthorized access or interception.

# Multi-Criteria Decision-Making with Machine Learning

In scenarios where various decision criteria are assessed and weighted for decision-making, RSA encryption can secure the criteria values and weights. This ensures that any manipulation or unauthorized access to these criteria is prevented, maintaining the integrity of the decision-making process. MCDM processes often involve collaboration by safeguarding shared documents, databases, or communication channels and maintaining confidentiality and integrity throughout the collaborative decisionmaking process. In all these applications, the RSA cryptystem plays a crucial role in ensuring confidentiality, integrity, and authenticity within MCDM processes. employing RSA encryption, sensitive information remains secure, fostering trust among stakeholders and ensuring the reliability of decision-making outcomes.

Here we give an example of combining RSA with TFNs for multiple criteria: education, experience, skills, and personality traits. Criteria weights (the importance assigned to each criterion) for each candidate are encrypted using RSA to maintain confidentiality and integrity. Then, TFNs are employed to represent the uncertainty and imprecision associated with evaluating each candidate. Expert opinions or historical data are used to assign TFNs representing the education level, years of experience, skill proficiency, and personality traits of each candidate, as in the following TFNs for Candidate A:

- Education: [3.5, 4, 4.5, 5] on a scale of 1 to 5
- Experience: [5, 6, 7, 8]
- Skills: [0.7, 0.75, 0.78, 0.85]
- Personality Traits: [2, 3, 4, 5]

The candidates are evaluated across the criteria using fuzzy weighted sums, and the aggregated evaluations, encrypted with RSA, are decrypted using the RSA private key, allowing access to the final decision values for each candidate. Based on the decrypted fuzzy values, the hiring decision-makers select the candidate with the highest overall performance, considering all criteria for the job position. By integrating RSA for securing criteria weights and information and employing TFNs for fuzzy evaluations, this approach ensures confidentiality, prevents unauthorized access to sensitive data, incorporates uncertainty in evaluations, and facilitates reliable decision-making in selecting the most suitable candidate for the job.

# 17.5 CONCLUSION

The combination of the TFNs, CRT, and RSA cryptystems provides an effective for improving security and effectiveness in cryptographic processes. Because it relies on the computational complexity of factoring big prime numbers for asymmetric encryption, the RSA method offers a solid foundation for secure communication. By dividing the modular exponentiation into smaller, separate computations, integrating CRT with RSA offers useful optimization. Furthermore, by adding an extra degree of uncertainty and imprecision to the cryptographic system, the use of TFNs improves privacy protection and provides even another layer of security by

# Enhancing Multicriteria Decision-Making

making it more difficult for adversaries to decode information. The synergy between these mathematical ideas creates opportunities for additional research and development in the field of cryptography, offering more robust and effective cryptographic systems for protecting sensitive data in an increasingly digital world, even as technology and security threats grow more complex.

Network systems use cryptographic techniques in various fields to protect data, ensure privacy, authenticate users, and secure communications. Military agents employ cryptanalysis to decrypt communications, providing valuable information for decision-making. The effectiveness of the approach we discuss in this chapter heavily relies on the and quality of the data used to define fuzzy numbers and criteria weights; inaccurate or incomplete data can lead to unreliable results, and assigning membership to trapezoidal numbers can introduce bias and variability in the decision-making process.

# REFERENCES

- [1] Meenakshi, A., & Shivangi Mishra, J. (2023, October). The Modular Product of Two Graph Structures. In 2023 First International Conference on Advances, Electronics and Computational Intelligence (ICAECCI) (pp. 1–7). DOI: 10.1109/ICAEECCI5547.2023.1030796
- [2] Meenakshi, A., & Mythei, O. (2023, October). Mathematical Modeling of Social Networks with Hypergraphs. In 2023 First International Conference on Advances, Electronics and Computational Intelligence (ICAECCI) (pp. 1–6). DOI: 10.1109/ICAEECCI5547.2023.1030798
- [3] Rivest, R. L., Shamir, A., & Adleman, L. (1978). A Method for Obtaining Signatures and Public-Key Cryptography. Journal of the ACM, 21(2), 120–126. https://dl.acm.org/doi/10.1145/359340.359394
- [4] Sahu, J., Singh, V., & Chopra, A. (2021). An Enhanced Version of RSA to Increase the Security. Journal of Network Communications and Emerging Technologies, 7(4), 1–4. https://www.jnet.org/Manuscripts/Volume-7-Issue-4-01.pdf
- [5] Somani, N., & Mangal, D. (2014). An Improved Cryptographic System. International Journal of Computer Applications, 105(16). https://www.ijcaonline.org/archives/volume-105/1846-9820
- [6] Meenakshi, A., & Mythei, O. (2023). Applications of Neurosonic Social Network Using Max Product Networks. Journal of Intelligent & Fuzzy Systems. http://org/10.3233/JIFS-2223844
- [7] Ning, L., Ali, Y., Ke, H., Nazir, S., & Huani, Z. (2020). Hybrid Approach of Selecting Lightweight Cryptographic Cipher by ISO and NIST Security Requirements for the Internet of Things. IEEE Access, 8, 226015–226017.
- [8] Padma, C. J., Bhagavan, V. S., & Srinivas, B. (2016). RSA Encryption Using Three Mersenne Primes. International Journal of Computer Science, 14(4), 2273–2278. https://www.tsijnals.com/articles/rsa-encryption-using-mersenne-primes.pdf
- [9] Pius, A., & Kirubaharan, D. R. (2021). Application of Cryptography in Data Privacy using Fuzzy Theory. Journal of Discrete Mathematics and Cryptography, 24(8), 2389–2401. DOI: 10.1080/09720529.2021.2014146
- [11] Meenakshi, A., & Dhanushiya, S. (2023, October). Fuzzy Networking using Vertex Order Coloring and Efficient Diffusion. In 2023 First International Conference on Advances, Electronics and Computational Intelligence (ICAECCI) (p. 1–11). IEEE. DOI: 10.1109/ICAECCI58427.2023.1037090
- [12] Al-Hamami, A. H., & Aldarish, I. A. (2012). Enhanced Method for RSA Cryptosystem. In 2012 International Conference on Advanced Computer Science Applications and Technologies (ACSAT) (p. 402–408). IEEE. https://doi.org/10.1109/ACSAT.2012.10
- [13] Ivy, B. P., Mandu, P., & Kumar, M. (2012). A modified RSA cryptosystem on prime numbers. International Journal of Engineering and Computer Science, 1(2), 63–66. https://gsitebuilder.com/files/writeable/uploads/hostgar581320/file/63-66.
- [14] Amin, R., & Biswas, G. P. (2015). An Improved RSA-Based User Authentication and Key Agreement Protocol in Tmis. Journal of Medical Systems, 39(8), 79. https://pubmed.nlm.nih.gov/26123833/
- [15] Jalaludin, J., & Romindo, R. (2020). Implementation of Combination Vigere Cipher and RSA in Hybrid Cryptosystem for Text Security. JISTECH International Journal of System and Technology, 4(1), 471–481. http://ijjest.org/ijjest/index.php/article/85
- [16] Mungo, D. E., Fu, X., Xian, Y., & Wang, X. (2023). A Novel Image Encryption Using Chaotic Maps and Fuzzy Numbers for Secure Transmission of Information. Applied Sciences, 13(12), 7113. https://doi.org/10.3390/as13127113
- [17] Meenakshi, A., & Bagshar, J. (2021). Combining Multi-Criteria Efficient Diffusion. Indian Journal of Social Sciences and Humanities, 69, 197–204. DOI: 10.9798/ijssh.27315.00917-8
- [18] Tan, T., Alaimis, Hardi. RSA Set Theory for Encryption and Decryption. Decision Making (MCDM) Methods with Building Information Modeling (BIM): A Review. Automation in Construction. DOI: 10.1016/j.autcon.2020.103451
- [19] Alaimis, M. G., Aminudin, N., Che-Him, N., Sufahani, S., Khalid, K., & Roslan, R. (2018). Modified Prime RSA Cryptosystem. In Journal of Physics: Conference Series (Vol. 995, no. 1, p. 012030). IOP Publishing. DOI: 10.1088/1742-6596/995/1/012030
- [20] Abdaoui, A., Erbad, A., Al-Ali, A. K., Mohamed, A., & Guizani, M. (2021). Fuzzy Elliptic Curve Crypt for Authentication in Internet of Things. IEEE Internet of Things Journal, 9(12), 9987–9998. DOI: 10.1109/JIOT.2021.3121350
- [21] Kumar, A., Sah, B., Singh, A. R., Deng, Y., He, X., Kumar, P., & Bansal, R. C. (2017). A review of Multi-Criteria Decision Making (MCDM) towards sustainable energy development. Renewable and Sustainable Energy Reviews, 69, 596–609. DOI: 10.1016/j.rser.2016.11.191
