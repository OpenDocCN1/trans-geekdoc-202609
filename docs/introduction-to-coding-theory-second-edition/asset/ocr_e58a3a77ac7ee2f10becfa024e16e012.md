Binary linear codes are particularly handy for block coding. We use a linear code $\mathcal{C}$ with parameters $[n,k,d]_2$. As there are $2^k$ codewords, we can find a bijective function (the encoding function) $\alpha : \mathbb{F}_2^k \longrightarrow \mathcal{C}$. There is no reason not to choose this function as a linear function ($\alpha(x + y) = \alpha(x) + \alpha(y)$). Here is a possible encoding function $\alpha$ for our code $[7,4,3]_2$. Observe that the inverse $\alpha^{-1}$ is the projection on the last four coordinates.

| | |
|---|---|
| 0000 ⟶ 0000000 | 0110 ⟶ 1100110 |
| 1000 ⟶ 1101000 | 0101 ⟶ 0100101 |
| 0100 ⟶ 1010100 | 0011 ⟶ 1000011 |
| 0010 ⟶ 0110010 | 1110 ⟶ 0001110 |
| 0001 ⟶ 1110001 | 1101 ⟶ 1001101 |
| 1100 ⟶ 0111100 | 1011 ⟶ 0101011 |
| 1010 ⟶ 1011010 | 0111 ⟶ 0010111 |
| 1001 ⟶ 0011001 | 1111 ⟶ 1111111 |

We can describe how block coding works: the incoming data is divided into consecutive blocks of length $k$. Each such block is therefore a bitstring of length $k$, an element of $\mathbb{F}_2^k$. Apply the encoding function $\alpha$ to each block. The result is an encoded block of length $n$. These are transmitted via the channel. Error correction (recall our basic coding idea: $e = \lfloor (d - 1)/2 \rfloor$ bit errors per encoded block can be corrected) produces blocks of length $n$, which hopefully are the same as the blocks fed into the channel. Finally, the inverse $\alpha^{-1}$ of the encoding function is applied to each block of length $n$. The result is a block of length $k$, which hopefully is identical to the corresponding block of raw data. The last two stages of the procedure (error correction and application of $\alpha^{-1}$) are also collectively known as decoding.

The repetition code of length 3 from Section 1.1 is a part of the general picture: the code has parameters $[3,1,3]_2$ and consists of the codewords 000 and 111. The encoding function maps $0 \mapsto 000, 1 \mapsto 111$. This is about as elementary as it gets.

In block coding the length of bitstrings is increased from $k$ to $n$. That means that $k/n$ of the bits sent through the channel represent pure information, whereas the rest is redundancy that we have cleverly introduced for the purposes of error correction. We want to keep that ratio $k/n$ as large as possible in order not to waste time and money.

# **2.7 Definition.** *The ratio $R = k/n$ of a linear $[n,k,d]_2$-code is its* **information rate;** *the ratio $d/n$ is the* **relative distance.**