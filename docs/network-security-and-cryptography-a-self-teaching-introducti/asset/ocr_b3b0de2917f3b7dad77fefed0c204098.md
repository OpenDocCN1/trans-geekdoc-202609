# 6.7.4.5.2 Advantages and Limitations of CTR

The advantages of CTR are:

+   - Parallel Processing:

In CFB and OFB, the plaintext blocks have to be encrypted sequentially, since feedback from the previous step is required for the encryption/decryption of the next block of plaintext. However, in the counter mode, knowing Block Number (K) of a block, it can be decrypted out of sequence by using the Counter Value (Counter + K-1). This feature enables encryption/decryption of more than one block in parallel. Thus, the processors that support parallel processing can be employed to enhance the encryption/decryption speed tremendously.

+   - Pre-processing:

The output of Encrypt Algorithms for various values of Counter can be computed in advance and stored in memory (if sufficient memory is available and security of these values can be ensured). These precomputed values of Encrypt output are then used to encrypt/decrypt a plaintext block much more efficiently.

+   - Random Access:

Knowing the block number, any block of plaintext can be encrypted and any block of cipher-text can be decrypted randomly.

+   - Simplicity: Unlike the ECB and CBC modes, Counter Mode requires implementation of only the Encrypt Algorithm both for the Encryption and Decryption sides.

+   - Provable Security:

CTR is at least secure as the other modes. Due to these advantages, the Counter Mode makes an ideal choice for Asynchronous Transfer Mode (ATM) security and IP Security (IPSec).

The limitations of CTR are:

+   - The CTR mode, like the ECB mode, cannot be used for real-time processing.