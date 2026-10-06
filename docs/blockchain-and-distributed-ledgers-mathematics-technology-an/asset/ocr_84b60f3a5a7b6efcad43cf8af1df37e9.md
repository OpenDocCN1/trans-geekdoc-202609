# Blockchain and Distributed Ledgers: Mathematics, Technology, Economics

(3) Split $I$ into two 32-byte sequences $I_L$ and $I_R$ respectively, such that master key $m = I_L$, and master chain code $c = I_R$.

(4) If master key is invalid (that is, if $m = 0$ or $m$ larger than the order of the curve), go to (1).

The master key is used as an initial key to derive new keys — which themselves will be hierarchically derived in a tree structure. The chain code characterizes the key derivation (CKD) at the node level, that is, how new keys are derived. BIP32 defines two different derivation modes:

+   * hardened derivation: hardened derivation computes a child secret key from a parent secret key (see Figure 9.6), therefore access to the keystore, to generate any child key. Access to the keystore is required for every new address.

+   * non-hardened derivation: non-hardened derivation computes a child public key from a parent public key (see Figure 9.7). Non-hardened derivation does not require any knowledge of the parent secret key to generate new public keys, or addresses; it does not reveal any information about the child secret key. The protocol guarantees nonetheless that the secret key implicitly corresponding to the derived child public key exists, and it may be independently calculated from the parent secret key available in the keystore.

Both derivation schemes are complementary and may be used jointly to compute a key that has been partly derived with a hardened scheme, partly derived with a non-hardened scheme. Non-hardened derivation was proposed precisely to the creation of new addresses with no access to secret keys, so that the keystore may be isolated for security reasons.

![](bbox=[0.273, 0.626, 0.725, 0.896])

Figure 9.6 Hardened child key derivation with BIP32. Own graphics.