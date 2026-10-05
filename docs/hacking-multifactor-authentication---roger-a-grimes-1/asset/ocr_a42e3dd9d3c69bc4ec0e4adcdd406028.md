# 34 Hacking Multifactor Authentication

The authentication must have integrity, meaning that it accurately authenticates who or what should be successfully authenticated, and vice versa. The authentication secrets or factors used to authenticate a subject are kept secret by the authentication system and the subject. The authentication system should be resistant to malicious denial-of-service (DoS) attacks and be accessible with adequate performance to support its business function.

# Authentication Life Cycle

Authentication is the set of system and processes, starting with establishing proof of ownership or control of an identity, followed by giving the person some sort of resulting digital content (often known as a token or ticket), which the authenticated subject can present during future access control checks. In a good system, the process of authentication and authorization is monitored, and critical events are logged to a file for potential future collecting, auditing, and evaluation. As Figure 2.1 shows, authentication is just one process in a series of progressive, linked steps. The rest of this section will cover these steps in more detail.

![](bbox=[0.095, 0.445, 0.202, 0.91])

Figure 2.1: Basic authentication life cycle