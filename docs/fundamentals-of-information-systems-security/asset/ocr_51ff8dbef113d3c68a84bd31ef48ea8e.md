# Defeating Least Privilege, Separation of Duties, and Need to Know

**Least privilege** means granting the minimum access that allows a user to accomplish assigned tasks. Stated another way, it means to grant just enough authorization for users to do their jobs, but nothing else. Least privilege is difficult to maintain, but it does protect data from excessive authorization.

**Separation of duties** is the process of dividing a task into a series of unique activities performed by different people, each of whom is allowed to execute only one part of the overall task. This principle prevents people from both creating and approving their own work. Separation of duties can be a valuable tool to prevent fraud or errors by requiring the cooperation of another person to complete a task. Dual control is an example of separation of duties. Examples include a safe with two combination locks on the door or a missile-control system that requires the simultaneous turning of keys in consoles too far apart for one person to manage.

**Need to know** is the concept of preventing people from gaining access to information they don't need to carry out their duties. Providing access on the basis of need to know can reduce the chance of improper handling of data or the improper release of information.

Least privilege, separation of duties, and need to know can be defeated by the following:

+   - **Collusion.** Users work together (colluding) to avoid the controls, aggregate their authority, and assist each other in performing unauthorized tasks. Job rotation reduces the risk of collusion.
+   - **Covert channels.** These are hidden (covert) ways of passing information against organizational policy. There are two main types of covert channels: timing (signaling from one system to another) and storage (the storing of data in an unprotected or inappropriate place).

# Application-Based DAC

Application-based DAC denies access based on context or content. The application presents only options that are authorized for the current user. For example, an automatic teller machine (ATM) menu limits access by displaying only the options that are available to a particular user. You can apply security controls using these types of DACs based on user context or resource contents:

# FYI

The **Trusted Computer System Evaluation Criteria (TCSEC)** provides definitions of both DAC and MAC. These definitions fit the needs of public and private sector organizations that need to protect sensitive information. TCSEC was a prominent standard in the U.S. Department of Defense's Rainbow Series. The Rainbow Series was a collection of computer-security standards and guidelines published in the 1980s and 1990s. Each book in the series had a different-colored cover, which led to the nickname for each book. The TCSEC had an orange cover and is often called simply _The Orange Book_. The Common Criteria superseded _The Orange Book_ in 2005.