+   On the File to Import page, type the path to the appropriate certificate files (for example, \bf1\$bf1.cer), and then click Next.

+   8. On the Certificate Store page, click “Place all certificates in the following store,” and then click Next.

+   9. On the Completing the Certificate Import Wizard page, verify that the information you accurate, and then click Finish.

+   10. You can repeat the same steps to add additional certificates for each of the federation servers that live in the federation server farm.

# The Bottom Line

**Install the AD FS role on a server.** Installing the AD FS role on a server is one of the first steps in implementing an AD FS infrastructure. Windows Server 2012 R2 made it easier than ever to install and use AD FS AD FS provides you with single sign-on access within your corporate network, to a partner organization, and to websites and applications hosted on the Internet.

**Master It** How do you install AD FS on a server?

**Configure the first federation server in a server farm.** A federation server serves as part of a federation service that can issue, manage, and validate requests for security tokens and identity management. Multiple federation servers provide much-needed functionality like high availability and network load balancing in a large AD FS infrastructure. For proper SSO user access between your organization and a partner organization, federation servers must be deployed in the partner's organization as well as your own.

**Master It** How do you create the first federation server in a federation services farm?

**Configure AD FS performance monitoring.** AD FS includes its own dedicated counters to help you monitor the performance of both federation servers and federation server proxy machines. This is a nice little addition that helps you manage AD FS more easily. Generated reports provide AD FS-specific details that show how well it is running in the environment. Monitoring performance is an essential part of planning for growth and scalability. High utilization could mean that you need to deploy another federation server to balance the load more proficiently.

Master It How would you monitor the performance of your AD FS infrastructure?