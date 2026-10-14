# Test Your Understanding

+   22.
+   a. What is the strongest form of authentication?
+   b. List the functions of a PKI.
+   c. Can a firm be its own certificate authority?
+   d. What is the advantage of doing so?
+   e. Who creates a computer’s private key–public key pair?
+   f. How do CAs distribute public keys?
+   g. What is provisioning?
+   h. What is the prime authentication problem?
+   i. What can be done to reduce this risk?

strong procedures for who may submit someone for inclusion, who may approve it (always someone else), what identification is required, and how to handle exceptions. These procedures must be carefully enforced and audited.

# 5.7 Authorization

# 5.7 Explain authorizations.

Access control has three elements that we have called AAA—authentication, authorization, and auditing. So far, we have only looked at authentication. However, knowing the identity of the communication partner is not enough. The specific authorizations (permissions) of the communicating party also need to be defined. Not everyone who is authenticated may be allowed to do anything he or she wishes in every directory. (To give an analogy, you probably would not let some of the people you know to drive your car.)

# The Principle of Least Permissions

In planning authorizations, it is important to follow the principle of least permissions. This means that each person should only get the permissions that he or she absolutely needs to do his or her job. If the initial assignment of permissions is too narrow, additional permissions can be granted as needed.

> The principle of least permissions is that each person should only get the permissions that he or she absolutely needs to do his or her job.

To give an example, suppose that the system has permissions A, B, C, D, E, and F and that a person needs permissions A, C, and E. Suppose the person is only given the permissions that he or she needs. Then the person will be given A, C, and E.

What if a mistake is made, and the person only receives A and C? The answer is that E can be added later. The person will be inconvenienced until E is provided, but security is not violated. Assigning least permissions means that the system tends to fail safely, not giving each user too many permissions if an error is made.

The opposite approach is to give each user either full permissions or extensive permissions. This way, the user will always or almost always have the permissions they need to do his or her job. It is then possible to take away privileges that the user does not need. However, it is very easy to forget to take away a permission that allows the user to take actions that cause serious damage.