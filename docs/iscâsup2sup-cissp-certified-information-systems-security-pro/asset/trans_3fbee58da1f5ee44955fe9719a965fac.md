
在本章前面的[图 6.1](#c06.xhtml#figure6-1)质询-响应协议示例中，使用了一种简单的置换密码来反转消息的字母顺序，使得 `apple` 变成了 `elppa`。置换密码可以比这复杂得多。例如，你可以使用关键字执行 `列式置换`。在下面的示例中，我们尝试使用密钥 `attacker` 加密消息“The fighters will strike the enemy bases at noon”（战斗机将在中午袭击敌方基地）。第一步是获取关键字的字母并按字母顺序给它们编号。首次出现的字母 `A` 获得值 1；第二次出现的编号为 2。序列中的下一个字母 `C` 编号为 3，以此类推。这产生了以下序列：

```
A T T A C K E R
1 7 8 2 3 5 4 6
```

接下来，将消息的字母按顺序写在关键字字母的下方：

```
A T T A C K E R
1 7 8 2 3 5 4 6
T H E F I G H T
E R S W I L L S
T R I K E T H E
E N E M Y B A S
E S A T N O O N
```

最后，发送者通过向下读取每一列来加密消息；读取列的顺序对应于第一步中分配的数字。这产生了以下密文：

```
T E T E E F W K M T I I E Y N H L H A O G L T B O T S E S N H R R N S E S I E A
```

在另一端，接收者使用密文和相同的关键字重建八列矩阵，然后只需跨行读取明文消息即可。

### 替换密码

`替换密码` 使用加密算法将明文消息的每个字符或比特替换为不同的字符。本章开头讨论的凯撒密码就是替换密码的一个很好的例子。现在你已经了解了一些密码学数学知识，我们将再次审视凯撒密码。回想一下，我们只是将消息中的每个字母向右移动三位来生成密文。然而，当我们到达字母表末尾且字母用尽时，遇到了一个问题。我们通过循环回到字母表开头来解决这个问题，因此明文字符 `Z` 变成了密文字符 `C`。

你可以通过将每个字母转换为其十进制等价物（其中 `A` 为 0，`Z` 为 25）用数学术语表示 `ROT3` 密码。然后你可以给每个明文字母加 3 来确定密文。你可以使用“密码学数学”部分讨论的模运算函数来处理循环问题。凯撒密码的最终加密函数如下：

```
C = (P + 3) mod 26
```

相应的解密函数如下：

```
P = (C - 3) mod 26
```

与置换密码一样，存在许多比本章示例更复杂的替换密码。多表替换密码在同一消息中使用多个字母表以阻碍解密工作。多表替换密码系统最著名的例子之一是 `维吉尼亚密码`。`维吉尼亚密码` 使用单个加密/解密表，如下所示：

```
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
B C D E F G H I J K L M N O P Q R S T U V W X Y Z A
C D E F G H I J K L M N O P Q R S T U V W X Y Z A B
D E F G H I J K L M N O P Q R S T U V W X Y Z A B C
E F G H I J K L M N O P Q R S T U V W X Y Z A B C D
F G H I J K L M N O P Q R S T U V W X Y Z A B C D E
G H I J K L M N O P Q R S T U V W X Y Z A B C D E F
H I J K L M N O P Q R S T U V W X Y Z A B C D E F G
I J K L M N O P Q R S T U V W X Y Z A B C D E F G H
J K L M N O P Q R S T U V W X Y Z A B C D E F G H I
K L M N O P Q R S T U V W X Y Z A B C D E F G H I J
L M N O P Q R S T U V W X Y Z A B C D E F G H I J K
M N O P Q R S T U V W X Y Z A B C D E F G H I J K L
N O P Q R S T U V W X Y Z A B C D E F G H I J K L M
O P Q R S T U V W X Y Z A B C D E F G H I J K L M N
P Q R S T U V W X Y Z A B C D E F G H I J K L M N O
Q R S T U V W X Y Z A B C D E F G H I J K L M N O P
R S T U V W X Y Z A B C D E F G H I J K L M N O P Q
S T U V W X Y Z A B C D E F G H I J K L M N O P Q R
T U V W X Y Z A B C D E F G H I J K L M N O P Q R S
U V W X Y Z A B C D E F G H I J K L M N O P Q R S T
V W X Y Z A B C D E F G H I J K L M N O P Q R S T U
W X Y Z A B C D E F G H I J K L M N O P Q R S T U V
X Y Z A B C D E F G H I J K L M N O P Q R S T U V W
Y Z A B C D E F G H I J K L M N O P Q R S T U V W X
Z A B C D E F G H I J K L M N O P Q R S T U V W X Y
```

请注意，该表只是在主标题下重复书写字母表（26 次），每次移动一个字母。你需要一个密钥来使用 `维吉尼亚` 系统。例如，密钥可以是 `secret`。然后，你将执行以下加密过程：

1.  写出明文。
2.  在下方写出加密密钥，根据需要重复密钥多次，以建立一行与明文长度相同的文本。
3.  将每个字母位置从明文转换为密文。
    1.  找到由第一个明文字符（`a`）标记的列。
    2.  接着，找到由密钥第一个字符（`s`）标记的行。
    3.  最后，找到这两者的交点，并记下那里出现的字母（`s`）。这是该字母位置的密文。
4.  对明文版本中的每个字母重复步骤 1 到 3。

| 明文： | | a t t a c k a t d a w n |
| --- | --- | --- |
| 密钥： | | s e c r e t s e c r e t |
| 密文： | | s x v r g d s x f r a g |

虽然多表替换可以防止直接频率分析，但它容易受到一种称为 `周期分析` 的二阶频率分析形式的攻击，这是一种基于密钥重复使用的频率检查。

### 一次性密码本

`一次性密码本` 是一种极其强大的替换密码类型。一次性密码本为明文消息的每个字母使用不同的替换字母表。它们可以用以下加密函数表示，其中 `K` 是用于将明文字母 `P` 加密为密文字母 `C` 的加密密钥：

```
C = (P + K) mod 26
```

通常，一次性密码本被写成一系列很长的数字，以便代入该函数。

一次性密码本的巨大优势在于，如果使用得当，它们是一种无法破解的加密方案。不存在重复的字母替换模式，使得密码分析工作变得毫无用处。然而，必须满足几个要求以确保算法的完整性。

*   一次性密码本必须是随机生成的。使用短语或书中的一段文字会引入密码分析师可能破解密码的可能性。
*   一次性密码本必须在物理上受到保护，防止泄露。如果敌人拥有密码本的副本，他们可以轻松解密加密消息。
*   每个一次性密码本只能使用一次。如果重复使用密码本，密码分析师可以比较使用相同密码本加密的多条消息的相似性，并可能确定所使用的密钥值。
*   密钥长度必须至少与待加密的消息一样长。这是因为密钥的每个字符仅用于编码消息的一个字符。

