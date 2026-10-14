

## 标准比特币脚本——P2MS

P2MS 代表 **Pay-2-Multisig**。该脚本允许使用多重签名来访问锁定的比特币。

脚本如下所示：

**ScriptPubKey:** `OP_n <Public Key 1><Public Key 2>…<Public Key m>OP_m<Multisig>`

**ScriptSig:** `OP_0 <Signature 1><Signature 2>… <Signature n>`

在 2-of-3 多重签名中，需要三个签名中的两个才能索取由 `scriptPubKey` 锁定的资金。

这意味着在创建交易时，我们需要在脚本中包含多个公钥。这有以下缺点：

1. 交易将比普通 P2PKH 脚本消耗更多字节，因此发送方必须支付更高的交易费。
2. 发送方需要通过获取多个公钥来构建复杂脚本，即使只是发送给单个接收者。这给发送方带来了额外负担。
3. 如果量子计算机能够利用 Shor 算法破解私钥-公钥加密体制，公钥可能不再安全。

2012 年，P2SH 作为软分叉被引入，解决了上述缺点，因此我们不再深入探讨该脚本。

## 标准比特币脚本——P2SH

P2SH 代表 **Pay-2-Script-Hash**。顾名思义，哈希中嵌入了一个脚本，必须满足该脚本才能进行支付。这主要用于允许使用多重签名来访问比特币。它于 2012 年作为软分叉引入。

P2SH 脚本用脚本哈希替换了多重签名脚本，因此发送方无需为矿工打包交易支付额外费用。

对于 P2SH，`scriptSig` 为：

```
<Signatures> <Redeem Scripts>
```

而 `scriptPubKey` 为：

```
OP_HASH160 <20-byte Redeem Script hash> OP_EQUAL
```

2-of-3 多重签名的赎回脚本如下：

```
<2><Public Key 1><Public Key 2><Public Key 3><3><Multisig>
```

在 P2SH 中，需要执行两个脚本，即 `scriptPubKey` 和赎回脚本，以及给定的签名列表。这是一种特殊脚本，执行方式略有不同。在这种情况下，会维护堆栈的副本，一旦 `scriptPubKey` 执行完毕，赎回脚本开始执行。

由于 P2SH 脚本中的 `scriptPubKey` 包含脚本的 20 字节哈希，我们可以将复杂脚本隐藏在哈希中。发送方不需要知道索取资金的规则；他们只会看到一个普通的地址来转账。这极大地简化了流程，同时为索取锁定的比特币施加了复杂的规则。这些复杂规则作为各方之间的合约运作。这些合约催生了智能合约，我们将在下一章详细了解。

下图解释了 P2SH 的执行过程：

![](images/Figure-10.11.jpg)

**Figure 10.11:** P2SH execution

要编写验证 P2SH 交易输出签名的程序，我们需要能够识别 P2SH，因为它涉及三个连续的脚本执行。以下是三个执行脚本：

*   `OP_0 <signature 1> <signature 2> … <signature m> <Redeem Script>`
*   `OP_HASH160 <Redeem Script Hash> OP_EQUAL`
*   赎回脚本：`OP_m <Public Key 1> <Public Key 2> … <Public Key n> OP_n OP_MULTISIG`

对于 P2SH，签名预像保持不变，因此我们扩展了上一节 P2PKH 所涵盖的程序，以包含赎回脚本处理，并增加对 `OP_CHECKMULTISIG` 的处理。

```
g_pushnumber = range(0x51, 0x61) # excludes 0x61

def opEqual():
    v1 = st.pop()
    v2 = st.pop()
    if v1 == v2:
        st.append(b'\x01')
    else:
        st.append(b'\x00')

def opNum(b: int):
    num = b - 0x50
    st.append(bytes([num]))

def opCheckMultisig(script_b: bytes, inp_index: int, tx: dict):
    pubkey_cnt = int.from_bytes(st.pop(), byteorder='little')
    pubkey_l = [st.pop() for i in range(pubkey_cnt)][::-1]
    sig_cnt = int.from_bytes(st.pop(), byteorder='little')
    sig_l = [st.pop() for i in range(sig_cnt)][::-1]
    sig_index = 0
    for pubkey_b in pubkey_l:
        v = sigcheck(sig_l[sig_index], pubkey_b, script_b, inp_index, tx)
        if v == b'\x01':
            sig_index += 1
        if sig_index == sig_cnt:
            break
    # convert True/False to b'\x01' or b'\x00'
    b = bytes([int(sig_index == sig_cnt and v == b'\x01')])
    st.append(b)
```

**Program 10.9:** Bitcoin script operations for P2SH

以下程序用于识别是否正在执行 P2SH 脚本。此方法在 `scriptSig` 执行后调用：

```
def checkWrappedMultisig(st):
    script_b = st[-1]
    val = script_b[-2]
    if bytes([script_b[-1]]) == b'\xae' and val in g_pushnumber:
        return True
    else:
        return False
```

**Program 10.10:** Identify P2SH script

以下是处理额外操作码的更新后的 `execScript` 方法：

```
def execScript(script_b: bytes, inp_index: int, tx: dict):
    l = len(script_b)
    script_m = bytes2Mmap(script_b)
    while script_m.tell() < l:
        v = script_m.read(1)
        b = int.from_bytes(v, byteorder='little')
        if b == 0x00:
            pass
        elif b < 0x4f:
            script_m.seek(-1, 1)
            b = decodePushdata(script_m)
            d = script_m.read(b)
            pushdata(d)
        elif v == b'\x76':
            opDup()
        elif v == b'\xa9':
            opHash160()
        elif b in g_pushnumber:
            opNum(b)
        elif v == b'\x87':
            opEqual()
        elif v == b'\x88':
            opEqualVerify()
        elif v == b'\xac':
            opCheckSig(script_b, inp_index, tx)
        elif v == b'\xae':
            opCheckMultisig(script_b, inp_index, tx)
```

**Program 10.11:** P2SH script execution

以下方法执行 P2SH 脚本验证：

```
def verifyScript(tx: dict, inp_index: int):
    isP2SH = False
    scriptsig_b = getScriptSig(tx, inp_index)
    execScript(scriptsig_b, inp_index, tx)
    prev_scriptpubkey_b = getPrevScriptPubKey(tx, inp_index)
    if checkWrappedMultisig(st) == True:
        redeemscript_b = st[-1]
        isP2SH = True
    execScript(prev_scriptpubkey_b, inp_index, tx)
    status = st.pop()
    if status == b'\x01':
        print('1st Script succeeded')
    elif status == b'\x01':
        print('1st Script Failed')
    else:
        print('1st Invalid state')
    if isP2SH == True:
        execScript(redeemscript_b, inp_index, tx)
        status = st.pop()
        if status == b'\x01':
            print('2nd Script succeeded')
        elif status == b'\x01':
            print('2nd Script Failed')
        else:
            print('2nd Invalid state')
```

**Program 10.12:** P2SH verification method

我们按如下方式调用上述方法来验证交易 scriptSig：

```
if __name__ == '__main__':
    txid_s = '8b3e54e345d0b3e9278a27f1ab2aa2566aba8cbe7cf44b9aa1836c9d0fcc2625'
    inp_index = 0
    txid_b = bytes.fromhex(txid_s)[::-1]
    tx = findTransaction(txid_b, txindex_db_g)
    verifyScript(tx, inp_index)
```

既然你已经了解了交易如何验证，我们现在将创建交易，并将 `regtest` 比特币从一个地址转移到另一个地址。

## 构建交易

