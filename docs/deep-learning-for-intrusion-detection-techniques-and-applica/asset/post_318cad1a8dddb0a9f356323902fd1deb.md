
## Table 6.3 Content features within a connection suggested by domain knowledge.

| Feature name | Description | Type |
|--------------|-------------|------|
| hot | Number of hot indicators | Continuous |
| num_failed_logins | Number of failed login attempts | Continuous |
| Logged_in | 1 if successfully logged in; 0 otherwise | Discrete |
| Num_compromised | Number of compromised conditions | Continuous |
| Root_shell | 1 if root shell is obtained; 0 otherwise | Discrete |
| Su_attempted | 1 if su root command attempted; 0 otherwise | Discrete |
| num_root | Number of root accesses | Continuous |
| num_file_creations | Number of file creation operations | Continuous |
| num_shells | Number of shell prompts | Continuous |
| num_access_files | Number of operations on access control files | Continuous |
| num_outbound_cmds | Number of outbound commands in an ftp session | Continuous |
| Is_hot_login | 1 if the login belongs to the hot list; 0 otherwise | Discrete |
| Is_guest_login | 1 if the login is a guest login; 0 otherwise | Discrete |

## Table 6.4 Traffic features computed using a two-second time window.

| Feature name | Description | Type |
|--------------|-------------|------|
| Count | Number of connections to the same host as the current connection in the past two seconds | Continuous |

Note: The following features refer to these same host connection

| Feature name | Description | Type |
|--------------|-------------|------|
| serror_rate | % of connections that have SYN errors | Continuous |
| rerror_rate | % of connections that have REJ errors | Continuous |
| same_srv_rate | % of connections to the same services | Continuous |
| diff_srv_rate | % of connections to different services | Continuous |
| srv_count | Number of connections to the same service as the current connection in the past two seconds | Continuous |

Note: The following features refer to these same-service connections

| Feature name | Description | Type |
|--------------|-------------|------|
| srv_serror_rate | % of connections that have SYN errors | Continuous |
| srv_rerror_rate | % of connections that have REJ errors | Continuous |
| srv_diff_host_rate | % of connections to different hosts | Continuous |

## 6 Dataset for Evaluating Deep Learning-Based Intrusion Detection

The NSL-KDD detection dataset is much smaller in comparison to the full KDDCup99 dataset, despite being widely used, had several flaws, including a high number of duplicated records (approximately 78% in the training set and 75% in the test set), which caused ML models to become biased toward frequent attack types and prevented them from effectively learning rare but critical attacks such as R2L and U2R intrusions. Additionally, KDD99 had an unbalanced distribution of attack types, where some attacks dominated the dataset, making it less suitable for realistic intrusion detection research. To address these issues, NSL-KDD was introduced as a refined dataset that removes duplicate records, balances the attack categories, and provides a better evaluation framework for IDS models [15, 16].

The NSL-KDD dataset retains the same 41 network traffic features used in KDD99 but ensures a more balanced attack representation to avoid learning bias. These features are divided into three main categories: basic features (such as protocol type, service, and duration), content-based features (such as the number of failed login attempts and root access requests), and traffic-based features, which analyze network behavior over time to detect anomalies. The dataset is structured into a training set (KDDTrain+) with 125,973 instances and a testing set (KDDTest+) with 22,544 instances, along with an additional challenge test set (KDDTest-21) containing 11,850 instances. NSL-KDD includes four main categories of attacks: DoS, which floods systems to exhaust resources (e.g., Smurf, Neptune, Teardrop); U2R, where attackers gain administrative access (e.g., Rootkit, Buffer Overflow); R2L, where unauthorized access is obtained remotely (e.g., Guess_Password, Warezclient); and probing (Reconnaissance), which involves scanning networks for vulnerabilities (e.g., Satan, Nmap, Portsweep) [17, 18]. In total, the dataset contains 39 attack types.

One of the significant advantages of the NSL-KDD is its cleaner and more realistic dataset structure. Removing redundant records ensures that IDS models do not become biased toward common attack types, allowing them to generalize better to different forms of attacks. Additionally, the dataset contains a more balanced selection of difficult and easy attack records, making it challenging enough for ML models to improve their detection accuracy without being overly simplified. The reduction in dataset size compared to KDD99 also makes it computationally efficient, enabling researchers to train and test models more effectively without requiring massive processing power [19].

Despite these improvements, NSL-KDD still has some limitations. It does not include modern cyber threats such as ransomware, advanced persistent threats (APTs), or encrypted traffic-based attacks, which are crucial for evaluating today's IDS models. Additionally, because it is still based on a simulated dataset, it lacks the full complexity and diversity of real-world network traffic, meaning that models trained on NSL-KDD may not always perform well in real-life scenarios.

Furthermore, encrypted network traffic and sophisticated obfuscation techniques are not represented in the dataset, making it unsuitable for testing IDSs that focus on modern encrypted communication protocols such as SSL/TLS and VPN traffic monitoring.

In conclusion, NSL-KDD remains a widely used and improved alternative to KDD99, offering a more balanced, efficient, and effective dataset for evaluating intrusion detection systems. While it addresses several shortcomings of KDD99, its lack of modern attack scenarios and real-world network diversity limits its effectiveness in contemporary cybersecurity research.

### 6.4.4 ISCX-2012

The ISCX 2012 [20] intrusion detection evaluation dataset was developed by the Information Security Centre of Excellence (ISCX) at the University of New Brunswick (UNB) to address limitations in existing network security datasets. Many earlier datasets, such as DARPA 1998, KDD 1999, etc., were criticized for being outdated, unrealistic, or heavily anonymized, making them less effective for modern intrusion detection research. To overcome these issues, ISCX 2012 was designed using a systematic dataset generation approach that ensures realistic, diverse, and labeled network traffic, making it highly suitable for ML and IDS research.

The dataset consists of both normal and malicious traffic, covering various network protocols, including HTTP, SMTP, SSH, IMAP, POP3, and FTP. It was collected over seven days (June 11–18, 2012) in a controlled testbed environment with 21 interconnected Windows workstations. Unlike many previous datasets, ISCX 2012 provides full packet captures (PCAP files) as well as preprocessed CSV files with labeled features. The dataset was designed to ensure total interaction capture, meaning that all network activities, including packet payloads, were recorded without anonymization, providing a more detailed and realistic dataset for cybersecurity research.

A unique feature of ISCX 2012 is its profile-based traffic generation methodology. Instead of relying on synthetic attack insertions post-capture, the dataset was created by simulating real-world user and attack behaviors. Normal network traffic was carefully modeled based on real user activities, while attack traffic was executed in real time using various cybersecurity tools. This approach resulted in a dataset that closely resembles real-world attack scenarios.

The dataset includes different types of attacks, such as Brute Force SSH, DDoS, SQL Injection, HTTP DoS (Slowloris), and Infiltration Attacks. For instance, the Brute Force SSH attack involved repeated login attempts to break into an SSH server, while the DDoS attack was executed using an IRC botnet to flood the target with HTTP requests. Similarly, the SQL Injection attack exploited vulnerabilities
