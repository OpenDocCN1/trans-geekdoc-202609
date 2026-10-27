
我们将利用三字母组合 THE 的高频出现来为各列排序。我们从列1↔16开始。查看位置12和18时，会发现 E 与列10↔15中 T 的位置相匹配。我们预期在这两列之间会出现一列，其位置12和18上是明文 H。我们寻找一列，使位置12和18的字母对相匹配，于是得到两种可能：11↔17 和 18↔14。可以对它们分别进行考虑。

| 情况1 |  |  | 情况2 |  |  |
|---|---|---|---|---|---|
| 10↔15 | 11↔17 | 1↔16 | 10↔15 | 18↔14 | 1↔16 |
| <u>E</u> | XD | AG | <u>E</u> | <u>E</u> | AG |
| XF | FG | <u>E</u> | XF | <u>E</u> | <u>E</u> |
| FD | <u>E</u> | DA | FD | DA | DA |
| XF | XX | <u>E</u> | XF | DA | <u>E</u> |
| AF | <u>E</u> | DA | AF | <u>T</u> | DA |
| FG | AF | XF | FG | FA | XF |
| <u>E</u> | GG | DG | <u>E</u> | DG | DG |
| DG | GG | DA | DG | FF | DA |
| GG | <u>T</u> | DA | GG | <u>E</u> | DA |
| DG | DF | XD | DG | <u>T</u> | XD |
| <u>E</u> | AF | DA | <u>E</u> | <u>T</u> | DA |
| <u>T</u> | FA | <u>E</u> | <u>T</u> | GA | <u>E</u> |
| <u>E</u> | FG | <u>E</u> | <u>E</u> | GA | <u>E</u> |
| DG | AA | DG | DG | AF | DG |
| <u>T</u> | XF | DF | <u>T</u> | <u>E</u> | DF |
| XF | FG | DG | XF | <u>T</u> | DG |
| <u>E</u> | GA | XF | <u>E</u> | <u>E</u> | XF |
| <u>T</u> | FA | <u>E</u> | <u>T</u> | GA | <u>E</u> |
| DA | AA | DF | DA | GA | DF |
| <u>E</u> | <u>T</u> | DG | <u>E</u> | DG | DG |
| AF | XF | DF | AF | DA | DF |
| AF | <u>E</u> | XF | AF | GA | XF |
| DF | XD | <u>T</u> | DF | FA | <u>T</u> |
| FG | AA | DG | FG | FF | DG |
| FF | DA | GA | FF | GD | GA |
| <u>E</u> | FG | DG | <u>E</u> | <u>E</u> | DG |
| DA | FD | <u>E</u> | DA | DA | <u>E</u> |
| DF | DG | GA | DF | XF | GA |
| FF | FF | <u>T</u> | FF | GD | <u>T</u> |
| GD | DG | XF | GD | DA | XF |
| XF | DF | <u>T</u> | XF | GG | <u>T</u> |
| GA | FF | DA | GA | <u>T</u> | DA |
| DF | DG | FA | DF | FA | FA |
| <u>T</u> | <u>E</u> | GG | <u>T</u> | <u>E</u> | GG |
| 如果情况1正确，则 FA = H。 |  |  | 如果情况2正确，则 GA = H。 |  |  |

目前，我们还没有足够的信息来判断哪一种是正确的，因此我们开始进一步探究每一种可能。在情况1中，我们寻找一列放在我们正在构建的链条开头，使得某个 T 能与列10↔15中的 E 相连。共有四个列可以做到这一点：7↔4、12↔20、13↔19 和 18↔14。起初，7↔4看起来最好，因为它给出两对 T-E，而其他列只给出一对 T-E。然而，没有哪一列能放在7↔4和10↔15之间，从而在每对 T-E 之间放入 H。请注意，在情况1中，H 被认定为 FA。因此，仅找到一列在这两个位置具有相同字母对是不够的；我们还要求这对字母是 FA。（12↔20在其中一个位置提供了 FA，但这样一来，另一对 T-E 中间就会是别的字母，这也是可能的……）现在假设12↔20接续到情况1。那么我们会希望某个其他列在位置17处有一个 FA（用于填入 H），但我们任何地方都找不到。接着看13↔19，我们会希望位置11处有 FA。列3↔9提供了这一点。最后一种情况也是如此：对于18↔14，我们希望位置11处有 FA，列3↔9也提供了这一点。因此，共有三种合理的可能，其中后两种略占优势，因为它们不需要在任何 T 和 E 之间出现非 H 字母。我们将这最后两种可能作为情况1的子情况来考察。

| 情况1a | | | | | 情况1b | | | | |
|---|---|---|---|---|---|---|---|---|---|
| 13↔19 | 3↔9 | 10↔15 | 11↔17 | 1↔16 | 18↔14 | 3↔9 | 10↔15 | 11↔17 | 1↔16 |
| XX | AD | E | XD | AG | E | AD | E | XD | AG |
| FG | FD | XF | FG | E | E | FD | XF | FG | E |
| T | DD | FD | E | DA | DA | DD | FD | E | DA |
| FA | FA | XF | XX | E | DA | FA | XF | XX | E |
| E | DG | AF | E | DA | T | DG | AF | E | DA |
| T | E | FG | AF | XF | FA | E | FG | AF | XF |
| FF | DD | E | GG | DG | DG | DD | E | GG | DG |
| AG | T | DG | GG | DA | FF | T | DG | GG | DA |
| T | DF | GG | T | DA | E | DF | GG | T | DA |
| GD | FA | DG | DF | XD | T | FA | DG | DF | XD |
| T | FA | E | AF | DA | T | FA | E | AF | DA |
| FG | E | T | FA | E | GA | E | T | FA | E |
| DG | AF | E | FG | E | GA | AF | E | FG | E |
| XF | E | DG | AA | DG | AF | E | DG | AA | DG |
| DX | DG | T | XF | DF | E | DG | T | XF | DF |
| DF | E | XF | FG | DG | T | E | XF | FG | DG |
| DG | GF | E | GA | XF | E | GF | E | GA | XF |
| AG | FA | T | FA | E | GA | FA | T | FA | E |
| E | GG | DA | AA | DF | GA | GG | DA | AA | DF |
| DA | FF | E | T | DG | DG | FF | E | T | DG |
| DA | GG | AF | XF | DF | DA | GG | AF | XF | DF |
| DG | T | AF | E | XF | GA | T | AF | E | XF |
| T | DG | DF | XD | T | FA | DG | DF | XD | T |
| FF | XF | FG | AA | DG | FF | XF | FG | AA | DG |
| XF | GF | FF | DA | GA | GD | GF | FF | DA | GA |
| FG | XX | E | FG | DG | E | XX | E | FG | DG |
| DF | T | DA | FD | E | DA | T | DA | FD | E |
| XD | DG | DF | DG | GA | XF | DG | DF | DG | GA |
| AD | XF | FF | FF | T | GD | XF | FF | FF | T |
| FA | FF | GD | DG | XF | DA | FF | GD | DG | XF |
| DA | AF | XF | DF | T | GG | AF | XF | DF | T |
| GA | DG | GA | FF | DA | T | DG | GA | FF | DA |
| T | XF | DF | DG | FA | FA | XF | DF | DG | FA |
| FD | GF | T | E | GG | E | GF | T | E | GG |

| 13↔19 | 18↔14 | 3↔9 | 10↔15 | 11↔17 | 1↔16 | 6↔5 |
|---|---|---|---|---|---|---|
| XX | E | AD | E | XD | AG | DF |
| FG | E | FD | XF | FG | E | XF |
| T | DA | DD | FD | E | DA | FD |
| FA | DA | FA | XF | XX | E | XF |
| E | T | DG | AF | E | DA | FG |
| T | FA | E | FG | AF | XF | GG |
| FF | DG | DD | E | GG | DG | DD |
| AG | FF | T | DG | GG | DA | DF |
| T | E | DF | GG | T | DA | GG |
| GD | T | FA | DG | DF | XD | XF |
| T | T | FA | E | AF | DA | DD |
| FG | GA | E | T | FA | E | FF |
| DG | GA | AF | E | FG | E | FF |
| XF | AF | E | DG | AA | DG | FF |
| DX | E | DG | T | XF | DF | GG |
| DF | T | E | XF | FG | DG | T |
| DG | E | GF | E | GA | XF | DF |
| AG | GA | FA | T | FA | E | FD |
| E | GA | GG | DA | AA | DF | T |
| DA | DG | FF | E | T | DG | XF |
| DA | DA | GG | AF | XF | DF | T |
| DG | GA | T | AF | E | XF | DF |
| T | FA | DG | DF | XD | T | FA |
| FF | FF | XF | FG | AA | DG | FF |
| XF | GD | GF | FF | DA | GA | E |
| FG | E | XX | E | FG | DG | AA |
| DF | DA | T | DA | FD | E | DF |
| XD | XF | DG | DF | DG | GA | AA |
| AD | GD | XF | FF | FF | T | FA |
| FA | DA | FF | GD | DG | XF | AF |
| DA | GG | AF | XF | DF | T | FA |
| GA | T | DG | GA | FF | DA | DF |
| T | FA | XF | DF | DG | FA | XF |
| FD | E | GF | T | E | GG | FX |

我们本可以继续尝试把剩下的三列放入已部分恢复的密钥中，但在现阶段没有很强的理由再做一次放置，因此我们把这些剩余列作为一个整体来考虑。三个对象共有六种排列顺序，我们很快注意到，其中两种排列，即12↔20 8↔2 7↔4和7↔4 8↔2 12↔20，会使THE出现（分别位于位置16和20）。见下表。

| 12↔20 | 8↔2 | 7↔4 | *对比* | 7↔4 | 8↔2 | 12↔20 |
|---|---|---|---|---|---|---|
| DG | FA | XF |  | XF | DG | FA |
| <u>T</u> | DA | FD |  | FD | <u>T</u> | DA |
| FF | DG | GA |  | GA | FF | DG |
| FF | <u>E</u> | AA |  | AA | FF | <u>E</u> |
| <u>T</u> | DA | DF |  | DF | <u>T</u> | DA |
| XF | DF | DA |  | DA | XF | DF |
| <u>E</u> | AF | GD |  | GD | <u>E</u> | AF |
| DD | DG | GF |  | GF | DD | DG |
| <u>T</u> | DG | DF |  | DF | <u>T</u> | DG |
| DA | XF | DF |  | DF | DA | XF |
| AD | DA | AG |  | AG | AD | DA |
| GF | DA | AG |  | AG | GF | DA |
| DG | GA | <u>T</u> |  | <u>T</u> | DG | GA |
| GD | XF | XD |  | XD | GD | XF |
| FF | AF | XF |  | XF | FF | AF |
| <u>T</u> | FA | <u>E</u> |  | <u>E</u> | <u>T</u> | FA |
| <u>T</u> | DA | FD |  | FD | <u>T</u> | DA |
| GG | DD | FF |  | FF | GG | DD |
| DG | <u>E</u> | GF |  | GF | DG | <u>E</u> |
| FA | <u>E</u> | <u>T</u> |  | <u>T</u> | FA | <u>E</u> |
| AF | XF | XD |  | XD | AF | XF |
| FA | <u>E</u> | FF |  | FF | FA | <u>E</u> |
| GA | DF | DA |  | DA | GA | DF |
| <u>E</u> | GF | <u>E</u> |  | <u>E</u> | <u>E</u> | GF |
| FF | GA | <u>T</u> |  | <u>T</u> | FF | GA |
| GG | DD | DA |  | DA | GG | DD |
| DG | FF | FF |  | FF | DG | FF |
| DG | <u>T</u> | XF |  | XF | DG | <u>T</u> |
| <u>E</u> | XF | FG |  | FG | <u>E</u> | XF |
| XF | <u>T</u> | GA |  | GA | XF | <u>T</u> |
| XF | XD | DA |  | DA | XF | XD |
| <u>E</u> | FF | DG |  | DG | <u>E</u> | FF |
| XD | <u>E</u> | FG |  | FG | XD | <u>E</u> |
| GG | <u>E</u> | FX |  | FX | GG | <u>E</u> |

我们可以单独更仔细地考察这两种可能，但也可以看看它们如何适配到已部分组装的密钥上；例如，把12↔20 8↔2 7↔4放在部分密钥的开头，会得到一些不错的结果。
