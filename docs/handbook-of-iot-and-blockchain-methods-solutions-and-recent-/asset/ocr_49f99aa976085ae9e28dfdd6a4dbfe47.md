# 8.3.21 ILLEGAL ACTIVITIES

An illicit group of people can utilize the blockchain network or platform to perform various illegal activities. For instance, the Silk Road website was an online marketplace for illegal drug where sellers and buyers whose identities are anonymous did business using bitcoin (Hong 2015). Cryptocurrency that uses blockchain technology may also facilitate money laundering. Although bitcoin is not yet treated as a fiat currency, it makes it possible to create an “underground” channel for illegal movement of funds within its network.

# 8.3.22 IDENTITY THEFT

Although Blockchains preserve anonymity and privacy, the security of assets depends on safeguarding the private key, a form of digital identity. If one’s private key is acquired or stolen, no third party can recover it. Consequently, all the assets this person owns in the blockchain will vanish, and it will be nearly impossible to identify the thief. The consequences may be more devastating than identity theft in the offline world, where third-party institutions (e.g., credit card companies) or central authorities safeguard transactions, control risks, detect suspicious activities, or help find culprits. Also, current cryptography standards are not completely uncrackable (Swan 2015). With the advent of quantum computing, it is not impossible for cryptographic keys to be cracked quickly, demolishing the foundation of blockchain technology (Crosby et al. 2016).

# 8.4 POTENTIAL DEFENSES AGAINST SECURITY THREATS ON BLOCKCHAIN

Potential defenses which assure security against man-in-the-middle-attacks, hardware Trojans, etc., include the following schemes:

+   • **Watermarking:** Someone requests a transaction directly known as client or via something called a wallet. The transaction directly request from the client will deliver either a commit or by a process at the server where the transaction initiated known as the master. In watermarking, the original client’s digital signature is provided with the request. Watermarks are able to assure ownership as these are much more difficult to identify and modify. Unfortunately, the watermarking technique is not able to guarantee security against hardware Trojans.

+   • **Metering:** In this technique, both the public signature of wallet/master and the client’s digital signature are added to the transaction request as processing constraints. This metering scheme is not also able to assure protection against hardware Trojans as the attacker is able to create and hide a malicious Trojan in the circuit due to availability of the design functionality.

+   • **Side-channel fingerprinting:** This scheme is able to detect hardware Trojans easily as the manufactured parametric characteristics, such as power, area, delay, and block characteristics of the transaction are compared with those of