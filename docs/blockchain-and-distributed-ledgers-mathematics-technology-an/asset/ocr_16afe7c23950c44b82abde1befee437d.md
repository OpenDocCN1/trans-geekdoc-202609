# Blockchain and Distributed Ledgers: Mathematics, Technology, Economics

(9) Fee per byte — the meaning is self-explanatory.

(10) Fee weight — the meaning is self-explanatory.

(11) Input index — the sequential number of the input. Since our TX has one input, some-what confusingly, the index is 0.

(12) Previous TXID — the ID of the transaction outputs are used as inputs of our TX. The mathematical induction analogy is clear.

(13) Previous output index — shows which output of the previous transaction is used as input for.

(14) Input address — shows the address from which the input is coming from.

(15) Value — the meaning is self-explanatory.

(16) PubKeyScript — shows how to unlock the input value.

(17) SigScript — the signature used to unlock the input.

(18) Output index — the sequential number of the output. Since our TX has one output, similarly to Input index (11), it is zero.

(19) Output address — shows where the bitcoins are sent.

(20) Value — the meaning is self-explanatory.

(21) PubKeyScript — shows how to unlock the output value in the future.

# Table 5.7 Bitcoin transaction in the parsed form.

| | | |
|---|---||
| 1 | Version | 01000000 |
| 2 | Input count | 01 |
| 3 | Prev. TXID | 5180ff41557877303d10f03cca156679 4516ac65a7764e571dc0c93491f321d |
| 4 | Prev. output number | 05000000 |
| 5 | SigScript size | 6a |
| 6 | Data size | 47 |
| 7 | DER sequence identifier | 30 |
| 8 | Data size | 44 |
| 9 | Int identifier | 02 |
| 10 | Data size | 21 |
| 11 | r value | 00a98648381f405a668b2989ffaa500147c 7cb9f4ce03e912d18529fb3609e243a47 |
| 12 | Int identifier | 02 |
| 13 | Data size | if |
| 14 | s value | 798214efe63e4c7815edae5344f56 52b98ce1bd3693fa95dccd2c6994d88 |
| 15 | sighash | 01 |
| 16 | Data size | 21 |
| 17 | PubKey | 02bd63ab2a615bdd166d554ea3fd5d838 43bff9c76e0b8c6c150d88ee6ca7ea725 ffffff |
| 18 | Sequence number | |

(Continued)