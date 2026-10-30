# Security Controls

In this chapter, you will

+   - Determine the appropriate control to meet the goals of security
+   - Examine the controls used to ensure confidentiality
+   - Examine the controls used to ensure integrity
+   - Examine the controls used to ensure availability
+   - Examine the controls used to ensure safety

Security controls are the mechanisms employed to minimize exposure to risk and mitigate the effects of loss. Using the security attributes of confidentiality, integrity, and availability associated with data, it is incumbent upon the security team to determine the appropriate set of controls to achieve the security objectives. The elements confidentiality, integrity, and availability are commonly referred to as the CIA of security.

# Confidentiality

Confidentiality typically comes to mind when the term security is brought up. Confidentiality is the ability to keep some piece of data a secret. In the digital world, encryption excels at providing confidentiality. Confidentiality is used on stored data and on transmitted data. In both cases, symmetric encryption is favored because of its speed and because some asymmetric algorithms can significantly increase the size of the object being encrypted. In the case of a stored item, symmetric methods are favored, both for speed and because there really isn’t a key exchange problem. In the case of transmitted data, public key cryptography is typically used to exchange the secret key, and then symmetric cryptography is used to ensure the confidentiality of the data being sent.

Asymmetric cryptography does protect confidentiality, but its size and speed make it more efficient at protecting the confidentiality of small units for tasks such as electronic key exchange. In all cases, the strength of the algorithms and the length of the keys ensure the secrecy of the data in question.

Another method of protecting confidentiality is through the use of access controls. Access controls can restrict access to an object based on user IDs and access control lists (ACLs). This is a common method used in file systems because it provides relative protection that is efficient, although not as strong as encryption.