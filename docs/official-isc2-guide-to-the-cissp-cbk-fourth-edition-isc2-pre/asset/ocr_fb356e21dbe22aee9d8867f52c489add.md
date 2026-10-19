applications, and so true verification of the user’s legitimacy is lacking. An unauthorized individual, such as a contractor or support person, accessing the organization’s intranet can access the OIUA systems just as easily as a regular employee can. For some organizations, and depending on the type of systems affected by this model, that may not be a concern. Nevertheless, the security professional would be wise to thoroughly check the information contained in each participating system and the type of organizational resources those systems allow users to access before approving the use of an OIUA model. If the model serves a legitimate business purpose, the participating systems should be strongly isolated from the OIUA systems (logically and physically) before proceeding to offer this service to users.

# Single/Multi-Factor Authentication

An authentication factor can be one of three types:

+   - **Something You Know** – A password or PIN
+   - **Something You Have** – A token or smart card
+   - **Something You Are** – Biometrics, such as a fingerprint

Single factor authentication involves the use of simply one of the three available factors solely in order to carry out the authentication process being requested. The subjects that want to be authenticated will have to provide their factor; in other words, they will have to present their password, or swipe their smart card, or scan their finger in order to validate their identity and authenticate into the system.

Multi-factor authentication ensures that a user is who he or she claims to be. The more factors used to determine a person’s identity, the greater the trust of authenticity. Multi-factor authentication can be achieved using a combination of factors. Typically any combination of at least two factors is referred to as multi-factor authentication, although the most secure systems will require the use all three factors for a true multi-factor solution. One type of authentication may not be repeated in attempting to satisfy multi-factor authentication. For example, authenticating using two passwords does not constitute multi-factor. They are both part of “something you know” and can both only satisfy this category.

One example of how multi-factor authentication is being used in the enterprise today can be seen by examining what the Amazon Web Services (AWS) platform has architected for their customer facing solution. According to Amazon, AWS Multi-Factor Authentication (MFA) is a simple best practice that adds an extra layer of protection on