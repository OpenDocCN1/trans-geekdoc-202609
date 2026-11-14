
# Key Stretching

Key stretching, also known as key strengthening, is a cryptographic approach that includes lengthening the time it takes to test each potential key to make a weak key stronger. The original key is passed into an algorithm to generate an upgraded key, which should be at least 128 bits in length to be effective. If key stretching is employed, an attacker must either attempt every conceivable combination of the improved key or a large number of plausible combinations of the original key. Because the attacker must calculate the stretching function for each guess in the attack, key stretching slows down the attacker. **Pretty Good Privacy** (**PGP**), **GNU Privacy Guard** (**GPG**), **Wi-Fi Protected Access** (**WPA**), and WPA2 are all systems that employ key stretching. `PBKDF2`, `bcrypt`, and `scrypt` are some of the most widely used password key stretching algorithms.

# Hashing

To generate a one-way message digest, the data is passed through a cryptographic procedure. The method utilized determines the size of the message digest. The data is represented by the message digest, which cannot be reversed to identify the original contents. The message digest may be used to verify data integrity since it is unique. A message is reduced to a hash value using a one-way hash algorithm. Message integrity is determined by comparing the sender’s hash value to the receiver’s hash value. The message has been tampered with if both the sender and recipient employed the same hash function but the resulting hash values are different. Hash functions do not prevent data change, but they do give a way to see whether the data has been altered, as shown in *Figure 15.1*:

![](images/Image29320.jpg)

**Figure 15.1:** Hashing

There are certain restrictions to hash functions. If an attacker intercepts a message containing a hash value, the attacker may change the original message to construct a new incorrect message with a different hash value. If the attacker then sends the intended receiver a second faulty message, the intended recipient will have no means of recognizing that he has received an inaccurate message. When the recipient calculates the hash value, the incorrect message will seem to be legal since it was appended with the attacker’s new hash value rather than the original message’s hash value. To avoid this, the sender should provide a **message authentication code** (**MAC**) in the message. A keyed MAC is created by encrypting the hash function using a symmetric key method. The original message is not encrypted by the symmetric key. It’s solely used to keep the hash value safe. The essential processes of a hash function are shown in *Figure 15.2*:

![](images/Image29327.jpg)

**Figure 15.2:** Process of a Hash Function

Collisions and rainbow table attacks are the two main hash function weaknesses. When a hash function gives the same hash value on several messages, it is known as a **collision**. When rainbow tables are used to reverse a hash by computing all possible hashes and finding the matching value, it is known as a **rainbow table attack**. Message digests may be used to compare multiple files to check whether they are similar down to the bit level since they are defined by the original contents. Data integrity has been compromised if a calculated message digest does not match the original message digest value. To guarantee that real passwords are not stolen, password hash values are often saved instead of actual passwords. It is always preferable to select the hashing function that utilizes a greater hash value when deciding which hashing algorithm to employ. The hash function should be used to determine a file’s hash value. Let’s say you have a document called `contract.doc` that you need to make sure isn’t changed in any manner. Use `md5sum contract.doc`. This command will give you a hash value, which you should write down. Users should always use the `md5sum` command to recalculate the hash value when they require access to the file afterward. The file remains untouched if the value is the same as it was when it was first recorded. If it’s not the same, the file has been altered. `MD2`/`MD4`/`MD5`/`MD6`, `SHA`/`SHA-2`/`SHA-3`, `HAVAL`, `RIPEMD-160`, and `Tiger` are some of the hash algorithms you should be aware of.

# MD2/MD4/MD5/MD6

A 128-bit hash value is generated using the `MD2` message-digest algorithm. It goes through 18 rounds of calculations. `MD2` is still in use today, however, it is much slower than `MD4`, `MD5`, and `MD6`.

A 128-bit hash value is also generated using the `MD4` algorithm. However, it only does three compute rounds. Despite the fact that `MD4` is quicker than `MD2`, it has seen a considerable drop in usage due to the success of attacks against it.

The `MD5` algorithm, like the previous `MD` algorithms, generates a 128-bit hash result. It goes through four rounds of calculations. It was established in response to problems with `MD4`, and it is more complicated than `MD4`. `MD5` is not, however, collision-free. As a result, SSL certificates and digital signatures should not be utilized with it. Instead of `MD5`, the US government mandates the usage of `SHA-2`. However, when releasing software updates for commercial usage, many software providers disclose the `MD5` hash value so that the consumers may check the product’s integrity after downloading.

After conducting a variable number of calculations, the `MD6` algorithm generates a variable hash value. Although it was initially proposed as a replacement for `SHA-3`, it was dropped due to early problems with differential attacks. Since then, `MD6` has been re-released with this flaw patched. That release, however, was too late to be recognized as the `SHA-3` standard by the **National Institute of Standards and Technology** (**NIST**).

# SHA/SHA-2/SHA-3

The `SHA` (Secure Hash Algorithm) is a set of four algorithms developed by the **National Institute of Standards and Technology** (**NIST**) in the United States. After 80 rounds of calculations on 512-bit blocks, `SHA-0` yields a 160-bit hash result. It was initially known as just `SHA` since there were no additional *family members*. Because collisions were detected, `SHA-0` was never particularly popular. After 80 rounds of calculations on 512-bit blocks, `SHA-1` generates a 160-bit hash result, similar to `SHA-0`. The vulnerability in `SHA-0` that left it vulnerable to assaults was fixed in `SHA-1`.

`SHA-2` is a collection of hash functions, each with its own set of functional constraints. The `SHA-2` family consists of the following members:

*   `SHA-224`: After 64 rounds of calculations on 512-bit blocks, it generates a 224-bit hash value.
*   `SHA-256`: After 64 rounds of calculations on 512-bit blocks, it generates a 256-bit hash value.
*   `SHA-384`: After 80 rounds of calculations on 1,024-bit blocks, it generates a 384-bit hash value.
*   `SHA-512`: After 80 rounds of calculations on 1,024-bit blocks, it generates a 512-bit hash result.
*   `SHA-512/224`: After 80 rounds of calculations on 1,024-bit blocks, it generates a 224-bit hash value. The number 512 denotes the size of the internal state.
*   `SHA-512/256`: After 80 rounds of calculations on 1,024-bit blocks, it generates a 256-bit hash value. The 512 identifier denotes the internal state size once again.
