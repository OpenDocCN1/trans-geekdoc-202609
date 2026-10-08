(cf. Definition 2.2.1). Furthermore, note that item (i) in Lemma 2.4.2 demonstrates that

```
$$\begin{equation}
\mathcal{D} \big( \mathbb{S}_{\mathcal{O}(\Phi_m), n-m+1} \big) = \big( (n-m+1) \mathcal{O}(\Phi_m), \mathcal{O}(\Phi_m) \big)
\tag{2.157}
\end{equation}$$
```

(cf. Definition 2.4.1). This, (2.156), and item (i) in Proposition 2.1.2 show that

```
$$\begin{equation}
\begin{split}
\mathcal{D} \big( \mathbb{S}_{\mathcal{O}(\Phi_m), n-m+1} \bullet \big[ \mathbb{P}_{n-m+1}(\Phi_m, \Phi_{m+1}, \dots, \Phi_n) \big] \big) 
&= \bigg( (n-m+1) \mathcal{I}(\Phi_m), \sum_{k=m}^{n} \mathbb{D}_1(\Phi_k), \sum_{k=m}^{n} \mathbb{D}_2(\Phi_k), \dots, \sum_{k=m}^{n} \mathbb{D}_{\mathcal{I}(\Phi_m)-1}(\Phi_k), \mathcal{O}(\Phi_m) \bigg).
\end{split}
\tag{2.158}
\end{equation}$$
```

Moreover, observe that item (i) in Lemma 2.4.7 establishes that

```
$$\begin{equation}
\mathcal{D} \big( \mathbb{T}_{\mathcal{I}(\Phi_m), n-m+1} \big) = \big( \mathcal{I}(\Phi_m), (n-m+1) \mathcal{I}(\Phi_m) \big)
\tag{2.159}
\end{equation}$$
```

(cf. Definitions 2.1.1 and 2.4.6). Combining this, (2.158), and item (i) in Proposition 2.1.2 ensures that

```
$$\begin{equation}
\begin{split}
\mathcal{D} \bigg( \bigoplus_{k=m}^{n} \Phi_k \bigg)
&= \mathcal{D} \bigg( \mathbb{S}_{\mathcal{O}(\Phi_m), (n-m+1)} \bullet \big[ \mathbb{P}_{n-m+1}(\Phi_m, \Phi_{m+1}, \dots, \Phi_n) \big] \bullet \mathbb{T}_{\mathcal{I}(\Phi_m), (n-m+1)} \bigg) \\
&= \bigg( \mathcal{I}(\Phi_m), \sum_{k=m}^{n} \mathbb{D}_1(\Phi_k), \sum_{k=m}^{n} \mathbb{D}_2(\Phi_k), \dots, \sum_{k=m}^{n} \mathbb{D}_{\mathcal{I}(\Phi_m)-1}(\Phi_k), \mathcal{O}(\Phi_m) \bigg)
\end{split}
\tag{2.160}
\end{equation}$$
```

(cf. Definition 2.4.10). This proves items (i) and (ii). Note that Lemma 2.4.9 and (2.156) imply that for all $a \in C(\mathbb{R}, \mathbb{R})$, $x \in \mathbb{R}^{\mathbb{Z}(\Phi_m)}$ it holds that

```
$$\begin{equation}
\mathcal{R}_a^{\mathbf{N}} \big( \big[ \mathbb{P}_{n-m+1}(\Phi_m, \Phi_{m+1}, \dots, \Phi_n) \big] \bullet \mathbb{T}_{\mathcal{I}(\Phi_m), n-m+1} \big) \in C( \mathbb{R}^{\mathcal{I}(\Phi_m)}, \mathbb{R}^{(n-m+1)\mathcal{O}(\Phi_m)} )
\tag{2.161}
\end{equation}$$
```

and

```
$$\begin{equation}
\begin{split}
\big( \mathcal{R}_a^{\mathbf{N}} \big( \big[ \mathbb{P}_{n-m+1}(\Phi_m, \Phi_{m+1}, \dots, \Phi_n) \big] \bullet \mathbb{T}_{\mathcal{I}(\Phi_m), n-m+1} \big) \big)(x)
&= \big( \mathcal{R}_a^{\mathbf{N}} \big( \big[ \mathbb{P}_{n-m+1}(\Phi_m, \Phi_{m+1}, \dots, \Phi_n) \big] \big) (x, x, \dots, x)
\end{split}
\tag{2.162}
\end{equation}$$
```

(cf. Definition 1.3.4). Combining this with item (ii) in Proposition 2.2.3 demonstrates that for all $a \in C(\mathbb{R}, \mathbb{R})$, $x \in \mathbb{R}^{\mathbb{Z}(\Phi_m)}$ it holds that

```
$$\begin{equation}
\begin{split}
\big( \mathcal{R}_a^{\mathbf{N}} \big( \big[ \mathbb{P}_{n-m+1}(\Phi_m, \Phi_{m+1}, \dots, \Phi_n) \big] \bullet \mathbb{T}_{\mathcal{I}(\Phi_m), n-m+1} \big) \big)(x)
&= \big( (\mathcal{R}_a^{\mathbf{N}} (\Phi_m))(x), (\mathcal{R}_a^{\mathbf{N}} (\Phi_{m+1}))(x), \dots, (\mathcal{R}_a^{\mathbf{N}} (\Phi_n))(x) \big) \in \mathbb{R}^{(n-m+1)\mathcal{O}(\Phi_m)}.
\end{split}
\tag{2.163}
\end{equation}$$
```

Lemma 2.4.3, (2.157), and Corollary 2.1.5 hence show that for all $a \in C(\mathbb{R}, \mathbb{R})$, $x \in \mathbb{R}^{\mathbb{Z}(\Phi_m)}$ it holds that $\mathcal{R}_a^{\mathbf{N}} \big( \bigoplus_{k=m}^{n} \Phi_k \big) \in C(\mathbb{R}^{\mathcal{I}(\Phi_m)}, \mathbb{R}^{\mathcal{O}(\Phi_m)})$ and

```
$$\begin{equation}
\begin{split}
\bigg( \mathcal{R}_a^{\mathbf{N}} \bigg( \bigoplus_{k=m}^{n} \Phi_k \bigg) \bigg)(x)
&= \big( \mathcal{R}_a^{\mathbf{N}} \big( \mathbb{S}_{\mathcal{O}(\Phi_m), n-m+1} \bullet \big[ \mathbb{P}_{n-m+1}(\Phi_m, \Phi_{m+1}, \dots, \Phi_n) \big] \bullet \mathbb{T}_{\mathcal{I}(\Phi_m), n-m+1} \big) \big)(x) \\
&= \sum_{k=m}^{n} (\mathcal{R}_a^{\mathbf{N}} (\Phi_k))(x).
\end{split}
\tag{2.164}
\end{equation}$$
```

This establishes item (iii). The proof of Lemma 2.4.11 is thus complete.