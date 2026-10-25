+   - Third-Party Authentication: Third-party applications or cloud platforms’ integrity must be confirmed to ensure protection against malicious acts.

# 5.3.6 HUMAN LAYER

IoT security involves appropriately handling data by trained people, particularly in the healthcare domain. If the attacker exploits an IoT device successfully, device control is possible. This happens by gathering internal memory/firmware details and altering settings. The users of ehealth devices should refrain from using weak passwords, distributing keys physically or electronically, and purchasing health devices without proper authentication.

# 5.3.7 LIFE CYCLE CONTROL LAYER

This layer preserves and guarantees security from production to fitting/removal of devices. Primary characteristics are as follows [26]:

+   - Activity Monitoring: It is important for tracing, identifying, and detailing any malicious actions.
+   - Security Patches: Reliable fixing is required for IoT applications and devices to fight threats and analyze weaknesses.
+   - Safe Remote Control: Billions of IoT devices are preserved using this approach.

# 5.4 COLLABORATIVE, DISTRIBUTED, AND PRIVACY-PRESERVING ML: THE ROLE OF EFC

Researchers have focused on collaborative machine learning to address the challenges posed by the immense volume of data produced by IoT devices. Because of this, several users can train the ML model. This strategy does raise a few concerns concerning users’ privacy. The following is a synopsis of four approaches that have been developed to resolve concerns relating to ML and privacy [27,28].

# 5.4.1 FEDERATED LEARNING

A decentralized machine learning solution unites the computational capabilities of one principle server and several client servers. This strategy guarantees that all confidential information is present at the initial site during the learning process. The primary server will continue to function as an initial model for proxy data. A federated learning technique is depicted in Figure 5.6. In the initial model, local training is carried out using the client’s local data. This type of training involves the model being trained independently for many repetitions. Therefore, each provider obtains the model’s parameters from the primary server, trains the model using that provider’s data, and then sends the parameters it has computed back to the primary server. To construct one model from many client updates, the principal server is integrated with those client updates. At last, the upgraded model is distributed to all