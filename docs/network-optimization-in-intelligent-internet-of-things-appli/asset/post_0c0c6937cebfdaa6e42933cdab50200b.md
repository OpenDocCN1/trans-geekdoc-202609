
# Secure Communication and Authentication in IoT-UAV Networks

- c. Space/Satellite 2 Air communication (S2A): This connection involves the transfer of information between drones and satellite apparatus. This type of connection finds utility across diverse UAV operations, encompassing tasks such as remote sensing and information transfer.
- d. Mixed communication: This form of communication involves combining the previously mentioned three types of communication, namely S2A, A2A, and A2G, in order to achieve expected coverage and enhanced data rates.

## 15.2.4 FEATURES OF IoT-Based UAV Networks

The IoT-based UAV networks' features are the following [8]:

- a. Expense: The affordability of small UAVs within FANET (Flying Adhoc Network) stems from their reduced costs.
- b. Resilience: The presence of multiple UAVs ensures resilience in the event of a single UAV failure.
- c. Acceleration: The increased number of UAVs results in mission completion.
- d. Scalability: The network of multiple UAVs exhibits scalability, allowing for the inclusion of additional UAVs within FANET. Consequently, this facilitates the broadening of the mission's coverage area [9].
- e. Reliability: Unfavourable atmospheric conditions can negatively impact A2G communication. In these scenarios, A2A communication can effectively address connectivity challenges, ensuring the dependability of the network.

## 15.3 Pertinent WORK

Within this segment, a compilation of pertinent works concerning secure communication and authentication within IoT-based UAV networks is presented. While the number of published works in this domain is limited, this chapter strives to encompass the most significant contributions shown in Table 15.1, accompanied by a comparative analysis in Table 15.2.

Lin et al. [10] examined the security and privacy issues relevant to the Internet of drones (IoD). They highlighted verifying the authenticity of drones and location privacy, as well as the confidentiality of transferred data. Teng et al. [11] introduced an authentication procedure aimed at facilitating communication between drones using Elliptic Cryptography (ECC) and Public Key Infrastructure (PKI). While their method offers certain benefits, its implementation could be burdensome for devices with limited resources.

### TABLE 15.1 Summary of Pertinent Work

| Reference | Year | Mechanism | Limitations |
| :--- | :--- | :--- | :--- |
| Lin et al. [10] | 2018 | Privacy-preserving authentication and identity-based encryption | The inherent limitations of resources within IoD architecture hinder the implementation of Identity-based encryption (IBE); No mutual authentication. |
| Teng et al. [11] | 2019 | Elliptic Cryptography (ECC) and Public Key Infrastructure (PKI) | Implementation could be burdensome for devices with limited resources, such as drones. |
| He et al. [12] | 2019 | Proxy signature scheme | Length of the signature is large; signature processing more time. |
| Tian et al. [13] | 2019 | Efficient authentication | Security features such as man-in-the-middle and mutual authentication are missing; No security assessment method. |
| Huang et al. [14] | 2020 | Triangular-oriented strategy | Exorbit expenses for communication and storage. |
| Gope et al. [15] | 2020 | One-way hash and PUF | It falls short in terms of preserving location privacy. |
| Zhang et al. [16] | 2020 | One-way hash and 2-factor authentication | Untraceability is not part of the package. |
| Alladi et al. [17] | 2021 | Drone-MAP | Security assessment method like the random oracle model was provided; does not meet all security requirements like attack resistance. |
| Rajasekaran et al. [18] | 2022 | Anonymous mutual authentication | Bilinear guards are expensive and hard to implement due to complex nature; trusted servers can be vulnerable to attacks. |
| Salam et al. [19] | 2023 | SELTHA (Secure, Efficient, and Lightweight TOTP-based Authentication) | No formal security approach like ProVerif or Scyther. |

### TABLE 15.2 Comparative Analysis of Pertinent Work

| Security Requirements | [10] | [11] | [12] | [13] | [14] | [15] | [16] | [17] | [18] | [19] | This Work |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Mutual authentication | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Man-in-the-middle | × | ✓ | × | × | × | ✓ | × | ✓ | × | ✓ | ✓ |
| Replay attack | × | ✓ | × | × | × | ✓ | × | ✓ | × | ✓ | ✓ |
| Brute-force attack | × | ✓ | × | × | × | ✓ | × | ✓ | × | ✓ | ✓ |
| Physical capture | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Session key | × | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Untraceability | × | ✓ | × | × | × | ✓ | × | × | × | ✓ | ✓ |
| Anonymity | × | ✓ | × | × | × | ✓ | × | × | × | ✓ | ✓ |

* ×, not discussed; ✓, discussed.

He et al. [12] put forth an ECC-driven blind signature system for drone networks. This proxy signature, based on identification, intentionally omits any details about the drone's identity acting as a delegated signer to preserve anonymity. However, this particular approach doesn't align with our authentication objectives and may expose vulnerabilities to harmful incursions. Furthermore, an effective proxy signature mechanism should possess comparable information about the proxy signer as the original signer.

Tian et al. [13] introduced an authentication framework to establish secure communication among drones. This system incorporates an online/offline signature method and leverages mobile computing technology. In addition to ensuring robust authentication, the suggested strategy takes into account the imperative of safeguarding the privacy of drones' identities and whereabouts. The authors fail to describe security features such as man-in-the-middle and mutual authentication.

Huang and Savikin [14] proposed a novel technique for establishing charging stations for drones. This method employed a triangular-oriented strategy. Furthermore, charging stations that experienced lower foothold or remained unoccupied were systematically eliminated through recursive processes. It's important to note that this research does not primarily address the aspects of communication and storage expenses.

Gope et al. [15] put forth a proposal at guaranteeing the tangible safety of drones. This scheme relies on the deployment of physically unclonable functions and hash operations. While the scheme effectively safeguards the physical integrity of drones, it falls short in terms of preserving the privacy of their location.

Zhang et al. [16] unleashed an efficient authentication and key agreement (AKA) blueprint, hinting entirely on unidirectional hash function. Despite its robustness, this strategy neglects measures for concealing privacy.
