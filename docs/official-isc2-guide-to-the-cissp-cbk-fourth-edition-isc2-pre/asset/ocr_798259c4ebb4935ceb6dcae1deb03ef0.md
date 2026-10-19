configuration changes to mobile devices.

Lastly, Appendix XX to the Guidelines lists the major controls from the NIST Special Publication 800-53, "Security and Privacy Controls for Federal Information Systems and Organizations, Revision 4" that are applicable to enterprise mobile device security, and Appendix C provides a list of mobile device security resources.46

![](bbox=[0.02, 0.2, 0.21, 0.35])

# TRY IT FOR YOURSELF

A sample template that will allow the security practitioner to review in detail what a mobile device usage policy may look like is provided as Appendix D. The 2 page template will walk you through the stages of a usage policy for a mythical company. Defining a usage policy documents clear responsibilities for all those involved with mobile device activities.

Download the template and go through the sections in order to understand how a mobile device policy is structured.

# Single Point of Failure (SPOF)

As technology such as virtualization makes technology more efficient and manageable, the security architect must also understand how single points of failure can arise. Using the example of virtualization, if one were to compare the before and after states from a point of failure perspective, it would seem virtualization often adds a single point of failure to many enterprises. Before virtualization, servers were typically individual hardware components all separate from one another. If the email server went down, it would rarely mean the network attached storage server would go down as well. If these systems were virtualized and ran on the same host, that host becomes a single point of failure for both systems. If the host goes down, all guests running on the host will go down as well. The security architect must identify single points of failure and determine alternatives so stakeholders can make informed decisions regarding the acceptance of the risk or mitigation strategies.

Just how does a security architect go about identifying single points of failure? How does the security architect determine what alternatives will be acceptable as mitigation