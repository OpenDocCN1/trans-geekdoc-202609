
# Transaction

For example, *[Figure 4.2](#c04.xhtml#fig4_2)* shows a transaction executing a Plutus validator script:

[https://preprod.cexplorer.io/tx/99c529355ebd1f410517457b6ff04e66c2de28b8667b9428ec232e03efa22c29](https://preprod.cexplorer.io/tx/99c529355ebd1f410517457b6ff04e66c2de28b8667b9428ec232e03efa22c29)

![](images/Figure-4.2.jpg)

**Figure 4.2:** Transaction Example

The **CBOR** hexadecimal format for this transaction that was submitted to the network is as follows:

```
84a80082825820d9b02da5897bd1ff9e2fdab008334d2804ea1accab
c7c3962e33771ed9f1a8d500825820d9b02da5897bd1ff9e2fdab008334d2804ea1a
ccabc7c3962e33771ed9f1a8d501018182581d606d04be153546d63c8a33
e0c11ec44cf790803f31c2f893fc241529531a05eb1244021a0002
d9250b582031e6c463846e3c0afe2aebfc9993355dbe8ce4dab892a7
af0e397a75df3509b90d81825820d9b02da5897bd1ff9e2fdab008334d2804ea1a
ccabc7c3962e33771ed9f1a8d5010e81581c6d04be153546d63c8a33e0c11e
c44cf790803f31c2f893fc241529531082581d606d04be153546d63c8a33e0c11
ec44cf790803f31c2f893fc241529531a05d9dd11111a000445b8a30081825820
fc6500742705cfe8c2f0822e73e2ab09c43285973adffe8aa06bd12d1fa6051f584
0ec7f53a69852e6daa868a3f221114435544ab2851bc6f2f42abe9772507b30064a1
f012ddab23153644703047ea2faf9132390e91937b82389626404d7adfd0105818
40000d8799f4d48656c6c6f2c20576f726c6421ff821977151a009daaac068158f258
f0010000323232323232323222232325333008323232533300b002100114a066446
46600200200644a66602200229404c8c94ccc040cdc78010028a511330040040013
014002375c60240026eb0c038c03cc03cc03cc03cc03cc03cc03cc03cc020c008c0
20014dd71801180400399b8f375c6002600e00a91010d48656c6c6f2c20576f726
c6421002300d001149858c94ccc020cdc3a400000226464a66601a601e0042930b1ba
e300d00130060041630060033253330073370e90000089919299980618070010a4
c2c6eb8c030004c01401058c01400c8c014dd5000918019baa0015734aae7555cf2a
b9f5742ae89f5f6
```

When we decode this to a diagnostic form using [https://cbor.nemo157.com/](https://cbor.nemo157.com/), we can see the transaction details, as illustrated in *[Figures 4.3](#c04.xhtml#fig4_3)* and *[4.4](#c04.xhtml#fig4_4)*. *[Figure 4.3](#c04.xhtml#fig4_3)* shows the UTXO inputs and outputs and the required signatures for this transaction:

![](images/Figure-4.3.jpg)

**Figure 4.3:** CBOR Transaction Part 1

*[Figure 4.4](#c04.xhtml#fig4_4)* shows the collateral required, the public key, Redeemer, and Plutus script witnesses. This transaction does not contain auxiliary data or metadata, and the transaction validity flag is set to true.

![](images/Figure-4.4.jpg)

**Figure 4.4:** CBOR Transaction Part 2

## Redeemer

To get a human-readable version of the Redeemer, we need to convert from the Hex ByteString to a UTF-8 string. Plutus, however, will use the ByteString directly during script execution. Here is an example of using `xxd` to convert a Hex-encoded ByteString to a normal string:

```
$ echo 48656c6c6f2c20576f726c6421 | xxd -p -r
$ Hello, World!
```

## Plutus Script

The Plutus script is double encoded (CBOR + flat), meaning we need to deserialize it twice to get it into UPLC. So, the first step is to decode it using a CBOR decoder,[^(15)](#c04.xhtml#ftn15) and save it to a file called `plutus.flat`:

```
$ cat plutus.flat
010000323232323232323222232325333008323232533300b002100114a066446466002
00200644a66602200229404c8c94ccc040cdc78010028a511330040040013014002375c
60240026eb0c038c03cc03cc03cc03cc03cc03cc03cc03cc020c008c020014dd7180118
0400399b8f375c6002600e00a91010d48656c6c6f2c20576f726c6421002300d0011498
58c94ccc020cdc3a400000226464a66601a601e0042930b1bae300d0013006004163006
0033253330073370e900000089919299980618070010a4c2c6eb8c030004c01401058c0
1400c8c014dd5000918019baa0015734aae7555cf2ab9f5742ae8
```

Next, we need to convert it from hex to UPLC using the Aiken utility tool to decode it:

```
$ aiken uplc decode --hex plutus.flat
(program
1.0.0
[
(lam
i_0
[
(lam
i_1
…
)
(force (builtin headList))
]
)
(force (builtin tailList))
]
)
```

## Datum

Next, we will look at a Datum in *[Figure 4.5](#c04.xhtml#fig4_5)* using `cexplorer.io`:[^(16)](#c04.xhtml#ftn16)

![](images/Figure-4.5.jpg)

**Figure 4.5:** Datum Example

The datum in *[Figure 4.5](#c04.xhtml#fig4_5)* is an inline datum, so the value is stored on-chain and locked at a UTXO that we want to spend. If we look at the UTXO, we will see that the value is encoded in CBOR hex format:

`d8799f581c6d04be153546d63c8a33e0c11ec44cf790803f31c2f893fc24152953ff`

When we decode the datum CBOR hex value, we get the following output of a byte array:

```
121_0([_
h'6d04be153546d63c8a33e0c11ec44cf790803f31c2f893fc24152953',
])
```

In this example, the datum value represents a public key hash.

## Plutus Execution Budget

Looking at the Redeemer Witness of the transaction in *[Figure 4.4](#c04.xhtml#fig4_4)*, we will notice an execution budget for the attached plutus script:

`[30485_1, 10332844_2]`

These values refer to the memory and CPU (steps) execution units, which are defined in the Plutus ledger specification:

`ex_units = [mem: uint, steps: uint]`

The `mem` and `steps` are calculated and submitted with the transaction, then verified by the Plutus Core Evaluator during script execution. If either of the values exceeds the maximum limits during script execution, then an error will be raised:

```
Error: The budget when the machine terminated was:\n({ cpu: -84834\n| mem: 17553\n}
```

In this example, the `cpu/steps` value was exceeded and resulted in a negative number. As a result, the execution was halted, and the validation failed. To calculate the `mem` and `cpu/step` costs for a given Plutus script, a `cost model`[^(17)](#c04.xhtml#ftn17) is used to map the `execution cost` for each Plutus operation. The cost model is located in the network protocol parameters and can be changed over time via network updates. To see the `protocol parameters`, you can use the `cardano-cli` tool:

```
$ cardano-cli query protocol-parameters --testnet-magic 1
{
"collateralPercentage": 150,
"costModels": {
…
"PlutusScriptV2": {
"addInteger-cpu-arguments-intercept": 205665,
"addInteger-cpu-arguments-slope": 812,
"addInteger-memory-arguments-intercept": 1,
"addInteger-memory-arguments-slope": 1,
…
"maxTxExecutionUnits": {
"memory": 14000000,
"steps": 10000000000
},
"maxTxSize": 16384,
…
```

The protocol parameters specify, among other things, the execution cost of each Plutus operation, the maximum `memory` and `steps` units per transaction, and the maximum overall transaction size (`maxTxSize`) in KB.

## Collateral

The last topic we will look at is collateral included in a transaction. Collateral is a small amount of Lovelace (1.5 × Transaction Fee) that will be used if there is a phase-2 Plutus script failure.[^(18)](#c04.xhtml#ftn18) Any change left over from the collateral inputs is returned to the user and is called the **collateral return**. However, Plutus script evaluation is usually done locally before submitting it to the network. This will catch and prevent the submission of an invalid Plutus script. The role of collateral is to help protect the network from malicious or spam transactions.

## Conclusion
