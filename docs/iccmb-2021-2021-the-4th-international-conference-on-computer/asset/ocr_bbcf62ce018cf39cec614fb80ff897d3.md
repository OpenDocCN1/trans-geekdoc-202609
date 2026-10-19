![](bbox=[0.15, 0.1, 0.85, 0.27])

# Figure 3: Flow Chart of Patient Upload Data

![](bbox=[0.15, 0.35, 0.85, 0.55])

# Figure 4: Flow Chart of Patient Data Access

in the chain of each node in the node group, consensus PBFT algorithm is used to analyse the types of deals, get confirmed, more than two-thirds of the consensus packaged such deals on a chain.

# 3.2 Data sharing process

The specific process:

+   (1) Take the data requester physician as an example, send the real identity to the central authorized agency CA, and obtain CID.Send CID to each attribute authorization agency AA to get the identity-related attribute set S and private key set SK.
+   (2) Doctors send access data requests to nodes in the consortium blockchain Fabric validation node cluster, which includes the doctor's CID, the name of the access data, and the owner.After receiving the access request, the node first verifies the identity of the doctor. After the authentication is passed, the class transaction is retrieved on the chain according to the name and owner of the accessed data. After the

corresponding class transaction is found, the relevant class transaction containing the requested content and the CID of the doctor are sent to the IPFS node group.

+   (3) The nodes in the IPFS node group first verify the identity of the doctor. After the verification is passed, the IPFS hash value corresponding to the access data is extracted from the class transaction. According to the hash value, the complete encrypted data of the patient is retrieved in the private IPFS network in the model.
+   (4) After receiving the patient's encrypted original medical data, the doctor decrypts the ciphertext by using its own attribute set S and the key related to the attribute. If the doctor's attribute value meets the access strategy set by the patient, the complete medical data of the patient will be successfully decrypted.Conversely, decryption fails.

# 4 EVALUATE

+   (1) Model efficiency: