
## 7.4 云计算中的经典密码学

在本节中，对现有的经典密码学机制（如 RSA、AES、DES 和 Blowfish）进行了详细研究。

### 7.4.1 RSA

RSA 是一种非对称密钥密码学，在加密过程中使用公钥，在解密过程中使用私钥。它包含三个不同的阶段，分别是密钥生成阶段、加密阶段和解密阶段 [35]。

密钥生成

- 1. 选择两个素数 P 和 Q
- 2. 计算 $N = P \times Q$
- 3. 计算 $\varphi\left(N\right) = (P - 1) \times (Q - 1)$
- 4. 选择 e，使得 $gcd(\varphi\left(N\right), e) = 1$
- 5. 计算 $d = e^{-1}\, mod\, \varphi\left(N\right)$
- 6. 选择 e 作为公钥，d 作为私钥

加密过程
设 M 为需要存储的明文，C 为计算得出的密文。则 C 可以通过以下方式计算：

- 1. $C = M^{e}\, mod\, N$

解密过程
可以通过以下方式从密文 C 中恢复明文 M：

- 1. $M = C^{d}\, mod\, N$

### 7.4.2 AES

AES 作用于 128 位数据块，采用三种不同的密钥长度，分别为 128、192 和 256 位 [32, 33]。它有四个不同的阶段，如下所示：

- 替代字节（Substitution Byte）：明文的每一位被 8 位 S 盒中的替代位所替换。
- 行移位（Shift Row）：该操作以行为单位进行。每一行的元素通过特定的偏移量进行乱序。第一行保持不变，第二行的元素向左移位 1 位，第三行的元素向左移位 2 位，同理，第四行的元素向左移位 3 位。
- 列混合（Mix Column）：在此阶段，每一列通过线性函数映射以重构一个新的输入矩阵。
- 轮密钥加（Add Round Key）：在此步骤中，将子密钥与输入矩阵进行异或运算以获得密文。

在加密过程中，上述过程按顺序执行；但在解密过程中，上述过程按相反顺序执行。

### 7.4.3 DES

它利用了 16 轮 Feistel 密码结构，输入明文大小为 64 位。它将整个明文分为两个相等的块，每块为 32 位。对于加密过程，它使用了一个轮密钥生成器，该生成器从可用的 56 位密钥中取出 48 位的子密钥。一个块与子密钥结合，而另一个块保持不变，以获取下一段文本。子块大小为 32，子密钥大小为 48 位，因此 DES 使用 P-BOX 将块大小从 32 位扩展为 48 位。操作完成后，扩展后的块再次借助 S-Box 压缩回 32 位。此过程重复 16 次以获取密文。

### 7.4.4 Blowfish

Blowfish 是 DES 算法的一种替代方案。在此协议中，每个周期采用从 32 位到 448 位的可变密钥长度来获取密文。Blowfish 技术的输入块大小为 64 位。由于其不受专利保护且可自由用于所有用途，因此它正变得越来越流行。

## 7.5 同态密码系统

在本节中，研究了 Paillier 和 RSA 两种同态加密技术。这两种策略都是部分同态的。RSA 支持乘法同态性质，而 Paillier 支持加法同态性质。

### 7.5.1 Paillier 密码系统

它由 Paillier 于 1999 年发明。这是一种支持加法同态性质的公钥密码学。它包含三个阶段，分别是密钥生成、加密和解密阶段 [34]。

密钥生成

- 1. 选择两个素整数 P 和 Q
- 2. 计算 N = P × Q
- 3. 计算 $\lambda = \text{lcm}(P - 1, Q - 1)$
- 4. 找到 g，使得 $gcd(L(g^{\lambda} \bmod n^2), n) = 1$

L 可以定义为 $\frac{x-1}{n}$，其中 x 是明文。

- 5. 计算 $\mu = L(g^{\lambda} \bmod n^2)^{-1} \bmod n$
- 6. 公钥 = (n, g)，私钥 = ($\lambda, \mu$)

加密

- 1. M 是明文
- 2. 选择一个随机整数 r，使得 $0 < r < n$
- 3. $C = g^M r^n \bmod n^2$

解密

- 1. $M = L(C^{\lambda} \bmod n^2) \cdot \mu \bmod n$

#### 7.5.1.1 加法同态性质

设 E 为加密函数，M1 和 M2 为两个可供加密的明文，则

$E(M1 + M2) = E(M1) + E(M2)$

C1 和 C2 分别是 M1 和 M2 的两个密文，使用两个随机变量 r1 和 r2，则

$C1, C2 = g^{(M1 + M2)} (r1 \cdot r2)^n \bmod n^2$

### 7.5.2 RSA 同态密码系统

密钥生成 [35]

- 1. 选择两个素数 P 和 Q
- 2. 计算 $N = P \times Q$
- 3. 计算 $\phi(N) = (P-1) \times (Q-1)$
- 4. 选择 e，使得 $gcd(\phi(N), e) = 1$
- 5. 计算 $d = e^{-1} \bmod \phi(N)$
- 6. 选择 e 作为公钥，d 作为私钥

加密过程
设 M 为需要存储的明文，C 为计算得出的密文。则 C 可以通过以下方式计算：

- 1. $C = M^{e} \bmod N$

解密过程
可以通过以下方式从密文 C 中恢复明文 M：

- 1. $M = C^{d} \bmod N$

#### 7.5.2.1 乘法同态性质

设 E 为加密函数，M1 和 M2 为两个可供加密的明文，则

$E(M1, M2) = E(M1) \cdot E(M2)$

C1 和 C2 分别是 M1 和 M2 的两个密文，则

$C1, C2 = (M1 \cdot M2)^{e} \bmod n$

## 7.6 实现

在这篇研究文章中，作者们尝试在 java 环境中实现经典 RSA、Paillier 同态机制和 RSA 同态机制。计算对存储数据执行某些更新操作所花费的时间，并表明同态加密技术的运行时间远快于经典密码学。使用内存分析器来测量上述算法在操作期间使用的内存。上述算法已在 java 中实现，系统配置为 8GB RAM、Windows 10 操作系统和 1TB HDD，并使用 ECLIPSE JVM 内存分析器来跟踪算法使用的内存。需要导入 java 的 Security、IO 和 UTIL 包才能成功执行算法。图 7.2 和 7.3 分别显示了经典 RSA、Paillier 同态加密和 RSA 同态算法的运行时间和内存利用率比较。

![](img/cbc35e0d02425baa6028b87d56263a7f_182_0.png)

**图 7.2** CRSA、Pallier HE 和 RSA HE 的运行时间。

![](img/cbc35e0d02425baa6028b87d56263a7f_182_1.png)

**图 7.3** CRSA、HE RSA 和 HE PAILLIER 的内存分析。

## 7.7 结论与未来展望

本研究旨在调查经典密码学及同态密码系统的特点。在对经典密码学中的存储数据执行某些操作时，与同态加密系统相比，计算所花费的时间更长。因为在经典密码学中，必须先对密文进行解密，然后才能执行操作，所以计算时间较高。与经典密码学不同，同态加密系统允许用户直接对密文进行操作，这有助于减少计算时间。在这项工作中，作者实现了经典 RSA 以及 HE RSA 和 HE Paillier，用于加密后执行乘法或加法。结果表明，经典 RSA 的时间高于另外两种。在这项工作中，我们还讨论了密码学在云计算中的重要性，以及经典密码学中所面临的缺点，这些缺点通过应用同态密码学得到了消除。

RSA 和 Pallier HE 密码系统的计算时间取决于密钥大小。如果密钥大小更大，计算时间和成本也将严重增加。这项工作的未来展望是减少在云计算环境中应用同态加密系统时的时间复杂度。

## 参考文献

- 1. Wang, G. and Ng, T.E., The impact of virtualization on network performance of amazon ec2 data center, in: 2010 Proceedings IEEE INFOCOM, 2010, March, IEEE, pp. 1–9.
- 2. Wilder, B., Cloud architecture patterns: using microsoft azure, O’Reilly Media, Inc., North Sebastopol, CA, 2012.
- 3. Serrano, N., Gallardo, G., Hernantes, J., Infrastructure as a service and cloud technologies. IEEE Software, 32, 2, 30–36, 2015.
- 4. Zhou, T., Shen, J., Li, X., Wang, C., Shen, J., Quantum cryptography for the future internet and the security analysis, in: Security and Communication Networks, 2018.

