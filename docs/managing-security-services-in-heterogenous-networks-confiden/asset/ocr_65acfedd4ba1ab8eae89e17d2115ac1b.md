| SECURITY FEATURES | UTILIZES/BASED ON |
|---|---|
| BR/EDR Legacy Pairing | E21 or E22 algorithms based on SAFER + |
| Device authentication | E1 algorithm, based on SAFER + . |
| Encryption | E0 algorithm derived from the Massey-Rueppel algorithm |
| Message integrity | no provision for cryptographic. Though CRC can offer integrity protection, it is not considered to offer cryptographic integrity as it can be easily counterfeited |
| Secure Simple Pairing | FIPS-approved algorithms (SHA-256, HMAC-SHA-256 and the P-192 elliptic curve) and four association models: Just Works, Numeric Comparison, Comparison, Passkey Entry and Out-Of-Band |
| LE Legacy Pairing | AES-CCM encryption and four association models: Just Works, Numeric Comparison, Passkey Entry and Out-Of-Band. It also offers signed data and a privacy feature. |
| Secure Connections on the BR/EDR physical transport promotes Secure Simple Pairing | P-256 elliptic curve and device authentication to use FIPS-approved algorithms (HMAC-SHA-256 and AES-CTR). Secure Connections also enhances message integrity (AES-CCM). |
| Secure Connections on the LE physical transport upgrades LE Legacy Pairing | FIPS-approved algorithms (AES-CMAC and P-256 elliptic curve) and acclimatizes the Numeric Comparison association model of Secure Simple Pairing to be used on the Bluetooth LE physical transport. It also embraces provisions for a key created using Secure Connections on whichever physical transport to preclude the need for the user to pair a second time on the other physical transport. |

# 7.5.2 Security Services

The Bluetooth security model consists of five discrete security features, namely, the bonding, device authentication, encryption, message integrity and pairing.

+   * **Authentication** – It is used to verify the identity of the devices that are communicating. But user authentication is not offered natively.