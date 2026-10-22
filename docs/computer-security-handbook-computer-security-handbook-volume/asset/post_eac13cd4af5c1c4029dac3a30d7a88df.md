
either bank. Thus, there is no conflict of interest in either Barbara’s or Percival’s representation of a bank and the toy company. But there is a path along which information can flow from Barbara to Percival, and vice versa, that enables a conflict of interest to occur. Barbara can read information from an object in The Big Bank’s company data set and write it to an object in The Biggest Toy Company’s company data set. Percival can read the information from the object in The Biggest Toy Company’s company data set, thereby effectively giving him access to The Big Bank’s information—which is a conflict of interest. That he needs Barbara’s help does not detract from the problem. The goal of the model requires that this conspiracy be prevented. The next rule does so:

**Definition.** The CW*-property says that a subject s can write to an object o if and only if both of the following conditions are met:

- 1. The CW-simple security property allows s to read o; and
- 2. All unsanitized objects that s can read are in the same company data set as o.

Now Barbara can read objects in both The Big Bank’s company data set and The Biggest Toy Company’s data set. But when she tries to write to The Biggest Toy Company’s data set, the CW*-property prevents her from doing so as condition 2 is not met (because she can read an object in The Big Bank’s company data set).

This also accounts for sanitized objects. Suppose that Skyler represents The Biggest Toy Company and no other company. He can also read information from the sanitized class. When he tries to write to an object in The Biggest Toy Company’s company data set, he meets both conditions of the CW-simple security property (because he has only read objects in that company data set), and all unsanitized objects that he can read are in the same company data set as the object he can read. Thus, both conditions of the CW*-property are met, so Skyler can write the object.

The conditions of the CW*-property are very restrictive; effectively, a subject can write to an object only if it has access to the company data set containing that object, and no other company data set except the company data set in the sanitized class. But without this restriction, conflicts of interest are possible.

### 9.4.5 Summary.

The four models discussed in this section have played critical roles in the development of our understanding of computer security. Although it is not the first model of confidentiality, the Bell-LaPadula model describes a widely used security scheme. The Biba model captured notions of “trust” and “trustworthiness” in an intuitive way, and recent advances in the analysis of programs for vulnerabilities have applied that model to great effect. The Clark-Wilson model moved the notion of commercial integrity models away from multilevel models to models that examine process integrity as well as data integrity. The Chinese Wall model explored conflict of interest, an area that often arises when one is performing confidential services for multiple companies or has access to confidential information from a number of companies. These models are considered classic because their structure and ideas underlie the rules and structures of many other models.

## 9.5 OTHER MODELS.

Some models examine specific environments. The Clinical Information Systems Security model28 considers the protection of health records, emphasizing accountability as well as confidentiality and integrity. Traducement29 describes the process of real estate recordation, which requires a strict definition of integrity and accountability with little to no confidentiality.

Other models generalize the classic models. The best known are the models of noninterference security and deducibility security. Both are multilevel security models with two levels, HIGH and LOW. The noninterference model30 defines security as the ability of a HIGH subject to interfere with what the LOW subject sees. For example, if a HIGH subject can prevent a LOW subject from acquiring a resource at a particular time, the HIGH subject can transmit information to the LOW subject. In essence, the interference is a form of writing, and must be prevented, just as the Bell-LaPadula model prevents a HIGH subject from writing to a LOW object. The deducibility model31 examines whether a LOW subject can infer anything about a HIGH subject’s actions by examining only the LOW outputs. Both these models are useful in analyzing the security of systems32 and intrusion detection mechanisms,33 and led to work that showed connecting two secure compute systems may produce a nonsecure system.34 Further work is focusing on establishing conditions under which connecting two secure systems produces a secure system.35

## 9.6 CONCLUSION.

The efficacy of mathematical modeling depends on the application of those models. Typically, the models capture system-specific details and describe constraints ensuring the security of the system or the information on the system. If the model does not correctly capture the details of the entire system, the results may not be comprehensive, and the analysis may miss ways in which security could be compromised.

This is an important point. For example, the Bell-LaPadula model captures a notion of what the system must do to prevent a subject cleared for TOP SECRET leaking information to a subject cleared for CONFIDENTIAL. But if the system enforces that model, the TOP SECRET subject could still meet the CONFIDENTIAL subject and hand her a printed version of the TOP SECRET information. That is outside the system and so was not captured by the model. But if the model also embraces procedures, then a procedure is necessary to prevent this “writing down.” In that case, the flaw would be in the implementation of the procedure that failed to prevent the transfer of information—in other words, an incorrect instantiation of the model, exactly what Dorothy Denning’s comment in the introduction to this section referred to.

The models described in this section span the foundational (access-control matrix model) to the applied (Bell-LaPadula, Biba, Clark-Wilson, and Chinese Wall). All play a role in deepening our understanding of what security is and how to enforce it.

The area of mathematical modeling is a rich and important area. It provides a basis for demonstrating that the design of systems is secure, for specific definitions of secure. Without these models, our understanding of how to secure systems would be diminished.

## 9.7 FURTHER READING

- Anderson, R. “A Security Policy Model for Clinical Information Systems,” Proceedings of the 1996 IEEE Symposium on Security and Privacy (May 1996): 34–48.
- Bell, D., and LaPadula, L. “Secure Computer Systems: Unified Exposition and Multics Interpretation,” Technical Report MTR-2997 rev. 1, MITRE Corporation, Bedford, MA (March 1975).
- Biba, K. “Integrity Considerations for Secure Computer Systems,” Technical Report MTR-3153, MITRE Corporation, Bedford, MA (April 1977).
- Bishop, M. Computer Security: Art and Science. Boston: Addison-Wesley Professional, 2002.
- Brewer, D., and M. Nash. “The Chinese Wall Security Policy,” Proceedings of the 1989 IEEE Symposium on Security and Privacy (May 1989): 206–212.
- Clark, D., and D. Wilson. “A Comparison of Commercial and Military Security Policies,” Proceedings of the 1987 IEEE Symposium on Security and Privacy (April 1987): 184–194.
- Cortier, V., and S. Kremer. Formal Models and Techniques for Analyzing Security Protocols—Volume 5 Cryptology and Information Security Series. IOS Press, 2011.
- Cremers, C., and S. Mauw. Operational Semantics and Verification of Security Protocols. Springer, 2012.
- Demillo, D., D. Dobkin, A. Jones, and R. Lipton, eds. Foundations of Secure Computing. New York: Academic Press, 1978.
- Denning, D. “The Limits of Formal Security Models,” National Information Systems Security Conference, October 18, 1999; available at www.cs.georgetown.edu/~denning/infosec/award.html
- Denning, P. “Third Generation Computer Systems,” Computing Surveys 3, No. 4 (December 1976): 175–216.
- Engeler, E. Introduction to the Theory of Computation. New York: Academic Press, 1973.
- Ferraiolo, D., J. Cugini, and D. Kuhn. “Role-Based Access Control (RBAC): Features and Motivations,” Proceedings of the Eleventh Annual Computer Security Applications Conference (December 1995): 241–248.
- Gougen, J., and J. Meseguer. “Security Policies and Security Models,” Proceedings of the 1982 IEEE Symposium on Privacy and Security (April 1982): 11–20.
- Graubert, R. “On the Need for a Third Form of Access Control,” Proceedings of the Twelfth National Computer Security Conference (October 1989): 296–304.
- Haigh, J., R. Kemmerer, J. McHugh, and W. Young. “An Experience Using Two Covert Channel Analysis Techniques on a Real System Design,” IEEE Transactions in Software Engineering 13, No. 2 (February 1987): 141–150.
- Harrison, M., and W. Ruzzo, “Monotonic Protection Systems.” In D. Demillo et al., eds. Foundations of Secure Computing, pp. 337–363. New York: Academic Press. 1978.
- Harrison, M., W. Ruzzo, and J. Ullman. “Protection in Operating Systems,” Communications of the ACM 19, No. 8 (August 1976): 461–471.
- Ko, C., and T. Redmond. “Noninterference and Intrusion Detection,” Proceedings of the 2002 IEEE Symposium on Security and Privacy (May 2002): 177–187.
- Lampson, B. “Protection.” Proceedings of the Fifth Princeton Symposium of Information Science and Systems (March 1971): 437–443.
- Lipner, S. “Non-Discretionary Controls for Commercial Applications.” Proceedings of the 1982 IEEE Symposium on Privacy and Security (April 1982): 2–10.
- Mantel, H. “On the Composition of Secure Systems,” Proceedings of the 2002 IEEE Symposium on Security and Privacy (May 2002): 88–101.
- McCullough, D. “Non-Interference and the Composability of Security Properties,” Proceedings of the 1987 IEEE Symposium on Privacy and Security (April 1988): 177–186.
- Sandhu, R. “The Typed Access Matrix Model,” Proceedings of the 1992 IEEE Symposium on Security and Privacy (April 1992): 122–136.
