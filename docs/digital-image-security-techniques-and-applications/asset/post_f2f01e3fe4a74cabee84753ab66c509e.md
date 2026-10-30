
![](img/6e4271af21d9a195003ab8711aa79d27_333_0.png)

Figure 15.2 Common causes of data breaches.

reasons why data breaches happen. The following section discusses several security techniques that have been used in IoMT based on their effectiveness.

## 15.1.2 Security measures of medical data

Extensive research and development efforts have been dedicated to designing and studying various traditional and modern AI schemes with the objective of ensuring sensitive data security. In the context of health care organizations, several traditional security measures can be employed to safeguard sensitive data. These measures include:

- **Access Control:** Access control mechanisms limit access to medical data to authorized personnel only. This can be done by implementing role-based access control, where users are assigned access privileges based on their job responsibilities.
- **Authentication:** Authentication mechanisms such as passwords, biometrics, or smart cards can be used to ensure that only authorized personnel are accessing the medical data.
- **Encryption:** Encryption is the process of converting data into a code or cipher to prevent unauthorized access. Medical data can be encrypted when stored, transferred, or accessed, making it difficult for unauthorized users to understand.
- **Information Hiding:** Information hiding techniques are used to protect secret data inside the cover image or video. It also provides content authentication, data ownership verification, and copyright protection. Watermarking and steganography also come under this scheme.

- **Backup and Recovery:** Regular backups of medical data can help in ensuring that sensitive data is not lost due to accidental deletion, system failures, or other disasters. The backup data can be used to restore lost or damaged data in case of a security breach or other incidents.

- **Employee Training:** Regular training and awareness programs can help employees understand the importance of medical data security and their role in protecting it. They can also learn about security policies and best practices.

- **Physical Security Measures:** Implementing physical security measures, such as access controls, surveillance systems, and secure storage facilities, can protect physical infrastructure and prevent unauthorized access to sensitive data.

These traditional security measures, when implemented effectively, can help health care organizations protect medical data from unauthorized access, data breaches, and other security threats. However, as technology advances, new security measures may need to be implemented to keep up with evolving threats. Additionally, AI solutions are in high demand in almost every area. Here are some AI-based solutions that can be used to preserve medical data privacy:

- **Intrusion Detection Systems (IDS):** IDS [15] is an AI solution that detects and responds to cyberattacks. It uses machine learning algorithms to analyze network traffic and identify abnormal activity that may indicate an attack.

- **Malware Detection:** AI-based malware detection systems [16] can identify malicious software and prevent it from infecting systems. These systems use machine learning algorithms to analyze patterns in code and behavior to identify malicious software [14].

- **User Behavior Analytics:** It uses AI to identify abnormal user behavior that may indicate a security threat. For example, it can detect when a user logs in from an unusual location or attempts to access sensitive data outside of their normal working hours.

- **Data Loss Prevention:** These systems use AI to monitor data usage and prevent sensitive data from being accessed or transmitted to unauthorized parties. These systems can identify patterns in data usage and flag any unusual activity that may indicate a data breach.

- **Access Control:** AI can be used to manage access to medical data by implementing intelligent access control policies. This can involve analyzing user behavior to detect anomalies and flag suspicious activity.

- **Differential Privacy:** AI can be used to implement differential privacy, which adds noise to the data to protect individual privacy while allowing for useful insights to be derived. Differential privacy is a mathematical framework that ensures an individual’s data is protected even when combined with other data sets. Recent work [1] has presented secure medical data classification by employing differential privacy in an AI-based classification model.

- **Homomorphic Encryption:** AI can be used to implement homomorphic encryption, which allows data to be encrypted while still being processed. This allows for sensitive medical data to be securely analyzed without the need to decrypt it first.

- **Data Masking:** AI can be used to mask sensitive data in medical records, such as names and addresses, while still allowing for other useful information to be analyzed. This can be done through techniques such as tokenization or hashing.

- **Natural Language Processing (NLP):** AI can be used to develop NLP models that can scan medical documents for sensitive information such as patient names or addresses and redact or remove such information automatically.

- **Federated Learning:** Federated learning is another paradigm that allows multiple clients to train AI models securely without sharing sensitive data with other participants [2, 17].

- **Advanced AI Models:** Instead of sharing original data for model training, artificial data can be created and translated from one medical domain to another by cyclic GAN and can be further utilized for knowledge distillation purposes [18].

- **Optimal Key Generation for Data Encryption:** By utilizing CI with appropriate objective functions, random and optimal keys can be generated, which are less vulnerable to attackers due to the high search space of the key. It can be utilized for encryption purposes. They can be further extended to information hiding.

Overall, AI can be an effective tool to preserve medical data privacy. However, it is important to ensure that AI systems are secure and are implemented in accordance with privacy regulations and best practices to prevent the misuse of sensitive data.

## 15.2 OVERVIEW OF CI

CI is a dynamic field encompassing the theory, design, development, and application of computational paradigms inspired by biological and linguistic processes. Neural Networks [19], Fuzzy systems [20], and EC [6] have traditionally been considered the three primary pillars of CI. These paradigms are designed to emulate the behavior of natural intelligence and provide powerful tools for solving complex problems in a wide range of domains, including machine learning, robotics, data analytics, and optimization. By harnessing the power of CI, researchers and practitioners can develop novel algorithms and models that can learn, adapt, and evolve in response to changing environments and data inputs, leading to new insights and discoveries that can benefit society as a whole. Among all these, our primary focus is on EC.

### 15.2.1 Evolutionary computation

EC is an exciting subfield of AI that draws inspiration from biological evolution and natural events performed by organisms. By modeling the principles of evolution, EC methods aim to solve complex optimization problems efficiently. The primary goal of EC is to create novel computing methods that mimic natural intelligence discovered in physical, chemical, and biological systems. Unlike other optimization techniques, EC methods have been proven effective as a global optimization method for multiple problems. EC methods are population-based approaches that generate a random initial population and utilize variation operators, such as mutation and crossover, to create the next population or offspring. The natural selection process is then used to refine the population for the next generation. By following these steps, EC methods mimic the process of natural selection to create increasingly better solutions to the optimization problem at hand.

EC has a rich history dating back to the 1960s when researchers proposed Genetic Algorithms (GA), Genetic Programming (GP), and Evolution Strategies (ES) to solve global optimization problems [21]. Since then, other methods such as Differential Evolution and Estimation of Distribution Algorithms have been developed, all falling under the umbrella of evolutionary algorithms. In the 1990s, researchers also explored the simulation of natural intelligent phenomena of ants and swarms to create optimization methods, giving rise to the field of Swarm Intelligence [22]. GDWCNPSO [3], QL-SSA [7], MDO [23], and Golden Jackal optimization [24] are a few recent developments in this category. These methods are all subclasses of EC [25] and have greatly expanded the scope of EC. EC algorithms are particularly well-suited to non-convex and black-box optimization problems where the mathematical form of the objective function is not known. The mutation and crossover operations are based on guided randomness, and the method, as a whole, typically does not require any gradient knowledge about the objective function being optimized. Their derivative-free nature makes them a popular choice for solving challenging problems. Due to the versatility of EC methods, they have become the center of attention in the optimization field and have led to numerous innovations. These techniques are also effective for solving multi- and many-objective optimization issues. A broad overview of these intelligent optimization methods is presented in Figure 15.3. Further, different subclasses are shown in Figure 15.4.

Overall, EC is an innovative approach to solving complex optimization problems that draws inspiration from biological evolution. Its population-based characteristics and natural selection processes make it a powerful tool for creating efficient algorithms that can adapt to changing environments. With ongoing research and development, the potential for EC to solve increasingly complex problems continues to expand.
