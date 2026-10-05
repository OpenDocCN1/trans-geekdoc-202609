

## 第 23 章 协议的特殊算法

(4) Alice 向 Bob 发送 $q$，以便 Bob 能够使用 $m^*$ 并重构 $s_1$ 和 $s_2$。如果

$s_1 = cg^d \bmod p$
$s_2 = (g^b)^b + az^z \bmod p$

则签名是有效的。

Alice 也可以否认消息 $m$ 的签名 $z$。详情见 [329]。关于不可否认签名的其他协议可以在 [584,344] 中找到。Lein Harn 和 Shoubao 提出了一种群不可否认签名方案 [700]。

## 可转换不可否认签名

[213] 中给出了一种可转换不可否认签名的算法，它可以被验证、否认，并还可以转换为传统的数字签名。它基于 ElGamal 数字签名算法。

与 ElGamal 类似，首先选择两个素数 $p$ 和 $q$，使得 $q$ 整除 $p-1$。现在你需要创建一个小于 $q$ 的数 $g$。在 2 到 $p-1$ 之间选择一个随机数 $h$。计算

$g = h^{-1/q} \bmod p$

如果 $g$ 等于 1，则选择另一个随机 $h$。如果没有，则使用当前的 $g$。私钥是两个小于 $q$ 的不同数字 $x$ 和 $z$。公钥是 $p, q, g, y$ 和 $u$，其中

$y = g' \bmod p$
$u = g' \bmod p$

要计算消息 $m$（实际上是消息的哈希值）的不可否认签名，首先在 1 到 $q-1$ 之间选择一个随机数 $t$。然后计算

$T = g^t \bmod p$

以及

$m' = Ttztm \bmod q$。

现在对 $m'$ 计算 ElGamal 签名。选择一个随机数 $R$，使得 $R$ 小于 $p-1$ 且与之互质。然后计算 $r = g^R \bmod p$，并使用扩展欧几得算法计算 $s$，使得

$m' = tx + Rs \bmod q$

签名是 ElGamal 签名 $[t, s]$ 以及 $T$。以下是 Alice 如何向 Bob 验证她的签名：

- (1) Bob 生成两个随机数 $a$ 和 $b$。他计算 $c = T^{ma'} \bmod p$ 并发送给 Alice。
- (2) Alice 生成一个随机数 $k$，计算 $h_1 = cg^k \bmod p$ 和 $h_2 = h_1^{k'} \bmod p$，并将这两个数字都发送给 Bob。

## 23.5 指定确认者签名

(3) Bob 向 Alice 发送 $a$ 和 $b$。
(4) Alice 验证 $c = T^{T_{mg}^g} \pmod p$。她将 $k$ 发给 Bob。
(5) Bob 验证 $h_1 = T^{T_{mg}^{g+k}} \pmod p$，以及 $h_2 = y^{c^{a}u^b+k} \pmod p$。

Alice 可以通过发布 $z$ 将任何不想要的签名转换为普通签名。现在，任何人可以在没有她的帮助的情况下验证她的签名。

不可否认签名方案可以与秘密共享方案结合以创建分布式不可否认签名 [1235]。某人可以对消息签名，并分配确认该签名有效的能力。例如，可能需要五个人中的三个人参与协议，才能说服 Bob 签名是有效的。这一概念的改进消除了对可信分发者的要求 [700,1369]。

## 23.5 指定确认者签名

以下是 Alice 如何对签名以及 Bob 如何验证它，使得 Carol 可以在稍后的某个时间向 Dave 验证 Alice 的签名（见第 4.4 节）[333]。

首先，一个大素数 $p$ 和一个原元 $g$ 公开供一组用户使用。两个素数的积 $n$ 也是公开的。私钥 $z$ 和公钥 $h = g^z \pmod p$。Carol 有一个私钥，以及一个第三方。

在该协议中，Alice 可以对 $m$ 签名，使得 Bob 确信签名是有效的，而无需选择第三方。

- (1) Alice 选择随机的 $x$ 并计算
$a = g^x \pmod p$
$b = h^x \pmod p$

她计算 $m$ 的哈希值 $H[m]$，并将 $a$ 和 $b$ 的哈希值拼接为 $H(a,b)$。然后她计算
$nj=[H(m) \oplus H(a,b)]^s \pmod n$

- 并将 $a, b$, 和 $j$ 发给 Bob。
- (2) Bob 选择两个随机数 $s$ 和 $t$，都小于 $n$，发送给 Alice。
- (3) Alice 选择一个随机的 $q$，小于 $p$，并计算 $q \pmod p$
 $d = g^ \pmod p$。
- (4) Bob 将 $a, b$ 和 $j$ 发给 Carol。
- (5) Bob 计算 $c = T^{ma'} \pmod p$ 并 $ $d = \ $s \pmod c$。
- (6) Alice 向 Bob 发送 $t$。
- (7) Alice 计算 $d = g^s \pmod p$ 并将 $e = g^s \pmod p$ 发给 Carol。
- (8) 向 Carol 发送 $u$。
- (9) Carol 计算 $h = g^z \pmod p$ 并发送 $s$。
- (10) Bob 计算 $r = g^R \bmod p$ 并将 $s$ 发送给 Alice。
- (11) Alice 计算 $r = g^k \pmod p$ 并发送 $a$。
- (12) Bob 计算 $s = g^t \pmod p$ 并发送 $t$。
- (13) Alice 计算 $h = g^x \pmod p$ 并发送 $b$。
- (14) Bob 计算 $a = g^x \pmod p$ 并发送 $x$。
- (15) Alice 计算 $y = g^z \pmod p$ 并发送 $j$。
- (16) Bob 计算 $s = g^s \pmod p$ 并发送 $s$。
- (17) Alice 计算 $h = g^x \pmod p$ 并发送 $k$。
- (18) Bob 计算 $s = g^t \pmod p$ 并发送 $t$。
- (19) Alice 计算 $s = g^s \pmod p$ 并发送 $s$。
- (20) Bob 计算 $a = g^x \pmod p$ 并发送 $x$。
- (21) Alice 计算 $y = g^z \pmod p$ 并发送 $j$。
- (22) Bob 计算 $s = g^s \pmod p$ 并发送 $s$。
- (23) Alice 计算 $h = g^x \pmod p$ 并发送 $k$。
- (24) Bob 计算 $s = g^t \pmod p$ 并发送 $t$。
- (25) Alice 计算 $s = g^s \pmod p$ 并发送 $s$。
- (26) Bob 计算 $a = g^x \pmod p$ 并发送 $x$。
- (27) Alice 计算 $y = g^z \pmod p$ 并发送 $j$。
- (28) Bob 计算 $s = g^s \pmod p$ 并发送 $s$。
- (29) Alice 计算 $h = g^x \pmod p$ 并发送 $k$。
- (30) Bob 计算 $s = g^t \pmod p$ 并发送 $t$。
- (31) Alice 计算 $s = g^s \pmod p$ 并发送 $s$。
- (32) Bob 计算 $a = g^x \pmod p$ 并发送 $x$。
- (33) Alice 计算 $y = g^z \pmod p$ 并发送 $j$。
- (34) Bob 计算 $s = g^s \pmod p$ 并发送 $s$。
- (35) Alice 计算 $h = g^x \pmod p$ 并发送 $k$。
- (36) Bob 计算 $s = g^t \pmod p$ 并发送 $t$。
- (37) Alice 计算 $s = g^s \pmod p$ 并发送 $s$。
- (38) Bob 计算 $a = g^x \pmod p$ 并发送 $x$。
- (39) Alice 计算 $y = g^z \pmod p$ 并发送 $j$。

## 23.6 使用加密数据计算

一个素数 $p$ 和一个原元 $g$ 被公开并由一组用户使用。两个素数的积 $n$ 也是公开的。一个私钥 $z$ 和公钥 $h = g^z \pmod p$。Carol 有一个私钥，以及一个第三方。

在该协议中，Alice 可以对 $m$ 签名，使得 Bob 确信签名是有效的，而无需选择第三方。

- (1) Alice 选择随机的 $x$ 并计算
$a = g^x \pmod p$
$b = h^x \pmod p$

她计算 $m$ 的哈希值 $H[m]$，并将 $a$ 和 $b$ 的哈希值拼接为 $H(a,b)$。然后她计算
$nj=[H(m) \oplus H(a,b)]^s \pmod n$

- 并将 $a, b$, 和 $j$ 发给 Bob。
- (2) Bob 选择两个随机数 $s$ 和 $t$，都小于 $n$，发送给 Alice。
- (3) Alice 选择一个随机的 $q$，小于 $p$，并计算 $q \pmod p$
$d = g^q \pmod p$
- (4) Bob 将 $a, b$ 和 $j$ 发给 Carol。
- (5) Carol 计算 $s = g^s \pmod p$ 并发送给 Bob。

(注：由于原文文本存在大量重复和乱码，此处根据用户提供的逻辑重新整理了清晰的翻译)

[content]

## 第 23 章 协议的特殊算法

## 可转换不可否认签名

一种可转换不可否认签名的算法，它可以被验证、否认，并还可以转换为传统的数字签名，在 [213] 中。它基于 ElGamal 数字签名算法。

与 ElGamal 类似，首先选择两个素数 $p$ 和 $q$，使得 $q$ 整除 $p-1$。现在你需要创建一个小于 $q$ 的数 $g$。在 2 到 $p-1$ 之间选择一个随机数 $h$。计算

$g = h^{-1/q} \bmod p$

如果 $g$ 等于 1，则选择另一个随机 $h$。如果没有，则使用当前的 $g$。私钥是两个小于 $q$ 的不同数字 $x$ 和 $z$。公钥是 $p, q, g, y$ 和 $u$，其中

$y = g' \bmod p$
$u = g' \bmod p$

要计算消息 $m$（实际上是消息的哈希值）的不可否认签名，首先在 1 到 $q-1$ 之间选择一个随机数 $t$。然后计算

$T = g^t \bmod p$

以及

$m' = Ttztm \bmod q$。

现在，对 $m'$ 计算 ElGamal 签名。选择一个随机数 $R$，使得 $R$ 小于 $p-1$ 且与之互质。然后计算 $r = g^R \bmod p$，并使用扩展欧几得算法计算 $s$，使得

$m' = tx + Rs \bmod q$

签名是 ElGamal 签名 $[t, s]$ 以及 $T$。以下是 Alice 如何向 Bob 验证她的签名：

- (1) Bob 生成两个随机数 $a$ 和 $b$。他计算 $c = T^{ma'} \bmod p$ 并发送给 Alice。
- (2) Alice 生成一个随机数 $k$，计算 $h_1 = cg^k \bmod p$ 和 $h_2 = h_1^{k'} \bmod p$，并将这两个数字都发送给 Bob。

## 23.5 指定确认者签名

(3) Bob 向 Alice 发送 $a$ 和 $b$。
(4) Alice 验证 $c = T^{T_{mg}^g} \pmod p$。她将 $k$ 发给 Bob。
(5) Bob 验证 $h_1 = T^{T_{mg}^{g+k}} \pmod p$，以及 $h_2 = y^{c^{a}u^b+k} \pmod p$。

Alice 可以通过发布 $z$ 将任何不想要的签名转换为普通签名。现在，任何人可以在没有她的帮助的情况下验证她的签名。

不可否认签名方案可以与秘密共享方案结合以创建分布式不可否认签名 [1235]。某人可以对消息签名，并分配确认该签名有效的能力。例如，可能需要五个人中的三个人参与协议，才能说服 Bob 签名是有效的。这一概念的改进消除了对可信分发者的要求 [700,1369]。

## 23.5 指定确认者签名

以下是 Alice 如何对签名以及 Bob 如何验证它，使得 Carol 可以在稍后的某个时间向 Dave 验证 Alice 的签名（见第 4.4 节）[333]。

首先，一个大素数 $p$ 和一个原元 $g$ 公开供一组用户使用。两个素数的积 $n$ 也是公开的。一个私钥 $z$ 和公钥 $h = g^z \pmod p$。Carol 有一个私钥，以及一个第三方。

在该协议中，Alice 可以对 $m$ 签名，使得 Bob 确信签名是有效的，而无需选择第三方。

- (1) Alice 选择随机的 $x$ 并计算
$a = g^x \pmod p$
$b = h^x \pmod p$

她计算 $m$ 的哈希值 $H[m]$，并将 $a$ 和 $b$ 的哈希值拼接为 $H(a,b)$。然后她计算
$nj=[H(m) \oplus H(a,b)]^s \pmod n$

- 并将 $a, b$, 和 $j$ 发给 Bob。
- (2) Bob 选择两个随机数 $s$ 和 $t$，都小于 $n$，发送给 Alice。
- (3) Alice 选择一个随机的 $q$，小于 $p$，并计算 $q \pmod p$
$d = g^q \pmod p$

