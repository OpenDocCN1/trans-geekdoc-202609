
# 整数分解问题

我们找到两个整数 $a$ 和 $b$，使得 $a^2 \equiv b^2 \pmod n$ 且 $a \neq \pm b \pmod n$。因此，可以确定 $n$ 的非平凡因子。例如，考虑 $n=301$ 和 $B=13$。这里，$B=\{2,3,5,7,11,13\}$。现在执行以下计算：

```
$19^2 = 361 \pmod{301} = 2^2 \times 3 \times 5$

$20^2 = 400 \pmod{301} = 3^2 \times 11$

$21^2 \equiv 140 \pmod{301} = 2^2 \times 5 \times 7$
```

$22^2 = 484 \pmod{301} = 3 \times 61$
$23^2 = 529 \pmod{301} = 2^2 \times 3 \times 19$
$24^2 = 576 \pmod{301} = 5^2 \times 11$
$25^2 = 625 \pmod{301} = 1 \times 23$
$26^2 = 676 \pmod{301} = 2 \times 37$
$28^2 = 784 \pmod{301} = 2 \times 7 \times 13$

对于集合 $M=\{19,20,21,24,28\}$，$f(r) = r^2$ 在 $B$ 上是平滑的。我们也得到：
$20^2 \times 24^2 = 3^2 \times 5^2 \times 11$，因此 $a=480$ 且 $b=165$。所以，301 的因子是 $\gcd(480-165,301)=7$ 和 $\gcd(480+165,301)=43$。注意 $a$ 和 $b$ 可以通过相指数向量找到，即求解同余方程：

```
$x_1 + x_3 + x_5 \equiv 0 \pmod 2$
$x_1 + 2x_2 \equiv 0 \pmod 2$
$x_3 + 2x_4 \equiv 0 \pmod 2$
$x_3 \equiv 0 \pmod 2$
$x_2 + x_4 \equiv 0 \pmod 2$
$x_5 \equiv 0 \pmod 2$
```

该方程的一个非平凡解是 $(0,1,0,1)$。因此，我们得到同余 $20^2 \times 24^2 \equiv 3^2 \times 5^2 \times 11^2 \pmod{301}$。这里，$U=\{20,24\}$ 是 $M$ 的子序列。

## 5.3.2 二次方法

Pomerance (1982) 开发了一种名为 QS 方法的新型分解算法。这种方法类似于平方方法，但在这里使用筛选程序来寻找值 $r^2 \pmod n$。该算法定义如下：

1. 选择一个合数 $n$。
2. 选择一个边界 $B=\{p_1, p_2, \dots, p_{\pi(B)}\}$。
3. 考虑因子基 $B$。
4. 选择整数 $r$，使得 $f(r)=r^2-n$ 在 $B$ 上是平滑。
5. 选择子集 $U=\{r_1, r_2, \dots, r_m\}$ 使得：
   i. $f(r_i) = p_1^{e_{i1}} p_2^{e_{i2}} \dots p_{\pi(B)}^{e_{i\pi(B)}} \pmod n$，对于所有 $i$
   ii. $\sum_{i=1}^m e_{ij} = 2k_j, 1 \le j \le \pi(B)$，对于某些 $k_j \in \mathbb{Z}$
   其中 $e_{ij}$ 是 $p_j$ 在 $f(r_i)$ 分解中出现的指数。

6. 计算整数 $a$ 和 $b$，使得 $a = \prod_{i=1}^m r_i$ 且 $b = \prod_{j=1}^{B} p_j^{k_j}$。
7. 然后，我们有：

```
$a^2 = \prod_{i=1}^m r_i^2 = (\prod_{j=1}^{\pi(B)} p_j^{k_j})^2 \equiv b^2 \pmod n$
```

这导致了 $n$ 的非平凡因子。QS 方法类似于之前的方法，但在这里将 $r^2 \pmod n$ 替换为 $f(r)=r^2-n$。在因子基上检查 $f(r)$ 在 $B$ 上是平滑的是高效的。筛选过程可以发现 $f(r)$ 被因子基 $B$ 中的所有质数整除，对于所有 $i$。这意味着 $f(r)$ 在 $B$ 上是平滑的。对于 $t \in \mathbb{Z}$，$f(r) \equiv 0 \pmod{p_i}$。

该方法的预期运行时间为 $O(e^{(1+\epsilon)\sqrt{\log n \log \log n}})$，对于任何 $\epsilon>0$（Bimpakis & Jaiswal, 2005）。

## 5.3.3 数域筛选法

NFS 被认为是分解大数最快的方法。与其他分解方法一样，该方法也使用 $x^2 \equiv y^2 \pmod n$ 来寻找 $n$ 的因子，但这种计算是在代数整数上进行的。NFS 最初是为特殊形式的多项式设计的，这种变体被称为特殊数域筛选 (SNFS)。在1992年，该算法被修改用于任意整数，并称为通用数域筛选 (GNFS)。对于110位数字，QS 方法比 NFS 方法快。

注意，有限集合 $A \subseteq Z[\theta]$ 是一个代数因子基，其中每个 $a+b\theta$ 满足条件 $c, d \in Z[\theta]$ 使得 $c-d = a+b\theta, \forall(a,b)$；且元素 $l \in Z[\theta]$ 在 $A$ 上是平滑的，如果存在 $W \subset A$ 使得 $\prod_{(c,d) \in W}(c+d\theta)=1$。使用以下定理（Case，2003），代数因子基 $A$ 可以表示为整数集合 $\{(r,p)\}$。

### 定理

设 $f(x)$ 为具有整数系数的多项式函数，令 $\theta \in \mathbb{C}$ 为 $f(x)$ 的根。集合对 $\{(r,p)\}$（其中 $p$ 是素数，$r \in Z_p$ 是整数且满足 $f(r) \equiv 0 \pmod p$）与集合 $a+b\theta \in Z[\theta]$ 双双对应（Case, 2003）。

在 $Z[\theta]$ 和 $Z$ 中寻找平方数，必须找到一对数 $(a,b)$，使得 $a+b\theta$ 和 $a+bm$ 分别在 $A$ 和 $B$ 中是平滑的。可以通过以下方法找到（Case, 2003）：

- i. 选择一个整数 $b \in Z$ 和任意正整数 $N$。$a$ 从 $-N$ 运行到 $N$。

- ii. 通过以下方法找到两个数组：

![](img/5ee0cf067ac8390dfbbfeae8da2f7512_82_0.png)

- iii. 注意，如果 $a \equiv -bm \pmod{q_i}$，则 $q_i$ 将整除 $a+bm$，其中 $q_i \in B$。找到所有满足 $a \equiv -bm \pmod{q_i}$ 的 $a$ 值，并对于每个 $a$ 值，在筛数组中列出 $a$ 的因子。该过程对每个 $q_i \in B$ 重复。列出筛数组中所有被此方法完全分解的 $a+bm$。这些 $a+bm$ 在 $B$ 中是平滑的。

- iv. 如果 $a \equiv -br \pmod p$，则数对 $(r,p) \in A$ 整除 $a+b\theta$。找到所有满足 $a \equiv -br \pmod p$ 的 $a$ 值。对于每个 $a$，在筛数组中列出 $a+b\theta$ 的所有 $(r,p)$ 因子。最后，筛数组中将有一份 $a+b\theta$ 的 $(r,p)$ 因子列表。现在，如果 $\Pi_i = (-b)^d f(-a/b)$，则该因子列表是完全分解，在这种情况下，$a+b\theta$ 在 $A$ 上是平滑的。

- v. 通过比较两个数组，可以找到 $(a,b)$ 使得 $a+b\theta$ 和 $a+bm$ 平滑的。

再次，这两个定理保证了可以在 $Z[\theta]$ 中找到一个完全平方元素：

### 定理 (Case, 2003)

设 $l \in Z[\theta]$ 有分解式 $l = (a_1+b_1\theta)^{e_1}(a_2+b_2\theta)^{e_2} \cdots$，其中对于每个 $i$，$a_i+b_i\theta$ 满足属于代数因子基的标准。如果 $l$ 是 $Z[\theta]$ 中的完全平方数，则对于所有 $i$，$e_i \equiv 0 \pmod 2$ (Case, 2003)。

### 定理 (Case, 2003)

设 $U$ 为 $(a,b)$ 对，使得 $\prod_{(a,b) \in U}(a+b\theta)$ 在 $Z[\theta]$ 中是完全平方数。那么对于任何 $(s,q)$，由于 $(s,q) \nmid a+b$，对于任何 $(a,b) \in U$，
`$\prod_{(a,b)\in U} \frac{a+bs}{q} = 1$`
其中 $q$ 是素数，$s \in \mathbb{Z}$ 且 $f(s) \equiv 0 \pmod q$ (Case, 2003)。对于素数 $q$，满足 $f(s) \equiv 0 \pmod q$ 的 $(s,q)$ 对被称为二次基，元素 $(s,q)$ 称为二次（Case, 2003）。注意每个 $(a,b) \in U$ 都可以通过代数因子基 $A$ 的 $k$ 个元素、因子基 $B$ 的 $l$ 个元素和二次基 $Q$ 的 $u$ 个元素表示为阶 $1+k$。对于元素，证明了 $\prod_{(a,b)\in U}(a+b\theta)$ 和 $\prod_{(a,b)\in U}(a+b)$ 分别在 $Z[\theta]$ 和 $Z$ 中是完全平方数，且仅当每个 $(a,b)$ 的向量和模 2 等于零。因此只需检查每个 $(a,b)\in U$ 的向量和是否等于 $0 \pmod 2$。现在得到 $\prod_{(a,b)\in U}(a+b\theta)$ 在 $\mathbb{Z}$ 和 $Z[\theta]$ 中分别是完全平方数，可以通过环同态分解 $n$。

该算法的期望运行时间为 $O(e^{(c+o(1))(\log n)^{1/3}(\log \log n)^{2/3}})$，其中 $c$ 是一个值为 1.9 的常数。该方法的细节可以在 Lenstra (2000) 中找到。

## 基于近似的分解方法

Zalak 和 Haj-Boutros (2011) 提出了一种基于平方根近似的新整数分解方法。它包括寻找阶 $R_p=(p_1 \times p_2 \times \cdots \times p_n)$，其中 $\gcd(R_p,n)$ 在约定的时间内给出前两个因子。该过程重复直到获得 $n$ 的所有素因子。

算法定义如下：这里 $A$ 和 $B$ 是需要确定的合数。假设任何素因子 $B$ 可以表示为 $B=A\frac{p^2}{q^2}+\frac{m^2}{q^2}$，其中 $p$ 和 $q$ 是素数或互质，$m$ 是整数，且 $m^2$ 较小于 $A^2$。那么
$n=\frac{A^2p^2}{q^2}(1+\frac{m}{Ap^2})$ 这

## 新兴算法与技术

给出 $\sqrt{n}=\frac{Ap}{q}\left(1+\frac{m}{Ap^2}\right)$。由于 $\frac{m}{Ap^2} \ll 1$，所以 $(1+\frac{m}{Ap^2})=1+\frac{m}{2Ap^2}$，因此 $\sqrt{n}=\frac{Ap}{q}-\frac{m}{2pq}$。

由于 $\frac{m}{2pq} \ll 1$，可以考虑以下两个近似：

- i. $\sqrt{n}$ 的整数部分为 $[\sqrt{n}]\frac{Ap}{q} \pm \varepsilon$。

- ii. $\sqrt{n}$ 的小数部分为 $(\sqrt{n}-[\sqrt{n}])px=k \pm \varepsilon'$，其中 $k$ 是正整数或半整数，$0 \le \varepsilon < 1$ 且 $0 \le \varepsilon' \ll 1$。

因此，可以通过将小数部分 $\sqrt{n}-[\sqrt{n}]$ 乘以 $r=pq$ 来找到 $k$。由于 $r$ 是一个小的整数，如果找到了 $k$，可以使用任何分解方法轻松找到 $p$ 和 $q$。然后，将整数部分 $[\sqrt{n}]$ 乘以 $\frac{P}{q}$ 得到一个近似等于 $A$ 的数。算法所示。我们考虑 Zalek 和 Haj-Boutros (2011) 的分解算法。

## 算法

**输入:** $n$: 一个待分解的整数
$P$: 素数子集列表
Upr：允许的最高 $r=pq$ 阈值
Highstep：允许寻找解的步数阈值

**输出:** $A$ 和 $B$，$n$ 的两个整数因子。

```
begin

初始化;

$\varepsilon:=0.02, r:=2, steps:=0$;

fx:=\sqrt{n}-[\sqrt{n}];

迭代直到找到因子或达到 $steps$ 指定的阈值；

repeat

  while ($r < upr$ AND $fx \times r \neq [fx \times r] \pm \varepsilon$) do

    找到 $fx$ 的一个可能倍数以生成其最近的整数；

    steps:=steps+1;

    将 $r$ 分为 $p$ 和 $q$;

until $A$ 是 $n$ 的除因子;

if steps > Highstep then

B := \frac{n}{A}

else

print("n是素数或未找到解");
```
