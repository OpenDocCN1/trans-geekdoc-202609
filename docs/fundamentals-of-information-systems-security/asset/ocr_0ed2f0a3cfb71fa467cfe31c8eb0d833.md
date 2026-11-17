Other models are based on the work of Biba, Clark-Wilson, and Bell-La Padula. These models describe the use of access controls and permissions to protect confidentiality or integrity.

# Discretionary Access Control

The Common Criteria define discretionary access control (DAC) as follows:

> [A] means of restricting access to objects based on the identity of subjects and/or groups to which they belong. The controls are discretionary in the sense that a subject with certain access permission is capable of passing that permission (perhaps indirectly) on to any other subject.

The Common Criteria also note the following:

> [S]ecurity policies defined for systems used to process classified or other sensitive information must include provisions for the enforcement of discretionary access control rules. That is, they must include a consistent set of rules for controlling and limiting access based on identified individuals who have been determined to have a need to know for the information.

These definitions apply equally to both public and private sector organizations processing sensitive information.

# Operating Systems-Based DAC

Operating systems have primary responsibility for controlling access to system resources such as files, memory, and applications. One of the main jobs for security administrators is to maintain access controls. Access controls are effective when they ensure that only authorized users can access resources. They are efficient when they ensure that users can access all the resources they need. Creating access controls that are both effective and efficient can be challenging. Organizations must decide how they will design and maintain access controls to best meet their needs. Here are a few points organizations must consider in developing access control policies:

+   - Access control method—Today’s operating systems contain access control settings for individual users (rule-based) or for groups of users (role-based). Which method you use depends on the size of the organization and the way specific access rights need to be for individuals or roles.
+   - New user registration—When new users are brought into an organization, their user accounts must be created. This can take a lot of time. It must be done quickly, however, so new people can do their jobs. User registration must be standardized, efficient, and accurate.
+   - Periodic review—Over time, users often get special permission to complete a particular project or perform some special task. These permissions need to be reviewed from time to time to make sure they stop when they are no longer needed. This review solves problems of compliance and auditing by making sure people can access only required areas.