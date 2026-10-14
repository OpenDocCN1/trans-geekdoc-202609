of real-world conditions. For instance, we have seen that the false acceptance rate increases as the number of templates increases because there is a small false acceptance probability for each template. To take advantage of this, vendors may base FAR estimates on databases with only a few templates.

In addition, vendors enroll users under ideal circumstances and have ideal situations for the access attempt. For instance, in face recognition, their test subjects might be very well lit and looking straight forward for both enrollment and access attempts—conditions that are not likely to occur in the real world. This can make a vendor’s reported false rejection rate lower than it would be in practice.

# FAILURE TO ENROLL

There is another type of error, failure to enroll (FTE). This occurs if the system will not enroll a user. For instance, in the case of fingerprint authentication, some people do not have well-defined fingerprints due to age, years of construction labor, lot of clerical paper handling, or other reasons. In some cases, this can make a fingerprint authentication system useless.

# Test Your Understanding

+   14. a. In biometrics, what is a match?
+      b. Distinguish between false acceptances and false rejections.
+      c. What are false acceptance rates (FARs) and false rejection rates (FRRs)?
+      d. For computer access, why is a false acceptance bad?
+      e. Why is a false rejection bad?
+      f. Which is worse from a security viewpoint?
+      g. Which is worse from a user acceptance viewpoint?
+   15. a. For watch lists of criminals, what is a false acceptance?
+      b. For watch lists of criminals, which is worse from a security viewpoint, a false acceptance or a false rejection? Explain.
+      c. For watch lists of people who should be allowed to enter a room, which is worse from a security viewpoint, a false acceptance or a false rejection? Explain.
+   16. What is failure to enroll?

# Verification, Identification, and Watch Lists

**VERIFICATION** Biometric authentication has one of three possible goals. In **verification**, a supplicant claims to be a particular person, and the challenge is to measure the supplicant’s biometric access data against the template of the person he or she claims to be. When you log into a server with a username and password, this is verification.

> In verification, the verifier determines whether the supplicant is a particular person.

Every time a match is attempted, there is a danger of a false match, meaning that the template data may match the applicant’s access data when there should not be a match. This danger usually is small, and because verification only matches the access data to a single template, there is only one chance of a false match.

To give an example, if the probability of a false acceptance is one in a thousand, then probability of a false acceptance is one in a thousand because only one match is attempted. There is a false acceptance rate (FAR) of 0.1 percent.