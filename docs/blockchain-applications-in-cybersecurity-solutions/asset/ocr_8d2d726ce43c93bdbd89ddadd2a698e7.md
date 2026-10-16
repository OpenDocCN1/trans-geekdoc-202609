2. Posterior corruption — attempting to mint more blocks in a particular time frame than the main chain.

3. Stake leakage — duplicating a transaction from a properly kept ledger.

When initiating a remote attack, a hacker utilises a purchased or stolen private key from a big token balance that has previously been utilised for verification. The hacker can modify the blockchain's history and receive rewards based on PoS validation [26].

# b. User Wallet Attacks

In fact, until individuals interact with blockchains and cybersecurity, they're like salt and pepper. It may come as a surprise, but blockchain users are the most dangerous to security. People tend to overvalue the blockchain's security and overlook its flaws. Cybercriminals are mostly interested in user wallet credentials.

Hackers attempt to get wallet credentials using both old tactics, such as phishing and dictionary attacks, as well as more complex ones, such as identifying flaws in cryptographic techniques. Here's a rundown of popular ways to get into people's wallets [27].

# Phishing

In 2018, iotaseed.io (now offline), a phoney online seed generator, was used to launch an attack on IOTA wallets. Hackers used this service to execute a phishing campaign and obtain logs, including secret seeds. As a result, hackers were able to steal more than $4 million worth of IOTA from victims' wallets in January 2018 [28].

# Dictionary Attacks

During these attacks, a hacker tries to hash values of common passwords like password1 to decrypt a victim's cryptographic digest and salt. Attackers can find wallet credentials by converting clear text passwords to cryptographic hashes [29].

# Vulnerable Signatures

Blockchain networks establish user signatures using a variety of cryptographic algorithms, but they may be vulnerable. Bitcoin, for example, employs the ECDSA cryptographic technique to produce unique private keys automatically. However, ECDSA does not appear to have enough entropy, resulting in the same random value appearing in multiple signatures. IOTA's former Curl hash