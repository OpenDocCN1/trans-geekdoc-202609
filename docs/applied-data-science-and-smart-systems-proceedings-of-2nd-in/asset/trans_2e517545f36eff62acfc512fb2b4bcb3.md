
| [Nandy et al., 2021](#ch24.xhtml#ref24_21) || DNA-based image encryption algorithm for secure transmission || Lack of transparency |

| [Tomek et al., 2021](#ch24.xhtml#ref24_35) || DNA-based data storage || Inadequate security measure |

| [Namasudra et al., 2020](#ch24.xhtml#ref24_23) || DNA-based encryption in the cloud computing environment || Long data retrieval time |

### Blockchain system with DNA-based encryption algorithms

In the application of DNA encryption algorithm with a blockchain system, some work has been done on this domain on different domains. For example, [Kaur et al. (2023](#ch24.xhtml#ref24_17)) proposed a blockchain-based system for securing and managing healthcare data generated on cloud networks through DNA cryptography. [Ramaiah et al. (2021](#ch24.xhtml#ref24_26)) and [Arya et al. (2021](#ch24.xhtml#ref24_34)) designed a blockchain-based criminal identification using a DNA encryption algorithm. [Table 24.3](#ch24.xhtml#tab24_3) analyses the application of DNA-based encryption algorithms with blockchain systems in different domains.

[Table 24.3 Analysis of blockchain system-based on DNA encryption algorithm.](#ch24.xhtml#R_tab24_3)

| Authors || Domain || Limitations |

| --- | --- | --- |

| [Kaur et al., 2023](#ch24.xhtml#ref24_17) || Healthcare || Low throughput |

| --- | --- | --- |

| [Ramaiah et al., 2021](#ch24.xhtml#ref24_26) ||  || Lack privacy |

| [Alshamrani et al., 2021](#ch24.xhtml#ref24_3) || IoT || Higher latency |

| [Liang et al., 2023](#ch24.xhtml#ref24_18) ||  || Inadequate security |

Based on the limitations of existing literature, this study will Integrate blockchain-based DNA encryption algorithms to address the challenges.

## Proposed solution

This part presents the proposed blockchain-DNA encryption algorithm to transform cybersecurity.

### Proposed algorithm

| **Proposed blockchain-based DNA encryption algorithm** |

| --- |

| 

1.  **Input: Digital data 2. Output: Blockchain-based DNA encryption**

2.  **Output: Blockchain-based DNA encryption 3. if (data is plain text), then**

3.  **if (data is plain text), then**

4.  **Generate hash**

5.  **Assign ASCII value**

6.  **Convert ASCII to binary number**

7.  **Insert the encryption method and create a DNS sequence 8. else**

8.  **else**

9.  **Return Cipher text**

10.  **end**

**Pseudo code for generating block hash**

1.  **if (new block = block_index) then**

2.  **Add block information, timestamp**

3.  **Generate block hash**

4.  **else**

5.  **Return Block**

6.  **end**

**Checking validation**

1.  **if (hash value= Valid), then**

2.  **Implement_blockchain and store**

3.  **else 4. Return to none**

4.  **Return to none**

5.  **end**

 |

The blockchain-based DNA encryption algorithm steps are described in the below steps.

***Step 1: Encoding digital data –*** Choose a method to map binary data (0s and 1s) to DNA bases (A, C, G, T). For example, you might use A for 00, C for 01, G for 10, and T for 11.

Split the digital data into chunks corresponding to the length of DNA fragments (oligonucleotides).

***Step 2: Error correction –*** Implement correction mechanisms for possible errors introduced during DNA synthesis and sequencing. Techniques like forward error correction codes can be used.

***Step 3: Encrypting the DNA data –*** Apply a cryptographic encryption algorithm to the DNA-encoded data to enhance security. This step can involve traditional encryption methods such as AES or specialized DNA-based encryption techniques.

***Step 4: Generating keys –*** If applicable, generate cryptographic keys for encryption and decryption. These keys could be encoded into DNA sequences as well.

***Step 5: Storing on the blockchain –*** Use a blockchain platform to store the encrypted DNA data securely. This might involve creating transactions with associated metadata and storing the DNA sequences on the blockchain.

***Step 6: Access control and decryption –*** Using smart contracts, develop a mechanism to control that can access and decrypt the DNA-encoded data. Access control keys might be required for decryption.

***Step 7: Decoding and Decryption –*** Retrieve the encrypted DNA sequences from the blockchain. Decrypt the DNA-encoded data using the decryption keys and the reverse process of the encryption algorithm. Convert the DNA bases back into binary data.

***Step 8: Error detection and correction –*** Apply error detection and correction mechanisms to ensure the accuracy of the decrypted data.

***Step 9: Verification –*** Verify the accuracy of the decrypted data against the original digital data to ensure successful decryption.

## Challenges of integrating DNA encryption in blockchain system

Integrating blockchain technology with DNA encryption presents a unique set of challenges due to both domains’ complexity and specialization. Some key challenges include ([Akgün et al., 2015](#ch24.xhtml#ref24_4); [Hazra et al., 2018](#ch24.xhtml#ref24_14); [Hao et al., 2021](#ch24.xhtml#ref24_13)).

1.  ***Data size and efficiency:*** DNA-encoded data can be significantly larger than traditional digital data. Storing large amounts of DNA data on a blockchain could strain the network’s storage and processing capabilities, leading to slower transaction speeds and increased costs.

2.  ***Regulatory and ethical concerns:*** Using DNA for encryption and storage raises ethical and regulatory questions regarding the use of genetic material. Privacy, consent, and ownership issues must be addressed to ensure that DNA and blockchain technology integration respects legal and ethical boundaries.

3.  ***Interoperability and adoption:*** Integrating DNA encryption algorithms and blockchain technology requires interoperability with existing systems and standards. Adoption challenges may arise if the integration process is not seamless or if existing infrastructure needs substantial modifications to accommodate DNA-encoded data.

4.  ***Computational resources and costs****:* DNA encoding/decoding and blockchain processing require substantial computational resources. The cost of performing these operations, especially at scale, could be prohibitive and limit the practicality of the integration.

5.  ***Transaction speed and scalability:*** Blockchains already face transaction speed and scalability challenges. Integrating complex DNA encryption processes could further slow transaction processing, making real-time applications impractical. Achieving high throughput while ensuring secure DNA encryption is a technical hurdle.

6.  ***DNA encoding and decoding:*** Encoding digital data into DNA sequences and decoding it back into a usable format requires specialized algorithms and biotechnology processes. Integrating these processes with blockchain’s distributed architecture and consensus mechanisms could be complex and require significant algorithmic in-novation.

## Case studies and analysis

This area presents the case studies on the application of blockchain with DNA encryption for enhanced security and comparative analysis of existing blockchain-based DNA-based systems and the proposed solution.

### Case studies

[Table 24.4](#ch24.xhtml#tab24_4) lists case studies on integrating blockchain systems with DNA encryption algorithms.

[Table 24.4 Case Studies on the integration of blockchain system with DNA based encryption algorithm.](#ch24.xhtml#R_tab24_4)

| Authors || Case study || Description |

| --- | --- | --- |

| [Chernomoretz et al., 2020](#ch24.xhtml#ref24_7) || DNA-based forensic and legal applications using blockchain || Blockchain was used to store DNA evidence, maintaining its integrity and provenance securely. DNA encryption further protects sensitive genetic information, ensuring only authorized parties can access the evidence |
