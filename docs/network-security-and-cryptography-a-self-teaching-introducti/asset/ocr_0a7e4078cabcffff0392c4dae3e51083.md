occurrences over an interval of time, and if the count exceeds the threshold then an intrusion is assumed.

+   - Profile-Based Detection: This technique is based on developing the activity profile of each legitimate user. The intrusion detection is performed on the basis of "sudden and significant change in the behavior" of a user.

Rule-Based Detection: This involves defining a set of rules that can be used to decide whether a given behavior is that of a legitimate user or of an intruder. It has two approaches:

+   - Anomaly Detection: It attempts to detect deviations from the previous established usage pattern.

+   - Penetration Identification: It refers to use of an expert system to detect suspicious users.

# 13.4 PASSWORD MANAGEMENT

A password is the biggest defense against intruders. Each user in a multi-user environment will be assigned a User ID and a Password. A user can change the password anytime. A fundamental principle of Password Management is that it should be known only to its owner. When a user changes a password, the password is transformed using a one-way function, and the transformed value is only saved in the system along with the corresponding User ID. Whenever a user enters passwords to gain access into the system, the password entered by the user is transformed using the same one-way function, and the transformed value is compared with the one saved in the system. If both values match, the user authentication is considered to be verified.

# 13.5 MALICIOUS PROGRAMS

These are malicious programs used by intruders to attack system security. There are two classes of these programs: