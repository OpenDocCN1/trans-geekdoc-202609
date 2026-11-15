+   - A dictionary entry consisting of: name, opcode, and definition.
+   - Argument requirements include the argument count and their expected data types.
+   - An short alias or symbol for some of the more frequently used words.
+   - Either a postfix or prefix operation (most words are postfix).

During run-time, _epop_ checks that argument requirements are satisfied, helping to prevent errors. A useful diagnostic tool in that regard is the SEE word. An example of what SEE displays is shown here for the XOR word:

```
XOR ' SEE
XOR. Opcode: 191
0.0 RG5 opcode: 1. argc: 0
GT opcode: 14. argc: 2
SWAP opcode: 23. argc: 2
0.0 RG5 opcode: 1. argc: 0
GT opcode: 14. argc: 2
ADD opcode: 8. argc: 2
1 RG5 opcode: 1. argc: 0
EQ opcode: 13. argc: 2
```

Occasionally, errors arise when two or more unbound asynchronous words compete for the same data. To avoid this and to force synchronization, insert the SYNC operator, aliased as ";;". For example: