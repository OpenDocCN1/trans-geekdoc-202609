| Multiply and assign | | | |
|---|---|---|---|
| Divide and assign / | / | a /= b | a = a/b |
| Divide and assign the integer part //= | //= | a //= b | a = a/b |
| Module and assign %= | %= | a %= b | a = a%b |
| Power and assign **= | **= | a **= b a | a = a**b |

| A | B | A or B | A and B | Not A |
|---|---|---|---|---|
| False | False | False | False | True |
| False | True | True | False | True |
| True | False | True | False | False |
| True | True | True | True | False |

Equals:

| A | B | A or B | A and B | Not A |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 1 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 1 | 0 | 0 |
| 1 | 1 | 1 | 1 | 0 |

For example,

```
>>> A = True
>>> type(A)
<class 'bool'>
>>> B = False
>>> A or B
True
```