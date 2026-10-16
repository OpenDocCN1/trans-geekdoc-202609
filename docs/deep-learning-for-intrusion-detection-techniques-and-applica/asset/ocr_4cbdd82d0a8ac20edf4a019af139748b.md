abnormal instances, identifying patterns of similarity or dissimilarity, often using sophisticated mathematical techniques. Achieving robust generalization is a core objective of DL systems.

DL approaches can be broadly divided into two main types: supervised and unsupervised learning [14].

+   • Supervised Deep Learning: Relies on a training dataset where data instances are labeled, typically by human experts, which can be time-consuming and expensive. In this context, a label may represent a class or category a data instance belongs to.

+   • Unsupervised Deep Learning: Seeks to discover hidden structures or groupings in data by evaluating the similarity between instances, without relying on pre-existing labels. It uses metrics to measure similarity or distance between data points.

+   • Semi-Supervised Deep Learning: Combines small amounts of labeled data with large amounts of unlabeled data, making it useful when labeling is limited. For instance, a model may have labeled data only for a “yes” class while needing to learn from both “yes” and “no” instances.

Based on how data is grouped, DL algorithms are further categorized into classification and clustering techniques.

Classification: Identifies the category or class a new data instance belongs to, based on learning from labeled examples. DL models designed for classification are known as classifiers, but not all supervised DL models are classifiers.

Clustering: Divides data into groups, or clusters, where items within a cluster are more similar to one another than to items in different clusters. This is an unsupervised learning technique.

These diverse techniques, when applied in DL systems, significantly improve intrusion detection and decision-making processes by automating the discovery of sophisticated attack patterns and anomalies in vast, dynamic datasets.

# 13.5 Vulnerabilities in Hardware and Software

Vulnerabilities are inherent weaknesses in the design, implementation, or management of networked systems that expose them to potential security threats. These vulnerabilities typically stem from one of three primary causes [27, 28]:

+   • Poor Design: Design flaws in hardware or software can compromise security. An example is the sendmail vulnerability in early UNIX versions, which allowed attackers to gain unauthorized privileged access to hosts.

+   • Poor Implementation: Misconfigurations often result from inexperience, inadequate training, or careless work. For instance, failing to set restricted access on critical executable files may allow unauthorized users to tamper with them.