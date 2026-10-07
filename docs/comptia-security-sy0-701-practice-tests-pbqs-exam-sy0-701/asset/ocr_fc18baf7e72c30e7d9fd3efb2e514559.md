Option C is incorrect. Multi-factor authentication is essential for secure access but does not directly relate to high availability architecture.

Option D is incorrect. Having backups in various geographical locations is more relevant to disaster recovery than to high availability.

Question 242. After a recent service outage, a hospital’s IT team is reviewing the availability of its patient record system. They want to ensure the system remains operational, even in the event of hardware failures. Which of the following considerations is MOST relevant to this requirement?

+   (A) Implementing database mirroring
(B) Regularly updating the system’s antivirus definitions
(C) Using strong encryption for data at rest
(D) Conducting penetration testing on the system

Explanation 242. Correct Answer: A. Implementing database mirroring. Database mirroring is a solution for increasing the availability of a SQL Server database. Mirroring is implemented on a per-database basis and works only with databases that use the full recovery model. This ensures that in the event of a hardware failure, there’s a mirrored copy of the data available.

Option B is incorrect. While updating antivirus definitions is crucial for preventing malware infections, it is not directly