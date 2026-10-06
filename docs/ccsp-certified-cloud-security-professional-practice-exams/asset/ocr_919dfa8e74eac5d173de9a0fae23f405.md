represents the last hop before leaving the application for external use, and would be the appropriate place to have a DLP implementation.

+   * A is incorrect because the server originating the traffic represents a first hop of network transmission, and the data may pass through other systems and network devices before leaving for external use. It would not be the optimal place for a DLP implementation.

+   * C is incorrect because firewalls and other network-monitoring solutions are between VLANs, which by nature are internal to a network and do not represent when data leaves for external use.

+   * D is incorrect because the server receiving the data would be a client where data in use becomes the appropriate stage; it is no longer data in transit once it reaches its destination.

# 9. Which of the following types of solutions is often used for regulatory compliance reporting?

+   A. SIEM

+   B. DLP

+   C. IRM

+   D. IDS

+   * A. A security information and event management (SIEM) solution is used to collect, aggregate, and process data throughout an application or even an entire infrastructure. It is often used to produce auditing and compliance reports based on the data that is collected and aggregated, and most SIEM solutions have very robust reporting, alerting, and dashboard capabilities.

+   * B is incorrect because data loss prevention (DLP) solution is used to protect sensitive information and how it is processed, handled, and disseminated. It is not used for reporting.

+   * C is incorrect because rights management (IRM) solutions are used to control how information is accessed and used, and is not a reporting tool or solution.

+   * D is incorrect because an intrusion detection system (IDS) is used to monitor data transmissions against known signatures and patterns, and to alert application owners or developers about anomalies or suspicious circumstances. It is not used for regulatory or compliance reporting.

# 10. Encryption solutions can be embedded within database operations that will serve to protect data in a manner that is not noticeable to the user. What kind of encryption strategy is this?

+   A. Transparent

+   B. Passive

+   C. RSA

+   D. Homomorphic