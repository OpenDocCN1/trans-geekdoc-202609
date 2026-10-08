
# 2.1. Compositions of fully-connected feedforward ANNs

Next note that (2.22), (2.2), and the assumption that $\mathcal{L}(\Phi_{2}) = 1$ imply that for all $k \in \{1,2,\ldots,\mathcal{L}(\Phi_{1})\}$ it holds that

$$
\begin{align} (\mathcal{W}_{k,\Phi_{1}\bullet\Phi_{2}}, \boldsymbol{B}_{k,\Phi_{1}\bullet\Phi_{2}}) = \begin{cases} (\mathcal{W}_{1,\Phi_{1}}\mathcal{W}_{1,\Phi_{2}}, \mathcal{W}_{1,\Phi_{1}}\boldsymbol{B}_{1,\Phi_{2}} + \boldsymbol{B}_{1,\Phi_{1}}) & : k = 1 \\ (\mathcal{W}_{k,\Phi_{1}}, \boldsymbol{B}_{k,\Phi_{1}}) & : k > 1. \end{cases} \tag{2.24} \end{align}
$$

This, (2.2), and (2.23) prove that for all $k \in \{1,2,\ldots,\mathcal{L}(\Phi_{1}) + \mathcal{L}(\Phi_{3}) - 1\}$ it holds that

$$
\begin{align} \begin{aligned} & \left(\mathcal{W}_{k,(\Phi_{1}\bullet\Phi_{2})\bullet\Phi_{3}}, \boldsymbol{B}_{k,(\Phi_{1}\bullet\Phi_{2})\bullet\Phi_{3}}\right) \\ &= \begin{cases} \left(\mathcal{W}_{k,\Phi_{3}}, \boldsymbol{B}_{k,\Phi_{3}}\right) & : k < \mathcal{L}(\Phi_{3}) \\ \left(\mathcal{W}_{1,\Phi_{1}}\mathcal{W}_{\mathcal{L}(\Phi_{3}),\Phi_{3}}, \mathcal{W}_{1,\Phi_{1}\bullet\Phi_{2}}\boldsymbol{B}_{\mathcal{L}(\Phi_{3}),\Phi_{3}} + \boldsymbol{B}_{1,\Phi_{1}\bullet\Phi_{2}}\right) & : k = \mathcal{L}(\Phi_{3}) \\ \left(\mathcal{W}_{k-\mathcal{L}(\Phi_{3})+1,\Phi_{1}\bullet\Phi_{2}}, \boldsymbol{B}_{k-\mathcal{L}(\Phi_{3})+1,\Phi_{1}\bullet\Phi_{2}}\right) & : k > \mathcal{L}(\Phi_{3}) \end{cases} \end{aligned} \tag{2.25} \end{align}
$$

Furthermore, observe that (2.2), (2.22), and (2.23) show that for all $k \in \{1,2,\ldots,\mathcal{L}(\Phi_{1}) + \mathcal{L}(\Phi_{3}) - 1\}$ it holds that

$$
\begin{align} \begin{aligned} & \left(\mathcal{W}_{k,\Phi_{1}\bullet(\Phi_{2}\bullet\Phi_{3})}, \boldsymbol{B}_{k,\Phi_{1}\bullet(\Phi_{2}\bullet\Phi_{3})}\right) \\ &= \begin{cases} \left(\mathcal{W}_{k,\Phi_{2}\bullet\Phi_{3}}, \boldsymbol{B}_{k,\Phi_{2}\bullet\Phi_{3}}\right) & : k < \mathcal{L}(\Phi_{2}\bullet\Phi_{3}) \\ \left(\mathcal{W}_{1,\Phi_{1}}\mathcal{W}_{\mathcal{L}(\Phi_{2}\bullet\Phi_{3}),\Phi_{2}\bullet\Phi_{3}}, \mathcal{W}_{1,\Phi_{1}}\boldsymbol{B}_{\mathcal{L}(\Phi_{2}\bullet\Phi_{3}),\Phi_{2}\bullet\Phi_{3}} + \boldsymbol{B}_{1,\Phi_{1}}\right) & : k = \mathcal{L}(\Phi_{2}\bullet\Phi_{3}) \\ \left(\mathcal{W}_{k-\mathcal{L}(\Phi_{2}\bullet\Phi_{3})+1,\Phi_{1}}, \boldsymbol{B}_{k-\mathcal{L}(\Phi_{2}\bullet\Phi_{3})+1,\Phi_{1}}\right) & : k > \mathcal{L}(\Phi_{2}\bullet\Phi_{3}) \end{cases} \end{aligned} \tag{2.26} \end{align}
$$

Combining this with (2.25) establishes that for all $k \in \{1,2,\ldots,\mathcal{L}(\Phi_{1}) + \mathcal{L}(\Phi_{3}) - 1\} \setminus \{\mathcal{L}(\Phi_{3})\}$ it holds that

$$
\begin{align} \left(\mathcal{W}_{k,(\Phi_{1}\bullet\Phi_{2})\bullet\Phi_{3}}, \boldsymbol{B}_{k,(\Phi_{1}\bullet\Phi_{2})\bullet\Phi_{3}}\right) = \left(\mathcal{W}_{k,\Phi_{1}\bullet(\Phi_{2}\bullet\Phi_{3})}, \boldsymbol{B}_{k,\Phi_{1}\bullet(\Phi_{2}\bullet\Phi_{3})}\right). \tag{2.27} \end{align}
$$

Moreover, note that (2.24) and (2.2) ensure that

$$
\begin{align} \mathcal{W}_{1,\Phi_{1}\bullet\Phi_{2}}\mathcal{W}_{\mathcal{L}(\Phi_{3}),\Phi_{3}} = \mathcal{W}_{1,\Phi_{1}}\mathcal{W}_{1,\Phi_{2}}\mathcal{W}_{\mathcal{L}(\Phi_{3}),\Phi_{3}} = \mathcal{W}_{1,\Phi_{1}}\mathcal{W}_{\mathcal{L}(\Phi_{3}),\Phi_{2}\bullet\Phi_{3}}. \tag{2.28} \end{align}
$$

In addition, observe that (2.24) and (2.2) demonstrate that

$$
\begin{align} \begin{aligned} \mathcal{W}_{1,\Phi_{1}}\boldsymbol{B}_{\mathcal{L}(\Phi_{3}),\Phi_{2}} + \boldsymbol{B}_{1,\Phi_{1}\bullet\Phi_{2}} &= \mathcal{W}_{1,\Phi_{1}}\mathcal{W}_{1,\Phi_{2}}\boldsymbol{B}_{\mathcal{L}(\Phi_{3}),\Phi_{3}} + \mathcal{W}_{1,\Phi_{1}}\boldsymbol{B}_{1,\Phi_{2}} + \boldsymbol{B}_{1,\Phi_{1}} \\ &= \mathcal{W}_{1,\Phi_{1}}\left(\mathcal{W}_{1,\Phi_{2}}\boldsymbol{B}_{\mathcal{L}(\Phi_{3}),\Phi_{3}} + \boldsymbol{B}_{1,\Phi_{2}}\right) + \boldsymbol{B}_{1,\Phi_{1}} \\ &= \mathcal{W}_{1,\Phi_{1}}\boldsymbol{B}_{\mathcal{L}(\Phi_{3}),\Phi_{2}\bullet\Phi_{3}} + \boldsymbol{B}_{1,\Phi_{1}}. \end{aligned} \tag{2.29} \end{align}
$$

Combining this and (2.28) with (2.27) proves that for all $k \in \{1, 2, \ldots, \mathcal{L}(\Phi_1) + \mathcal{L}(\Phi_3) - 1\}$ it holds that

$$
\left(\mathcal{W}_{k, (\Phi_1 \bullet \Phi_2) \bullet \Phi_3}, \boldsymbol{B}_{k, (\Phi_1 \bullet \Phi_2) \bullet \Phi_3}\right) = \left(\mathcal{W}_{k, \Phi_1 \bullet (\Phi_2 \bullet \Phi_3)}, \boldsymbol{B}_{k, \Phi_1 \bullet (\Phi_2 \bullet \Phi_3)}\right). \tag{2.30}
$$

This and (2.23) imply that

$$
(\Phi_1 \bullet \Phi_2) \bullet \Phi_3 = \Phi_1 \bullet (\Phi_2 \bullet \Phi_3). \tag{2.31}
$$

The proof of Lemma 2.1.3 is thus complete. $\square$

## Lemma 2.1.4. Let $\Phi_1, \Phi_2, \Phi_3 \in \mathbb{N}$ satisfy $\mathcal{I}(\Phi_1) = \mathcal{O}(\Phi_2)$, $\mathcal{I}(\Phi_2) = \mathcal{O}(\Phi_3)$, and $\mathcal{L}(\Phi_2) > 1$ (cf. Definition 1.3.1). Then

$$
(\Phi_1 \bullet \Phi_2) \bullet \Phi_3 = \Phi_1 \bullet (\Phi_2 \bullet \Phi_3). \tag{2.32}
$$

(cf. Definition 2.1.1).

*Proof of Lemma 2.1.4.* Note that the fact that for all $\Psi, \Theta \in \mathbb{N}$ it holds that $\mathcal{L}(\Psi \bullet \Theta) = \mathcal{L}(\Psi) + \mathcal{L}(\Theta) - 1$ ensures that

$$
\begin{align*}
\mathcal{L} ( ( \Phi_1 \bullet \Phi_2 ) \bullet \Phi_3 ) &= \mathcal{L} ( \Phi_1 \bullet \Phi_2 ) + \mathcal{L} ( \Phi_3 ) - 1 \\
&= \mathcal{L} ( \Phi_1 ) + \mathcal{L} ( \Phi_2 ) + \mathcal{L} ( \Phi_3 ) - 2 \\
&= \mathcal{L} ( \Phi_1 ) + \mathcal{L} ( \Phi_2 \bullet \Phi_3 ) - 1 \\
&= \mathcal{L} ( \Phi_1 \bullet ( \Phi_2 \bullet \Phi_3 ) )
\end{align*}
\tag{2.33}
$$

(cf. Definition 2.1.1). Furthermore, observe that (2.2) shows that for all $k \in \{1, 2, \ldots, \mathcal{L}(\Phi_1 \bullet \Phi_2)\} + \mathcal{L}(\Phi_3)$ it holds that

$$
\begin{align*}
& \left( \mathcal{W}_{k, (\Phi_1 \bullet \Phi_2) \bullet \Phi_3}, \boldsymbol{B}_{k, (\Phi_1 \bullet \Phi_2) \bullet \Phi_3} \right) \\
&= \left\{\begin{array}{ll}
\left( \mathcal{W}_{k, \Phi_3}, \boldsymbol{B}_{k, \Phi_3} \right) & : k < \mathcal{L}(\Phi_3) \\
\left( \mathcal{W}_{1, \Phi_1 \bullet \Phi_2} \mathcal{W}_{\mathcal{L}(\Phi_3), \Phi_3}, \mathcal{W}_{1, \Phi_1 \bullet \Phi_2} \boldsymbol{B}_{\mathcal{L}(\Phi_3), \Phi_3} + \boldsymbol{B}_{1, \Phi_1 \bullet \Phi_2} \right) & : k = \mathcal{L}(\Phi_3) \\
\left( \mathcal{W}_{k - \mathcal{L}(\Phi_3) + 1, \Phi_1 \bullet \Phi_2}, \boldsymbol{B}_{k - \mathcal{L}(\Phi_3) + 1, \Phi_1 \bullet \Phi_2} \right) & : k > \mathcal{L}(\Phi_3).
\end{array}\right.
\end{align*}
\tag{2.34}
$$

Moreover, note that (2.2) and the assumption that $\mathcal{L}(\Phi_2) > 1$ ensure that for all $k \in \mathbb{N} \cap (\mathcal{L}(\Phi_3), \mathcal{L}(\Phi_1 \bullet \Phi_2 \bullet \Phi_3)]$ it holds that

$$
\begin{align*}
& \left( \mathcal{W}_{k - \mathcal{L}(\Phi_3) + 1, \Phi_1 \bullet \Phi_2}, \boldsymbol{B}_{k - \mathcal{L}(\Phi_3) + 1, \Phi_1 \bullet \Phi_2} \right) \\
&= \left\{\begin{array}{ll}
\left( \mathcal{W}_{k - \mathcal{L}(\Phi_3) + 1, \Phi_2}, \boldsymbol{B}_{k - \mathcal{L}(\Phi_3) + 1, \Phi_2} \right) & : k - \mathcal{L}(\Phi_3) + 1 < \mathcal{L}(\Phi_2) \\
\left( \mathcal{W}_{1, \Phi_1} \mathcal{W}_{\mathcal{L}(\Phi_2), \Phi_2}, \mathcal{W}_{1, \Phi_1} \boldsymbol{B}_{\mathcal{L}(\Phi_2), \Phi_2} + \boldsymbol{B}_{1, \Phi_1} \right) & : k - \mathcal{L}(\Phi_3) + 1 = \mathcal{L}(\Phi_2) \\
\left( \mathcal{W}_{k - \mathcal{L}(\Phi_3) + 1 - \mathcal{L}(\Phi_2) + 1, \Phi_1}, \boldsymbol{B}_{k - \mathcal{L}(\Phi_3) + 1 - \mathcal{L}(\Phi_2) + 1, \Phi_1} \right) & : k - \mathcal{L}(\Phi_3) + 1 > \mathcal{L}(\Phi_2)
\end{array}\right.
\end{align*}
$$

$$
= \left\{\begin{array}{ll}
\left( \mathcal{W}_{k - \mathcal{L}(\Phi_3) + 1, \Phi_2}, \boldsymbol{B}_{k - \mathcal{L}(\Phi_3) + 1, \Phi_2} \right) & : k < \mathcal{L}(\Phi_2) + \mathcal{L}(\Phi_3) - 1 \\
\left( \mathcal{W}_{1, \Phi_1} \mathcal{W}_{\mathcal{L}(\Phi_2), \Phi_2}, \mathcal{W}_{1, \Phi_1} \boldsymbol{B}_{\mathcal{L}(\Phi_2), \Phi_2} + \boldsymbol{B}_{1, \Phi_1} \right) & : k = \mathcal{L}(\Phi_2) + \mathcal{L}(\Phi_3) - 1 \\
\left( \mathcal{W}_{k - \mathcal{L}(\Phi_3) - \mathcal{L}(\Phi_2) + 2, \Phi_1}, \boldsymbol{B}_{k - \mathcal{L}(\Phi_3) - \mathcal{L}(\Phi_2) + 2, \Phi_1} \right) & : k > \mathcal{L}(\Phi_2) + \mathcal{L}(\Phi_3) - 1.
\end{array}\right.
\tag{2.35}
$$
