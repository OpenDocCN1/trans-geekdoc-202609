
# Various research efforts on role hierarchies

Various research efforts on role hierarchies have been discussed in the literature. There is also a conference series called **SACMAT** (Symposium on Access Control Models and Technologies) that evolved from role-based access control research efforts. For example, how does access get propagated? Can one role subsume another? Consider the role hierarchy illustrated in [Figure 2.5](#ch02.xhtml#fig2_5a). This means if we grant access to a node in the hierarchy, does the access propagate upwards? That is, if a department manager has access to certain project information, does that access get propagated to the parent node, which is a director node? If a section leader has access to employee information in his/her section does the access propagate to the department manager who is the parent in the role hierarchy? What happens to the child nodes? That is, does access propagate downward? For example, if a department manager has access to certain information, then do his subordinates have access to that information? Are there cases where the subordinates have access to data that the department manager does not have? What happens if an employee has to report to two supervisors, one his department manager and the other his project manager? What happens when the department manager is working on a project and has to report to his project leader who also works for him?

![Figure 2.5 Role hierarchy.](images/fig2_5.jpg)

[Figure 2.5 Role hierarchy.](#ch02.xhtml#Ffig2_5)

Role-based access control has been examined for relational systems, object systems, distributed systems, and now some of the emerging technologies such as data warehouses, knowledge management systems, semantic web, e-commerce systems, and digital libraries. Furthermore, object models have been used to represent roles and activities (see, e.g., proceedings of the IFIP Database Security Conference series and more recently the Proceedings of the ACM Conference series on Data and Applications Security and Privacy).

## 2.2.1.3 Usage Control

More recently Sandhu et al. has developed yet another access control-like model and that is the Usage Control Model, which he refers to as **UCON** (see, e.g., the work reported in [[PARK2004](#ch02.xhtml#ref2_14)]). The **UCON** model attempts to incorporate some additional features into role-based access control including attribute mutability and obligations.

## 2.2.1.4 Attribute-based Access Control

Due to the fact that roles are not uniform across organizations, it was felt that role-based access control was not sufficient for web-based systems. Around the same time, web services and service-oriented architectures and cloud-based systems gained popularity and are now widely used. Therefore, an access control model based on claims was developed for such an environment. This model is attribute-based access control. Here, a user makes certain claims about him or her. These claims are then verified by the organization that wants to give the user access to the resources. If the user's claims are valid, then the policies are checked as to whether such a user has access to the resources. Attribute-based access control has become extremely popular in the last decade **[NIST](#ch02.xhtml#ref2_15)**.

## 2.2.2 Administration Policies

While access control policies specify access that specific users have to the data, administration policies specify who is to administer the data. Administration duties would include keeping the data current, making sure the metadata is updated whenever the data is updated, and ensuring recovery from failures and related activities.

Typically, the database administrator (**DBA**) is responsible for updating, say, the metadata, the index and access methods, and also ensuring that the access control rules are properly enforced. The System Security Officer (**SSO**) may also have a role. That is, the **DBA** and **SSO** may share the duties between them. The security-related issues might be the responsibility of the **SSO** while the data-related issues might be the responsibility of the **DBA**. Some other administration policies being considered include assigning caretakers. Usually owners have control of the data that they create and may manage the data for its duration. In some cases, owners may not be available to manage the data, in which case they may assign caretakers (i.e., custodians).

Administration policies get more complicated in distributed environments, especially in a web environment. For example, in web environments, there may be multiple parties involved in distributing documents including the owner, the publisher, and the users requesting the data. Who owns the data? Is it the owner or the publisher? Once the data has left the owner and arrived at the publisher, does the publisher take control of the data? There are many interesting questions that need to be answered as we migrate from a relational database environment to a distributed and perhaps a web environment. These also include managing copyright issues, data quality, data provenance, and governance. Many interesting papers have appeared in recent conferences on administration policies. [Figure 2.6](#ch02.xhtml#fig2_6a) illustrates various administration policies.

![Figure 2.6 Administration policies.](images/fig2_6.jpg)

[Figure 2.6 Administration policies.](#ch02.xhtml#Ffig2_6)

## 2.2.3 Identification and Authentication

For the sake of completion, we discuss identification and authentication as part of our discussion on discretionary security. By identification we mean users must identify themselves with their user ID and password. Authentication means the system must then match the user ID with the password to ensure that this is indeed the person he or she is purporting to be. A user may also have multiple identities depending on his/her roles. Identity management has received a lot of attention especially with the advent of web services (see [[BERT2006](#ch02.xhtml#ref2_5)]).

Numerous problems have been reported with the password-based scheme. One is that hackers can break into the system and get the passwords of users and then masquerade as the user. In a centralized system, the problems are not as complicated as in a distributed environment. Now, with the World Wide Web and e-commerce applications, financial organizations are losing billions of dollars when hackers masquerade as legitimate users.

More recently biometrics techniques are being applied for identification and authentication. These include face recognition, fingerprint recognition, and voice recognition techniques to authenticate the user. These techniques are showing a lot of promise and are already being used. We can expect widespread use of biometric techniques as face recognition technologies advance.

## 2.2.4 Auditing a Database System

Databases are audited for multiple purposes. For example, they may be audited to keep track of the number of queries posed, the number of updates made, the number of transactions executed, and the number of times the secondary storage is accessed so that the system can be designed more efficiently. Databases can also be audited for security purposes. For example, have any of the access control rules been bypassed by releasing information to the users? Has the inference problem occurred? Has privacy been violated? Have there been unauthorized intrusions?

Audits create a trail and the audit data may be stored in a database. This database may be mined to detect any abnormal patterns or behaviors. There has been a lot of work in using data mining for auditing and intrusion detection. Audit trail analysis is especially important these days with e-commerce transactions on the web. An organization should have the capability to conduct an analysis and determine problems like credit card fraud and identity theft.

## 2.2.5 Views for Security
