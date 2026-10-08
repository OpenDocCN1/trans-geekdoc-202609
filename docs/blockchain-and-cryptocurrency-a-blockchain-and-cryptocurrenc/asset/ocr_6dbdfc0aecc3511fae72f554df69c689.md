valid or not. Because it is also impossible to predict what the nonce will be, it also acts as a proof that the miner has indeed achieved Proof-of-Work.

Calculation of a valid hash is as follows (based on block #540909):

The formula to calculate the current target of the block is

Current target = Maximum target / Difficulty

Maximum target is

```
0x00000000FFFFFFFF000000000000000000000000000000000000000000000
```

This is a hexadecimal number. After conversion to a decimal number, the maximum target is

```
269599466715063979466701508701963067363714422540572841103610249215
```

Difficulty is (as given in the block)

```
701999231177.17
```

Therefore, the current target is

```
269599466715063979466701508701963067363714422540572841103610249215/701999231177.17
```

```
= 3.84089×10^54
```

The hash of the block

```
00000000000000000000ef17668e407e78c5a247f731b1138ad16f5bf79f1c0d
```

Converted to a decimal number, the value is

```
89454716205495239529548710168460626470818561584946189
```