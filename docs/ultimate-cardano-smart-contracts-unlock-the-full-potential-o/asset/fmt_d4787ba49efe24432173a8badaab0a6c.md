
Using a blockchain explorer, we can see what this transaction looks like on the Cardano blockchain, as shown in [Figure 3.3](#c03.xhtml#fig3_3): [https://preprod.cexplorer.io/tx/c9e6dc1e7ecdf7110747c91d0d638ce896435a504e745025996230533ae9f548](https://preprod.cexplorer.io/tx/c9e6dc1e7ecdf7110747c91d0d638ce896435a504e745025996230533ae9f548)

![](images/Figure-3.3.jpg)

**Figure 3.3:** Block Explorer Transaction View

# Transaction Input

A transaction input simply points to a transaction hash on the ledger and index since there may be more than one transaction output for a specific transaction.

![](images/Figure-3.4.jpg)

**Figure 3.4:** Transaction Input

The ledger specification[⁴](#c03.xhtml#ftn4) for an input is defined as:

```
transaction_input = [ transaction_id : $hash32
, index : uint
]
```

# Transaction Output

Before the Alonzo Era of smart contracts, a transaction output contained the following:

*   Address that the output is locked at
*   Value of Ada and any Cardano native tokens
*   Optional `datum` used for storing a persistent data hash

The ability to store a `datum` value with a UTXO is how Cardano uses a EUTXO model, whereas Bitcoin only uses a UTXO model.

Here is an example of 2 EUTXOs at an address on Cardano\*:

```
$ cardano-cli query utxo --address addr_test1vzu…dxn7 --cardano-mode --testnet-magic 1
TxHash TxIx Amount
--------------------------------------------------------------------
158…925 0 3551912116 lovelace + TxOutDatumNone
b4e…0d2 0 5000000 lovelace + TxOutDatumNone
```

*\*Please note that the address and TxHash have been truncated for formatting.*

Observations:

*   In this example, there are 2 UTXOs.
*   Transaction hash `158…925` with index 0 has 3,551,912,116 lovelace.
*   Transaction hash `b4e…0d2` with index 0 has 5,000,000 lovelace.
*   There is 1,000,000 lovelace in 1 Ada.
*   The amount of Ada locked at the address is:
    ```
    3,551.912116
    + 5.000000
    3,556.912116
    ```
*   There is no datum associated with these UTXOs.

Post Alonzo, additional fields were added to the outputs. In the current Conway Era, we have the following output fields:

*   Address that the output is locked at
*   Amount of Ada and any Cardano native tokens
*   Optional `datum` used for storing a persistent data hash on-chain
*   Optional `inline datum` used for storing persistent data value on-chain
*   Optional `reference script` that allows a smart contract to be stored on-chain

Here is an example of a UTXO in the Conway era:

```
$ cardano-cli query utxo --tx-in 5f07cfe475c846a7a644850f7174d98d281b09d3a780a0e51d06d1adff0cdcf7#4 --cardano-mode --testnet-magic 1 --out-file utxo.out
$ cat utxo.out
{
"5f07cfe475c846a7a644850f7174d98d281b09d3a780a0e51d06d1adff0cdcf7#4"
: {
"address":
"addr_test1qrazs4ngp8vl0h2qaexugnm4lhjts0g7l94d780pyx99f87m76rh0cewyp03f8w9e2lemp96jtqk0hyjqtg5528pn9tsyqhfr5",
"datum": null,
"datumhash": null,
"inlineDatum": null,
"referenceScript": null,
"value": {
"lovelace": 981840654
}
}
}
```

The `datum` field contains the datum value attached to a transaction when it is submitted to the Cardano blockchain. If an `inlineDatum` is used, the datum value is stored on-chain, otherwise, only the `datumhash` is recorded on-chain.

Looking at the ledger specification,[⁵](#c03.xhtml#ftn5) the output is defined as follows:

```
post_alonzo_transaction_output =
{ 0 : address
, 1 : value
, ? 2 : datum_option ; datum option
, ? 3 : script_ref ; script reference
}

datum_option = [ 0, $hash32 // 1, data ]
```

# Metadata

A transaction can have metadata and is optionally included when submitting a transaction to the network. Only the hash of the metadata contents is stored on-chain and is not accessible to smart contracts. Blockchain indexers, however, capture, store, and retrieve the full contents of the transaction metadata, which are used for off-chain transaction building. CIP-25,[⁶](#c03.xhtml#ftn6) using label 721, was the first transaction metadata standard for minting transactions of Non-Fungible Tokens or NFTs.

A minimal structure for an NFT using CIP-25, version 1, is as follows:

```
{
 "721": {
 "<policy_id>": {
 "<asset_name>": {
 "name": <string>,
 "image": <uri | array>
 }
 }
 }
}
```

An example of this standard being used and viewed with a blockchain explorer[⁷](#c03.xhtml#ftn7) is shown in [Figure 3.5](#c03.xhtml#fig3_5):

![](images/Figure-3.5.jpg)

**Figure 3.5:** Transaction Metadata

Where:

*   `policy_id` is `63733059deaddff620870b22f1ff6a9907bcd103e70d5dfcc53bbb14`
*   `asset_name` is `Mad Dog`
*   **NFT** name is `Mad Dog`
*   **NFT** image is `QmckPQPzthJjkS9GRSxdw2SzSinAwdDW34xXDZd26MrV5S`
*   **NFT** description is `Crazy dog that loves treats`

# Plutus Scripts

Up to this point, we have only looked at transactions that send (spend) assets from an address owned by a user with a corresponding public and private key. In Cardano, we have Smart Contracts that use a Turing-complete scripting language called Plutus. A Plutus script can spend or mint successfully only if the evaluated result returns true. The script is included when submitting a transaction so it can be evaluated by the **Plutus Core Evaluator** inside a Cardano node. As we recall, the network comprises connected nodes that form a consensus on valid blocks. So, when a transaction is submitted, each node must execute the included script and confirm the result. If true, the node will accept the transaction into the block and become part of the blockchain.

Typically, a Plutus script is either a `spending` **(validator)** or a `minting` script. A `spending` script involves spending UTXOs locked at a script address. The script address is simply a hash of the script itself and the appropriate address header byte value. A `minting` script involves minting (adding) or burning (removing) native tokens in the Cardano ledger. When a `minting` script is used to mint, the new tokens must be included in a UTXO(s) as output(s) and sent to an address. Conversely, when a `minting` script is used to burn, the tokens must be included in UTXO(s) as input(s).

# Datums

When we looked at transaction outputs, we observed that you can include a datum value for data persistence. This datum value can be read by a Plutus spending script that examines the transaction UTXO input. Since a UTXO can only be spent once as an input, the datum value must be recreated and included in the UTXO output if used by another script. If using a reference input, however, the UTXO is read-only, so the datum value can be reused for any number of transactions serially or in parallel.

# Redeemers

Redeemers can provide information to a Plutus script during script evaluation within a transaction. For example, the ability to specify what type of mint operation (minting or burning) a transaction will execute. Redeemers can also pass information to a Plutus script that is only known at run time and does not need to be persistent.

The following are the different types of Redeemers from the ledger specification[⁸](#c03.xhtml#ftn8):

```
redeemer_tag =
0 ; Spending
/ 1 ; Minting
/ 2 ; Certifying
/ 3 ; Rewarding
/ 4 ; Voting
/ 5 ; Proposing
```

We reviewed the `Spending` and `Minting` Redeemer tags, so now let’s look at `Certifying` and `Rewarding`. A `Certifying` Redeemer is used for publishing certificates to the network. This is used, for example, when registering a staking key to the network for staking. A `Rewarding` Redeemer is used for withdrawing staking rewards locked at a stake key address. Recall that a staking address is not a UTXO-based address and is only used to receive staking rewards. At the time of writing, `Voting` and `Proposing` Redeemer tags will be used for on-chain governance and voting.
