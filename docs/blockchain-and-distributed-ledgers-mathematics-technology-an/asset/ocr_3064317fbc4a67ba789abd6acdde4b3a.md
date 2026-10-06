# 166 Blockchain and Distributed Ledgers: Mathematics, Technology, and Economics

(22) OP_DUP — hex opcode.
(23) OP_HASH160 — hex opcode.
(24) A one-byte of PublicKey key — 14 (hex) = 20 (dec).
(25) PubKey — the HASH160 hash of the public key to which bitcoins are sent.
(26) OP_EQUALIFY — hex opcode.
(27) OP_CHECKSIG — hex opcode.
(28) Locktime — indicates the time of TX consumption. The lock time of 0000000 means that TX can be included in the block immediately without delay.

Of course, under the hood, this transaction looks differently. In the so-called scripted, or raw form, it is a set of 382 hexadecimal sums (191 bytes), which compactly serialized, and decapsulates the transaction for all time; see Table 5.8.

Table 5.8 Bitcoin transaction in the serialized form.
| Raw TX data |
| 0100000001580ff451587703d1003ca156679451ac65a776a67745e1dc9c73493f521d05000006a7369f5b3c7a5d60437022a009683f415a686289f98aa50017c2bf9f4c6e921238529fb3609e243a240271f7928214e634b8e4c2718ed5ebac53f6558b9c2bd369f5b7a5d626cd2d69f90701128d63ab426521bd6d15543ea3d5d38843f779e0638f7ca1550b85eca77525555ff010a8b201100000019976a411d050000006a7324444818264444502e65485178b2e5485179d45f002641decdec4748ac00000000 |
| First hash |
| 73c22f83d76222d41158b35d2469a45b3721f2f7fed1734360842f9583d5114f Second hash |
| 8f239a211d0b8fe75d93beff39eeb5e359ba4a56ea7490327ddf7548c92 TXID-reverted second hash |
| 928c4275dfd62703049e76aa54a9b355feb99e31fbe93dd75feb81d219a23f8 |

It is easy to check that Public Key, as shown as part of SigScript in line 17 of Table 5.6 and explicitly in line 17 of Table 5.7, the right key is for the hashed Public Key shown as part of PubKeyScript in line 16 of Table 5.6. The corresponding steps are shown in Table 5.9.

Thus, we recover the PubKeyHash and the right bitcoin address.