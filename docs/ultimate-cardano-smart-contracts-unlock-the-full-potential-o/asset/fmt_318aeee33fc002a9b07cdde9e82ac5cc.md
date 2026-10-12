
This will generate the following output when running the Plutus script.

`INFO (ticket:13:10) tx.minted: lovelace: 0`

`INFO (ticket:13:10) 0af9021a0…d93cba53ecf15.54687265616420546f6b656e: 2`

The line number of the Helios script is also shown in the `INFO` brackets. The `trace()` function can also be used to emit an output to test a boolean condition.

`value_minted.contains_policy(mph).trace("TTP3: ")`

This will generate an output of the evaluation when the Plutus script is executed.

`INFO (ticket:33:52) TTP3: true`

If the Smart Contract fails and returns a false boolean value, a stack trace is generated in [Figure 12.1](#c12.xhtml#fig12_1), which allows you to see where and why it failed.

![](images/Figure-12.1.jpg)

**Figure 12.1:** Helios `trace()`

# Aiken

When you build an Aiken script you can specify what type of tracing you want to include, as illustrated in [Figure 12.2](#c12.xhtml#fig12_2).

![](images/Figure-12.2.jpg)

**Figure 12.2:** Aiken Build Trace Options

To emit `print` statements, use the `trace` function.

`trace "redeemer message: "`

`trace string.from_bytearray(msg)`

To emit a trace when a condition is evaluated to be false, you use the `?` operator.

`some_expression_a? && some_expression_b?`

In this example, it can help isolate what expression is failing because if either condition evaluates to false, the entire script will fail.

An example of emitting `trace` information is shown in [Figure 12.3](#c12.xhtml#fig12_3).

![](images/Figure-12.3.jpg)

**Figure 12.3:** Aiken Traces

The validator script is compiled using the `-t` flag.

```
$ aiken build -t verbose
```

The following output is generated when the script is executed when the validator fails, as shown in [Figure 12.4](#c12.xhtml#fig12_4).

![](images/Figure-12.4.jpg)

**Figure 12.4:** Aiken Traces

# CBOR Analysis

As we learned in previous chapters, a Plutus script is compiled into `UPLC` and converted into the `CBOR` format. We typically inspect `CBOR` using the hexadecimal representation of the underlying bytes. This binary format is stored and executed on-chain, so looking at this when troubleshooting is helpful.

# Helios

Helios has excellent support for `CBOR` serialization and deserialization and you can easily view any part of the transaction in `CBOR` format.

```
await tx.finalize(networkParams, alice.address, utxos);

console.log("tx final: ", tx.toCborHex());
```

You can also easily deserialize a transaction or any transaction component back into a Helios object using `fromCbor()`.

```
const txCbor = tx.toCborHex();

const newTx = Tx.fromCbor(txCbor);

console.log("tx from cbor: ", newTx.dump());
```

# Lucid + Aiken

Aiken provides the `cbor.diagnostic()` function to help generate `CBOR` that can be used for troubleshooting. To print out the `CBOR` representation of the `msg` in [Figure 12.3](#c12.xhtml#fig12_3), we can use:

`trace cbor.diagnostic(msg)`

This will generate the `CBOR` representation of a bytearray:

`h'596F7520526F636B21'`

We can also print out the `CBOR` representation of the entire transaction easily using Lucid.

```
const signedTx = await tx.sign().complete();

console.log("signedTx: ", signedTx.toString());
```

The `CBOR` output in hexadecimal can then be used in [https://cbor.nemo157.com/](https://cbor.nemo157.com/) to inspect and analyze the `CBOR` elements. Once you have the `CBOR` elements, you can compare them against the formal `CDDL` specifications[¹](#c12.xhtml#ftn1) to see if there are any discrepancies. As we can recall from [Chapter 5, Transactions](#c05.xhtml), the `CDDL` is the Concise Data Definition Language used to describe the structure of a transaction.

# Execution Budget Errors

If you have not encountered execution budget errors, you will eventually.

```
CekError An error has occurred: User error:
The machine terminated part way through evaluation due to overspending the budget.
The budget when the machine terminated was:
({ cpu: -447572
| mem: 5302
}
```

Execution budget errors are typically detected during transaction construction, so the off-chain transaction builder framework generates a more user-friendly error. The preceding error *can also* occur when the off-chain framework has not supplied the correct budget values in the redeemer for each Plutus script being executed. This will result in an execution budget mismatch, which the Cardano node rejects.

There is another scenario where the order of the inputs is different between what is executed locally and what is executed on the Node. The order of the inputs will be re-ordered to follow the canonical `CBOR` order format.[²](#c12.xhtml#ftn2) However, the ordering of the *outputs* will remain the same as when they were created during off-chain transaction construction. This is why it is preferred to inspect outputs rather than inputs. For more information on this subject, please refer to CIP-0021[³](#c12.xhtml#ftn3), which documents the canonical ordering and how it relates to hardware wallets and tokens.

In the previous chapter, we showed how to include CPU and memory units in your testing so you can keep track of a transaction’s execution budget. Remember that a Plutus script is resource-constrained to minimize the hardware requirements for the node operators. This, in turn, promotes decentralization since anyone can run a node without requiring specialized hardware or infrastructure.

When you trigger a CPU or memory execution limit error using Helios, the error message will be displayed, as shown in [Figure 12.5](#c12.xhtml#fig12_5). It indicates what was exceeded and the current values of the protocol parameters during the evaluation. This is helpful so you can isolate exactly what contributes to the `cpu` and `mem` units and tune accordingly.

![](images/Figure-12.5.jpg)

**Figure 12.5:** Helios Execution Units Error

Protocol parameters can be changed by network updates, so it is best to query the network to get the current value. This can be done using a tool like [https://cexplorer.io/params](https://cexplorer.io/params) or `cardano-cli`, as shown in [Figure 12.6](#c12.xhtml#fig12_6).

![](images/Figure-12.6.jpg)

**Figure 12.6:** Network Protocol Parameters

In general, the following guidelines will help you optimize your Plutus script:

*   Compile Helios scripts with `optimize=true` and `aiken build` without any traces or logging levels.
*   Avoid unnecessary data conversions and work directly with the serialized data structures.
*   Avoid iterating through the list of UTXO inputs if possible and focus on specific UTXO outputs.
*   If you encounter script size or CPU and memory execution limit errors, split out validator logic across multiple scripts using separate transactions.
*   Use reference scripts to reduce the transaction size.

# Compiler Errors

Both Helios and Aiken handle errors well during script compilation. A typical error generated using Helios creates a stack trace that shows you exactly what and where the error occurred.

Here is an example of invalid syntax for assigning a variable using Helios.

`tx = ctx.tx;`

[Figure 12.7](#c12.xhtml#fig12_7) shows the error message, which states the type of error, the script name, and the line number.

![](images/Figure-12.7.jpg)

**Figure 12.7:** Helios Builder Error

Here is an example of an invalid variable assignment for Aiken.

`let { transaction, purpose } = context`

This will generate an error and indicate the line number and reason for the error (refer to [Figure 12.8](#c12.xhtml#fig12_8)).

![](images/Figure-12.8.jpg)

**Figure 12.8:** Aiken Builder Error

# Transaction Builder Errors
