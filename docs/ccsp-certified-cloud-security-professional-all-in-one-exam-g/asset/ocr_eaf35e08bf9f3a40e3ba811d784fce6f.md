# CCSP Certified Cloud Security Professional All-in-One Exam Guide

78

# Figure 3-1
The data lifecycle

![](bbox=[0.463, 0.096, 0.725, 0.29])

# Create

Although any initial phase is called “Create,” it can also be thought of as modification. In essence, any time data is considered “new,” it is in the Create phase. This data that is newly created, data that is imported into a system and new to that system, or data that is already present and modified into a new form or value. It is also the most appropriate time to determine the data classified as secure. When data is created, its value and sensitivity are known and can be handled properly from the onset, as all additional phases build off this phase. It is also the most appropriate to deal with data modification. The classification of data after modification should always be done as a new process, taking into account the state of the data after modification, because the level of sensitivity may very well have changed during the modification process. Decisions made during the creation process as far as classification will impact all additional phases, beginning immediately with how the data is stored and protected. Security controls should be initially implemented at the Create phase as well, specifically in the form of technologies such as SSL/TLS with data that is imported or imputed.

# Store

Immediately after the data is created, it must be stored in a way that is usable to the system or application (in many cases, this is an almost simultaneous and complementary process). Data can be stored in numerous ways. Storage methods include files on a file system, remote object storage in a cloud, and data written to a database. Storage of data must be done in accordance with the data classification determined during the Create phase. The Store phase is the first place where security controls can be implemented to protect the data at rest, and the Cloud Security Professional must ensure that all storage methods employ whatever technologies are necessary for its data classification level, including the use of access controls, encryption, and auditing. The use of appropriate redundancy and backup methods also comes into play immediately at the Store phase to protect the data on top of the security controls.