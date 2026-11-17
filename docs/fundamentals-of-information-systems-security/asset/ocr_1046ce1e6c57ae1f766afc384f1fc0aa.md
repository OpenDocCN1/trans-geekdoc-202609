common ways to ensure LDAP messages are secure is to use **Secure LDAP**, or LDAP over SSL (LDAPS). This version of LDAP just uses SSL/TLS for all message exchanges across the network.

# # Policies and Procedures for Accountability

At this point, you have learned about how users are identified (step 1), authenticated (step 2), and authorized (step 3). Now it's time for the last part of the access control process: accountability. **Accountability** is tracing an action to a person or process to know who made the changes to the system or data. This is important for audits and investigations as well as for tracing errors and mistakes. Accountability answers the question, “Can you hold users responsible for what they do on the system?”

# ## Log Files

**Log files** are a key ingredient to accountability. Log files are records that detail who logged on to the system, when they logged on, and what information or resources they used. In the early days of computing, logs were used on systems that were shared by several users. It was necessary to charge users for their time using the systems, so logs tracked that data. Log files were also used by companies such as CompuServe and AOL when Internet use was charged by the hour. On today’s networks, most billing is either a fixed fee or based on bandwidth usage. Time-based billing has become uncommon. Logging now is used for more than just billing. It is also a valuable tool to detect, prevent, or monitor access to a system.

# ## Monitoring and Reviews

One of the main reasons to track user access activities is to detect questionable actions and respond to them. That means you should use software that monitors your activity logs and generates alerts when it finds suspicious activity. Continuous monitoring is an important part of a secure access control system. But not all suspicious activity is obvious. At times the only way to detect account policy violations is to review user actions over a period of time. Your account policy should include a requirement for periodic user account reviews. Such reviews help to validate that user access definitions are correct. They also help to find inappropriate activity or excessive permissions. Of course, every policy should outline steps to take to respond to any violations. Knowing how to respond to violations is just as important as finding them in the first place.

# ## Data Retention, Media Disposal, and Compliance Requirements

Many current laws require that organizations take measures to secure many types of data. The Health Insurance Portability and Accountability Act (HIPAA) is one example of legislation that requires data security. It protects the privacy of personal health data and gives patients certain rights to that information. Another example is the Fair and Accurate Credit