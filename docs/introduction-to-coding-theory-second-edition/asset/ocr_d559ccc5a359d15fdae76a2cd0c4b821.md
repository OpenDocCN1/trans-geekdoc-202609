that $\mathcal{D}$ has minimum distance $\ge 6$. We want to show that the same is true of the $(n-7)$-dimensional cyclic code $\mathcal{C}$. Let $d$ be the minimum distance of $\mathcal{C}$ and assume $d<6$. In each application of Lemma 13.17 we choose $j\in C(q-2)$. The condition on $j$ from Lemma 13.17 is then satisfied. We start with $\{q-1,q\}\longrightarrow\{q-1,q,2q-1\}$ and continue

$\{0,1,q\}\longrightarrow\{0,1,q,q+1\}\longrightarrow\{-1,0,q-1,q\}\longrightarrow\longrightarrow\{-1,0,q-1,q,2q-1\}\longrightarrow\{-q,-(q-1),0,1,q\}.

The resulting independent set of size 5 is contained in $\{0\}\cup C(1)$. We have proved the following:

# 13.18 Theorem.

Let $q\ge4$. The cyclic $q$-ary code of length $q^2-q+1$ with $A=\{0,1\}$ is a $[q^2-q+1,q^2-q-6,6]_q$-code.

Short examples are $[13,6,6]_4$, $[21,14,6]_5$, $[43,36,6]_7$.

# Generator matrices of cyclic codes

In order to be able to work with cyclic codes, we have to determine generator matrices for them. It turns out that we can find an almost canonical form.

Recall the situation: we have $n\mid q^r-1$, $F=\mathbb{F}_q(\epsilon)$, where $\epsilon$ is a primitive element of $F$. Further, $W$ consists of all elements whose $n$-th power is 1 and $W=\{1,\alpha,\alpha^2,\dots,\alpha^{n-1}\}$. Our $q$-ary cyclic code is $\mathcal{C}(A)$. Its dimension is $|B|$, where $-B$ is the union of the cyclotomic cosets, which are disjoint from $\tilde A$. Let $C$ be a cyclotomic coset disjoint from $\tilde A$. Then $\operatorname{tr}(\mathcal{B}(-C))\subset\mathcal{C}(A)$ and $\mathcal{C}(A)$ is the direct sum of all those codes. In other words, $\mathcal{C}(A)$ is the direct sum of the codes $\operatorname{tr}(\mathcal{B}(C))$, where $C$ varies over the cyclotomic cosets contained in $B$. Each such code has dimension $|C|$. We have $\operatorname{tr}(\mathcal{B}(C))=\mathcal{B}(C)_{\mathbb{F}_q}$, but the expression using the trace is handler: it may be hard to find a systematic way to write down the words of an $F$-linear code all of whose entries happen to be in the subfield $\mathbb{F}_q$, whereas there is no problem in applying the trace mapping.

In particular, each cyclotomic coset $C$, $C\cap\tilde A=\emptyset$ contributes $|C|$ rows to a generator matrix of $\mathcal{C}(A)$.

To fix notation, denote $v(l,i)\in\mathbb{F}_q^n$ the vector with entry $\operatorname{tr}(\epsilon^l\beta^i)$ in coordinate $\beta\in W$. If $i\in C$, then $v(l,i)\in\operatorname{tr}(\mathcal{B}(C))$. Observe that $v(l,i)$ is the codeword in $\operatorname{tr}(\mathcal{B}(C))$ corresponding to the monomial $\epsilon^l X^i$. As $1,\epsilon,\dots,\epsilon^{r-1}$ is a basis of $F$ over $\mathbb{F}_q$, we can choose $0\le l\le r-1$.

Let $C$ be a cyclotomic coset, $C\cap\tilde A=\emptyset$. Choose $i\in C$. In the generic case when $|C|=r$, there is no problem: the words $v(0,i)$, $v(1,i),\dots v(r-1,i)$ form a basis of $\operatorname{tr}(\mathcal{B}(C))$. When $|C|<r$, these vectors still generate $\operatorname{tr}(\mathcal{B}(C))$.