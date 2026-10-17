
## TABLE 3 各实体的设置时间

| 实体 | 操作 | 计算 | 时间 (ms) |
|---|---|---|---|
| EV | 公钥/私钥生成 | `T2` | 2.03 |
| Bank | 公钥/私钥生成 | `3T2` | 6.09 |
| Bank | 构建树 | `(2^l − 1) × (T2 + T1)` | `(2^l − 1) × 3.37` |
| Attribute authority | 公钥/私钥生成 | `T1 + T2 + T3` | 3.38 |
| Attribute authority | 属性生成 | `4T2 + 2T4 + 2T5` | 8.25 |
| CSP | 公钥/私钥生成和共享密钥生成 | `T2 + 2 × (n − 1) × (n_r − 1) × T7` | `2.03+0.007×(n − 1)×(n_r − 1)` |
| RSU | 共享密钥生成 | `2 × (n − 1) × (n_r − 1) × T7` | `0.007 × (n − 1) × (n_r − 1)` |
| Charging pad | 共享密钥生成 | `(n − 1) × (n_p − 1) × T7` | `0.003 × (n − 1) × (n_p − 1)` |

## TABLE 4 计算开销

| 场景 | 实体 | 计算 | 时间 (ms) |
|---|---|---|---|
| Authentication to bank | EV | `3T1+T2+T5+T10+T11` | 20.16 |
| Authentication to bank | Bank | `6T2+T5+T10+T11` | 26.29 |
| Regular authentication to CSP | EV | `7T2+2T7+T8+T9+T11` | 21.45 |
| Regular authentication to CSP | CSP | `8T1+2T7+T5+T8+T9+T10` | 27.74 |
| Prioritized authentication to CSP | EV | `3dT1+6T2+(d+2)T3+(3d+1)T6+2T7+2T8+2T9+T11` | `4.03d+19.49` |
| Prioritized authentication to CSP | CSP | `(2d+9)T1+4dT2+(2d+2)T3+dT4+(d+1)T5+(d+1)T6+T7+2T8+2T9+T10` | `10.9d+19.08` |
| Authentication to RSU | EV | `2T7+T9` | 0.02 |
| Authentication to RSU | RSU | `2T7+T9` | 0.03 |
| Authentication to CP | EV | `2T7` | 0.007 |
| Authentication to CP | CP | `2T7` | 0.007 |

in `G1`, one keyed hash for verification, and one signature verification; for message (3) four exponentiations in `G1` for bank signature anonymization, one hash operation and one exponentiation in `G1` for generation of `π`, and one AES symmetric-key encryption; for message (4) one AES symmetric-key decryption. The total computations done by the EV can be formulated as `7T2 + 2T7 + T8 + T9 + T11`. On the other hand, the CSP performs the following computations: for message (1) one exponentiation in `G1`; for message (2) one exponentiation in `G1`, one keyed hash for verification, and one signature; for message (3) eight asymmetric pairing operations and one multiplication in `G1` for verification of bank signature, and one AES symmetric-key decryption; for message (4) one AES symmetric-key encryption. The total computations done by the CSP can be formulated as `8T1 + 2T2 + T5 + T7 + T8 + T9 + T10`.

During prioritized service, five messages are exchanged between the EV and the CSP, as shown in Fig. 6. Each EV performs the following computations: for message (1) the EV decrypts the attribute-based encrypted challenge by computing `3d` symmetric pairing, `3d + 1` multiplication in `GT`, and `d + 1` exponentiation in `GT`, in addition to one signature verification; for message (2) one exponentiation in `GT`, one keyed hash, and one AES symmetric encryption; for message (4) one exponentiation in `G1` for `tsr`, one hash operation and one exponentiation in `G1` for `π`, four exponentiations in `G1` for bank signature anonymization, and finally one AES symmetric encryption; for messages (3) and (5) two AES symmetric-key decryptions. The total computations done by the EV can be formulated as `3dT1 + 6T2 + (d + 2)T3 + (3d + 1)T6 + 2T7 + 2T8 + 2T9 + T11`. On the other hand, the CSP performs the following computations: for message (1) the CSP encrypts a challenge by computing `2d + 1` symmetric pairing operations, `2d + 1` exponentiation in `GT`, `d + 1` multiplication in `GT`, `4d` exponentiation in `G1`, `d` hash to `G1`, and `d` product in `G1`, in addition to one signature; for message (2) one exponentiation in `GT`, one keyed hash for verification, and one AES symmetric decryption; for message (3) one AES symmetric encryption; for message (4) eight asymmetric pairing operations and one multiplication in `G1` for verification of bank signature, and one AES symmetric-key decryption. The total computations done by the CSP can be formulated as `(2d + 9)T1 + 4dT2 + (2d + 2)T3 + dT4 + (d + 1)T5 + (d + 1)T6 + T7 + 2T8 + 2T9 + T10`.

For EV authentication with the RSU, it needs two hashing operations, one XOR operation, and one AES decryption to authenticate itself to each RSU. The XOR operations are ignored because they are infinitesimally small. The total computations done by the EV can be formulated as `2T7 + T9`. On the other hand, the RSU needs to perform one symmetric encryption and two hashing operations to authenticate each EV. The total computations done by the RSU can be formulated as `2T7 + T9`.

For EV authentication with CP, it needs two hashing operations and one XOR operation. The total computations done by the EV can be formulated as `2T7`. On the other hand, each CP needs two hashing operations to authenticate each EV. The total computations done by the RSU can be formulated as `2T7`.

## 6.2 通信开销

| 场景 | 实体 | 通信 (字节) |
|---|---|---|
| 认证到银行 | EV | 328 |
| 认证到银行 | Bank | 260 |
| 常规认证到 CSP | EV | 320 |
| 常规认证到 CSP | CSP | 252 |
| 优先认证到 CSP | EV | 660 |
| 优先认证到 CSP | CSP | `256d + 236` |
| 认证到 RSU | EV | 20 |
| 认证到 RSU | RSU | 40 |
| 认证到 CP | EV | 20 |
| 认证到 CP | CP | 40 |

messages: message (1) requires 4 bytes for `GID`, 4 bytes for `TS`, 64 bytes for `g^x`, and 128 bytes for `σ_UI`; message (3) requires 64 bytes for `s`. The total packet size sent by the EV is 328 bytes. On the other hand, the bank sends the following messages: message (2) requires 4 bytes for `TS`, 64 bytes for `c`, and 128 bytes for `σ_B(c||TS)`; message (4) is four group points of 64 bytes each. The total packet size sent by the bank is 260 bytes.

During regular service, four messages are exchanged between the EV and the CSP, as shown in Fig. 7. The EV sends the following messages: message (1) requires two group points of total size of 128 bytes, and message (3) requires five group points encrypted with AES with a total size of 320 bytes, and 20 bytes for the HMAC. The total packet size sent by the EV is 468 bytes. On the other hand, the CSP sends the following messages: message (2), which requires 64 bytes for one group point, 20 bytes for HMAC, and 128 bytes for signature; message (4) requires 40 bytes for authentication tokens. The total packet size sent by the CSP is 252 bytes.

During prioritized service, three messages are exchanged between the EV and the CSP, as shown in Fig. 6. The EV sends message (2), which contains 10 group points of 640 bytes, and 20 bytes for the HMAC, so the total size is 660 bytes. On the other hand, the CSP sends message (2), which contains an ABE challenge of size `(4d + 1) × 64` bytes, 4 bytes for the `TS`, and 128 signature; for message (3) it requires 40 bytes for authentication tokens. The total packet size sent by the CSP is `256d + 236` bytes.

For EV authentication with RSU, the EV receives 40 bytes for the challenge and the confirmation and sends 20 bytes for the authentication code. The same packet size is sent for the authentication with the CP.

## 7 结论与未来工作

In this chapter, we presented an integrated and secure scheme that offers anonymous authentication, prioritization, and payment for dynamic charging systems. The scheme allows EVs to purchase divisible e-coins from the bank that can later be used for the recharge of EV batteries. In addition, the scheme allows the CSPs to offer prioritized service to EVs based on the charging demand and its energy supply. Prioritization is performed using multiauthority ABE to authenticate EVs that need to charge. Moreover, an efficient hierarchical authentication scheme that is based on symmetric-key cryptography is used to authenticate EVs to RSUs and CPs. Our extensive privacy and security analysis have demonstrated that our scheme is secure against different attacks, and can achieve required privacy features. Also, our measurements have demonstrated that the computational and communication overhead of the proposed scheme are acceptable.
