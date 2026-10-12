

# 交易

例如，*[图 4.2](#c04.xhtml#fig4_2)* 展示了一个执行 Plutus 验证器脚本的交易：

[https://preprod.cexplorer.io/tx/99c529355ebd1f410517457b6ff04e66c2de28b8667b9428ec232e03efa22c29](https://preprod.cexplorer.io/tx/99c529355ebd1f410517457b6ff04e66c2de28b8667b9428ec232e03efa22c29)

![](images/Figure-4.2.jpg)

**图 4.2：** 交易示例

提交到网络的该交易的 **CBOR** 十六进制格式如下：

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

当我们使用 [https://cbor.nemo157.com/](https://cbor.nemo157.com/) 将其解码为诊断格式时，可以看到交易详情，如 *[图 4.3](#c04.xhtml#fig4_3)* 和 *[4.4](#c04.xhtml#fig4_4)* 所示。 *[图 4.3](#c04.xhtml#fig4_3)* 显示了该交易的 UTXO 输入、输出以及所需签名：

![](images/Figure-4.3.jpg)

**图 4.3：** CBOR 交易第 1 部分

*[图 4.4](#c04.xhtml#fig4_4)* 显示了所需的抵押品、公钥、Redeemer（赎回者）以及 Plutus 脚本见证。该交易不包含辅助数据或元数据，且交易有效性标志设置为 true。

![](images/Figure-4.4.jpg)

**图 4.4：** CBOR 交易第 2 部分

## Redeemer（赎回者）

要获得 Redeemer 的人类可读版本，我们需要将十六进制 ByteString 转换为 UTF-8 字符串。然而，Plutus 在脚本执行期间将直接使用 ByteString。以下是使用 `xxd` 将十六进制编码的 ByteString 转换为普通字符串的示例：

```
$ echo 48656c6c6f2c20576f726c6421 | xxd -p -r
$ Hello, World!
```

## Plutus 脚本

Plutus 脚本经过双重编码（CBOR + flat），这意味着我们需要反序列化两次才能将其转换为 UPLC。因此，第一步是使用 CBOR 解码器对其进行解码，[^(15)](#c04.xhtml#ftn15) 并将其保存到名为 `plutus.flat` 的文件中：

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

接下来，我们需要使用 Aiken 实用工具将其从十六进制转换为 UPLC 以进行解码：

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

## Datum（数据项）

接下来，我们将使用 `cexplorer.io` 查看 *[图 4.5](#c04.xhtml#fig4_5)* 中的 Datum：[^(16)](#c04.xhtml#ftn16)

![](images/Figure-4.5.jpg)

**图 4.5：** Datum 示例

*[图 4.5](#c04.xhtml#fig4_5)* 中的 Datum 是一个内联 Datum，因此该值存储在链上，并锁定在我们想要花费的 UTXO 上。如果我们查看该 UTXO，将看到该值以 CBOR 十六进制格式编码：

`d8799f581c6d04be153546d63c8a33e0c11ec44cf790803f31c2f893fc24152953ff`

当我们解码 Datum 的 CBOR 十六进制值时，会得到以下字节数组输出：

```
121_0([_
h'6d04be153546d63c8a33e0c11ec44cf790803f31c2f893fc24152953',
])
```

在本例中，Datum 值代表一个公钥哈希。

## Plutus 执行预算

查看 *[图 4.4](#c04.xhtml#fig4_4)* 中交易的 Redeemer 见证，我们会注意到附带的 Plutus 脚本有一个执行预算：

`[30485_1, 10332844_2]`

这些值指的是内存和 CPU（步数）执行单元，它们在 Plutus 账本规范中定义：

`ex_units = [mem: uint, steps: uint]`

`mem` 和 `steps` 随交易一起计算并提交，然后由 Plutus 核心求值器在脚本执行期间进行验证。如果在脚本执行期间任一值超出最大限制，则会引发错误：

```
Error: The budget when the machine terminated was:\n({ cpu: -84834\n| mem: 17553\n}
```

在本例中，`cpu/steps` 值超限并导致负数。结果，执行被终止，验证失败。要计算给定 Plutus 脚本的 `mem` 和 `cpu/step` 成本，会使用 `cost model`（成本模型）[^(17)](#c04.xhtml#ftn17) 来映射每个 Plutus 操作的 `execution cost`（执行成本）。成本模型位于网络协议参数中，并可通过网络更新随时间变化。要查看 `protocol parameters`（协议参数），可以使用 `cardano-cli` 工具：

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

除其他内容外，协议参数还指定了每个 Plutus 操作的执行成本、每笔交易的最大 `memory` 和 `steps` 单元，以及最大整体交易大小（`maxTxSize`），单位为 KB。

## 抵押品

我们将要讨论的最后一个主题是交易中包含的抵押品。抵押品是一小笔 Lovelace（1.5 × 交易费），如果发生第 2 阶段 Plutus 脚本失败，将会用到它。[^(18)](#c04.xhtml#ftn18) 抵押品输入中剩余的零钱将退还给用户，称为 **抵押品返还**。然而，Plutus 脚本评估通常在提交到网络之前在本地完成。这将捕获并防止无效 Plutus 脚本的提交。抵押品的作用是帮助保护网络免受恶意或垃圾交易的侵害。

## 结论

