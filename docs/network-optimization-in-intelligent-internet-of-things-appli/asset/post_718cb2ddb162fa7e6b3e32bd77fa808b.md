
# Lightweight Cryptography Algorithms in IoT

205

![](img/e0b54a8aa3102369506fc5feb80a6fde_221_0.png)

**FIGURE 11.2** Classification of lightweight cryptographic schemes.

achieved using asymmetric AES. The lightweight encryption schemes based on hash and bit-wise XOR operation are used for IoT devices. Lightweight cryptography is divided into three major categories: lightweight cryptography; hash functions; and lightweight integrity schemes. The main task of lightweight schemes is to set up an adequate control mechanism for data privacy that must consider the data collection, data transmission, and storage. The classification for these schemes is represented in Figure 11.2.

## 11.6.1 LIGHTWEIGHT CRYPTOGRAPHY

The substitution-permutation network-based PRESENT [27] uses a 64-bit block based on 80-bit and 128-bit keys. However, this algorithm is hardware efficient and uses 4-S boxes, which it takes large cycles in the block. Therefore, an upgraded version is required of this algorithm. Another work on security challenges and lightweight cryptography was discussed by Thakor et al. [28]. The authors discussed that while collecting data from the physical environment, they become an attractive target for many authors. They emphasize that conventional cryptography is not acceptable for resource-constrained devices. Therefore, the authors discussed lightweight cryptography algorithms based on block cipher as (a) substitution-permutation network work, (b) Generalized Feistel Network (GFN), (c) nonlinear feedback feedback shift register (NLFSR), and (d) hybrid cipher. Reddy et al. [29] proposed a lightweight cryptographic scheme. Their protocol provides resistance against replay attacks, clock synchronization problems, smart card stolen attacks, insider attacks, and user impersonation attacks.

206 Network Optimization in Intelligent IoT Applications

## 11.6.2 LIGHTWEIGHT HASH FUNCTION

These cryptographic hash functions generate the fixed representation of the message. These hash functions are based on one-way hash function and collision resistance. The one-way hash function is defined as, H(m) is known by the adversary. It should be impossible to extract the message 'm'. The collision resistance ensures H(m) != H(m'). The secure messages digest and secure hash functions are used in a variety of applications as message authentication, intruder detection, and digital signature. SHA3 has fixed-length hash algorithms SHA3-224, SHA3-256, SHA3-384, and SHA3-512 [30]. NIST has recommended SPONGENT, PHOTON, QUARK, and Lesamnta-LW hash schemes. These hash functions are popular due to their capability to produce much smaller memory footprints.

## 11.6.3 LIGHTWEIGHT INTEGRITY SCHEMES

Miller in 1985 defined the hard cryptographic algorithm as ECC. ECC is considered a more suitable solution in comparison with RSA as it requires a small key size. Smart homes contain smart devices as smart meters, smart doors, bulbs, and smart electricity systems. Any unauthorized users can take control of these systems and access data. Cryptographic approaches such as symmetric and asymmetric are used to maintain the integrity of network communication. Therefore, Kaur and Kumar [32] provide a two-parameter based authentication method to secure user data. Their protocol is based on the ECC scheme. ECC is the most popular choice to ensure the integrity of IoT data. Recent approaches such as Software Defined Networks (SDN) and blockchain are also utilized to maintain integrity.

## 11.7 LIGHTWEIGHT AUTHENTICATION SCHEMES FOR IOT

### 11.7.1 Two-Factor AUTHENTICATION SCHEMES

Authenticating user before joining the network is proposed by Yeh et al. [33]. The authors efficiently utilize the ECC-based schemes for secure communication. Additionally

223 Lightweight Cryptography Algorithms in IoT

### 11.7.2 THREE-FACTOR AUTHENTICATION SCHEMES

For resource-constrained IoT communication, three parameters are used to ensure secure communication. The ECC-based scheme, which provides key agreement and user authentication, is proposed by the author [37] based on lightweight computation. The information must remain confidential when transferring to the legitimate user. Therefore, the authors proposed a protocol for securing multimedia information and preserving the data from external attacks [25]. The BAN logic is used to evaluate the security goal of the proposed protocol. The significant growth in IoT communication is due to the WSN; the nodes are spread in unattended areas to provide real-time information. This issue has been addressed by authors [38] using the MAC function. The results are analyzed and proved mathematically using BAN logic and the Random Oracle Model (ROM).

## 11.7.3 MULTI-FACTOR AUTHENTICATION SCHEMES

The lightweight schemes are used for authentication such as multi-factor authentication based on ECC, XOR, and bitwise operations [39]. Other password schemes, graphical authentication schemes are also popular [40] for authenticating users. Similarly, many schemes based on three parameters [41] were proposed. These schemes are designed to overcome the drawbacks of previous schemes, such as stolen card attacks and offline password guessing attacks. The multi-factor schemes are classified according to authentication factors as (a) What you know, e.g. user credentials. (b) What you have, e.g., authorized smart card. (c) What you are, e.g. your biometric identity? Examples of multi-factor schemes are Google 2-step and FIDO U2F (universal two-factor) [42].

## 11.8 LIGHTWEIGHT CRYPTOGRAPHICALLY SECURE AUTHENTICATION MODEL

In the IoT communication framework, the data is collected from heterogeneous sensor nodes. These nodes are responsible for data dissemination. Nodes are susceptible to false data injection and node impersonation attacks. In Figure 11.3, we have illustrated the architecture for secure IoT communication by using lightweight schemes. In this architecture, by using internet communication, various IoT-based applications such as smart cities, smart agriculture, and smart automobiles are possible for the betterment of human life. The attacker can easily intercept the information communicated over the network. The attacker can capture, store, modify information, and send it to the unauthorized user. Therefore, lightweight authentication and lightweight cryptography preserve the privacy of user data. In this architecture, we have assumed that all sensor nodes deployed in one particular area send information to the cluster head node. These nodes are then connected to the base station and gateway node. In an IoT-enabled WSN, these forward the sensitive data to nearby gateway nodes through dedicated communication channels using cryptographically secure schemes.

224 Network Optimization in Intelligent Applications

![](img/e0b54a8aa3102369506fc5feb80a6fde_224_0.png)

FIGURE 11.3 Authentication model.

## 11.9 LIMITATIONS OF EXISTING CRYPTOGRAPHY

Considering the above-mentioned work, we analyzed cryptographically secured algorithms for IoT security has certain limitations:

- **Secret key security:** By using lightweight cryptographic schemes, communicating entities share confidential information. However, the secret key is shared on the insecure classical channel which is susceptible to interception.
- **Algorithms:** The lightweight cryptographic algorithms are based on mathematical primitives. Despite the advantages, there is no provision for how these algorithms will safeguard IoT communications.
- **Key size:** The asymmetric schemes are popular as they provide secure key generation and distribution. However, to increase the security for asymmetric algorithms, as RSA, the key size should be increased. It makes encryption slower and increases the complexity.
- **Memory constraints:** The AES algorithm ensures safe communication. However, considering the IoT resource-constrained nature, AES is not acceptable due to high memory requirement to store larger blocks, key size, and s-boxes.

## 11.10 CONCLUSION AND FUTURE WORK

With the advent of IoT devices around us, connected to the internet is increasing rapidly. The major issues concerning these applications are security, privacy, and authentication. Given the need for lightweight cryptography schemes for devices with limited computational power, efficient sensing abilities, and energy constraints. From the review, we have analyzed that RSA and AES schemes impress by their more mathematical structures. On the other hand, hashing is considered the most suitable for ensuring authentication. In addition to that, block cipher techniques such as Feistel network-based SIMON and add-rotate-XOR-based SPEK are most suitable
