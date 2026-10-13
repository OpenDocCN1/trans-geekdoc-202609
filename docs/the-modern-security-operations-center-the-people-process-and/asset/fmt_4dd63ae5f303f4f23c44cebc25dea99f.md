
There are many other supplementary Apache components to Hadoop to provide value, such as `Hive` or `Pig` for data warehousing, `Flume` for data ingestion, and `ZooKeeper` for coordinating distributed applications. `Apache Kafka` and `Apache Spark` are options that can help Hadoop work faster by helping to accommodate real-time data since they can use in-memory data storage, which is a limitation of `MapReduce`. The open-source community surrounding Hadoop is huge and very supportive, enabling you to identify many use cases through research.

### Hadoop Challenges

One of the bigger challenges regarding using Hadoop that requires more work than what can be provided by a supplementary add-on is addressing security concerns. Hadoop has some security options, but they are fragmented because vendors and the open-source software community have had to retrofit security features into an Apache framework that wasn’t developed with security in mind. Big data is becoming a critical resource for many organizations, bringing it into the spotlight as a high-value target for cyberattack. To better understand the security challenges with big data, the Cloud Security Alliance (CSA) Big Data Security Working Group listed the following top ten security and privacy challenges to overcome in CSA’s 2012 publication “Top Ten Big Data Security and Privacy Challenges”:

1.  Secure computations in distributed programming frameworks
2.  Security best practices for non-relational data stores
3.  Secure data storage and transactions logs
4.  End-point input validation/filtering
5.  Real-time security/compliance monitoring
6.  Scalable and composable privacy-preserving data mining and analytics
7.  Cryptographically enforced access control and secure communication
8.  Granular access control
9.  Granular audits
10. Data provenance

Ajit Gaddam presented his whitepaper “Securing Your Big Data Environment” at Black Hat USA 2015 regarding recommendations to address the preceding list of concerns. Gaddam’s whitepaper proposes a Big Data Security Framework, shown in [Figure 5-23](#ch05.xhtml#ch05fig23). I find that many of these security recommendations fall in line with topics found in popular guidelines such as `NIST` and `ISO`.

![FIGURE 5-23 Big Data Security Framework](Images/05fig23.jpg)

**FIGURE 5-23** Big Data Security Framework

A summary of how this framework applies to securing Hadoop can be broken into five focus areas:

*   **Data management:** Addresses how big data is collected and identified to ensure the scope of what to protect is properly assessed and understood.
*   **Identity and access management:** Focuses on how to control who can access what aspects of the big data being collected by your organization. This focus area also includes validating that big data is coming from an authorized source, to avoid including modified or unwanted data.
*   **Data protection and privacy:** Protects what data is collected and ensures any privacy concerns are addressed.
*   **Network security:** Targets securing data as it is collected and moved between systems that are part of or leveraging the Hadoop infrastructure.
*   **Infrastructure security and integrity:** Addresses securing the Hadoop components within its framework.

### Securing Hadoop

Hadoop includes different security options such as `Kerberos`, encryption within `HDFS`, `HDFS` file permissions, perimeter security using `Apache Knox`, and authorization applications such as `Apache Ranger` to address data protection, network security, and infrastructure security concerns. I have covered many of these security topics in this book, and my recommendation is to leverage the Big Data Security Framework as a point of reference, similarly to using any popular guideline, as you address the concerns presented within this framework. To assess a current Hadoop setup, you can perform a capabilities assessment to ensure a defense-in-depth approach is included, which was covered in [Chapter 1](#ch01.xhtml#ch01).

Most modern `SIEM` solutions have configuration options for working with Hadoop or similar technology. As an example, `Splunk` uses a `Splunk Hadoop Connect` application to simplify the integration process between Hadoop and Splunk. With this app, Splunk can forward events to Hadoop for long-term archiving and additional batch analytics. A short summary of what `Splunk Hadoop Connect` offers is the ability to export, explore, and import big data. Hadoop collects and indexes massive streams of machine data in real time and allows Splunk to navigate and inspect `HDFS` directories from the `Splunk Hadoop Connect` user interface. The `Splunk Hadoop Connect` user interface can also import and index Hadoop data into Splunk, making that data available for searching, reporting, analysis, and visualization without the limitations of requiring `MapReduce` code. [Figure 5-24](#ch05.xhtml#ch05fig24) shows a diagram of the relationship between Splunk, Hadoop, and the `Splunk Hadoop Connect` application.

![FIGURE 5-24 Splunk, Hadoop, and Splunk Hadoop Connect App Diagram](Images/05fig24.jpg)

**FIGURE 5-24** Splunk, Hadoop, and Splunk Hadoop Connect App Diagram

#### Big Data Threat Feeds

Another common use case is the threat feeds that vendors provide to their security tools. For this use case example, you as the customer do not deal with managing how big data is being used. Instead, the vendor has its own infrastructure to collect big data for the purpose of generating actionable intelligence for the vendor’s products and customers. Looking back at the `Cisco Talos` example, the big data sources listed as resources for research translate into different types of intelligence that is funneled to Cisco products. As a research team, Talos is pulling huge amounts of data about real-time attack behavior; however, as a customer, you will only see the results of the Talos research, such as how an IP address is associated with malicious behavior. [Figure 5-25](#ch05.xhtml#ch05fig25) is an example of the result from this type of big data research displayed in `Cisco Umbrella`. [Figure 5-25](#ch05.xhtml#ch05fig25) shows a summary of why the `17ebook.com` website is malicious based on big data research performed by `Cisco Talos`, including how often the website is accessed, what occurs when systems access this website, who owns this website, if this website is associated with other malicious websites, and real-time updates regarding the risk associated with this website. `Cisco Talos` is the researchers that enable Cisco security tools such as `Cisco Umbrella`.

![FIGURE 5-25 Cisco Umbrella Big Data Results Example](Images/05fig25.jpg)

**FIGURE 5-25** Cisco Umbrella Big Data Results Example
