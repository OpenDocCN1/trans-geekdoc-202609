span of the subject requiring access. KryptoKnight by IBM and NetSP, an older KryptoKnight derivative, are also SSO technologies, but they are not widely deployed. Although you are unlikely to see these systems, you should know their names and that they are used for SSO as they might show up on the exam.

# # Authorization and Access Control Techniques

With a user identified and authenticated, the next step is authorization. What can a user who is logged in access, and what types of rights and privileges does that user have? At the core of this discussion is how subjects access objects and what they can do with these resources after access is established. There are five primary types of access control:

+   - Discretionary access control (DAC)
+   - Mandatory access control (MAC)
+   - Role-based access control (RBAC)
+   - Attribute-based access control (ABAC)
+   - Rule-based access control

These might not be concepts that you are used to thinking about; however, access control decisions are made early on in the design of an operating system. For example, early Microsoft Windows products had a peer-to-peer design; this is much different from SUSE Linux 15.0, which has a Kubernetes management platform.

The following sections look at the five types of access control in detail.

# # Discretionary Access Control (DAC)

With DAC, access control is left to the owner’s discretion. It is similar to a peer-to-peer computer network, where each user is left to control his or her own system and resources. The owner is authorized to determine whether other users have access to files and resources. One significant problem with DAC is that its effectiveness is limited by the user’s skill and ability. A user who is inexperienced or simply doesn’t care can easily grant full access to