# 2.1.2 Elementary properties of compositions of fully-connected feedforward ANNs

**Proposition 2.1.2** *(Properties of standard compositions of fully-connected feedforward ANNs)*. Let $\Phi, \Psi \in \mathbb{N}$ satisfy $\mathcal{I}(\Phi) = \mathcal{O}(\Psi)$ (cf. Definition 1.3.1). Then

+   1. it holds that
$$\mathcal{D}(\Phi \bullet \Psi) = (\mathbb{D}_0(\Psi), \mathbb{D}_1(\Psi), \dots, \mathbb{D}_{\mathcal{H}(\Psi)}(\Psi), \mathbb{D}_1(\Phi), \mathbb{D}_2(\Phi), \dots, \mathbb{D}_{\mathcal{L}(\Phi)}(\Phi)),$$ (2.3)
2. it holds that
$$[\mathcal{L}(\Phi \bullet \Psi) - 1] = [\mathcal{L}(\Phi) - 1] + [\mathcal{L}(\Psi) - 1],$$ (2.4)
3. it holds that
$$\mathcal{H}(\Phi \bullet \Psi) = \mathcal{H}(\Phi) + \mathcal{H}(\Psi),$$ (2.5)
4. it holds that
$$
\begin{aligned}
\mathcal{P}(\Phi \bullet \Psi) &= \mathcal{P}(\Phi) + \mathcal{P}(\Psi) + \mathbb{D}_1(\Phi) \big[ \mathbb{D}_{\mathcal{L}(\Psi)-1}(\Psi) + 1 \big] \\
&\quad - \mathbb{D}_1(\Phi) \big( \mathbb{D}_0(\Phi) + 1 - \mathbb{D}_{\mathcal{L}(\Psi)}(\Psi) \big[ \mathcal{L}(\Psi)-1 \big)(\Psi) + 1 \big) \big( \\
&\quad \le \mathcal{P}(\Phi) + \mathcal{P}(\Psi) + \mathbb{D}_1(\Phi) \mathbb{D}_{\mathcal{H}(\Psi)}(\Psi),
\end{aligned}
$$ (2.6)

+   5. it holds for all $a \in C(\mathbb{R}, \mathbb{R})$ that $\mathcal{R}_a^\mathbb{N}(\Phi \bullet \Psi) \in C(\mathbb{R}^{\mathcal{I}(\Psi)}, \mathbb{R}^{\mathcal{O}(\Phi)})$ and
$$\mathcal{R}_a^\mathbb{N}(\Phi \bullet \Psi) = [\mathcal{R}_a^\mathbb{N}(\Phi)] \circ [\mathcal{R}_a^\mathbb{N}(\Psi)]$$ (2.7)

*(cf. Definitions 1.3.4 and 2.1.1)*.

*Proof of Proposition 2.1.2*. Throughout this proof, let $L = \mathcal{L}(\Phi \bullet \Psi)$ and for every $a \in C(\mathbb{R}, \mathbb{R})$ let

$$X_a = \{ x = (x_0, x_1, \dots, x_L) \in \mathbb{R}^{\mathbb{D}_{\mathcal{I}(\Phi \bullet \Psi)}(\Phi \bullet \Psi)} \times \mathbb{R}^{\mathbb{D}_1(\Phi \bullet \Psi)} \times \dots \times \mathbb{R}^{\mathbb{D}_L(\Phi \bullet \Psi)} : 
(\forall k \in \{1, 2, \dots, L\} : x_k = \mathfrak{H}_{a, \lceil L \rceil_L(k) + \operatorname{id}_{\mathbb{N}} \lceil L \rceil_L(k), \mathbb{D}_k(\Phi \bullet \Psi)}(\mathcal{V}_{k, \Phi \bullet \Psi} x_{k-1} + \mathcal{B}_{k, \Phi \bullet \Psi}) \} \} .$$ (2.8)

Note that the fact that $\mathcal{L}(\Phi \bullet \Psi) = \mathcal{L}(\Phi) + \mathcal{L}(\Psi) - 1$ and the fact that for all $\Theta \in \mathbb{N}$ it holds that $\mathcal{H}(\Theta) = \mathcal{L}(\Theta) - 1$ establish items (ii) and (iii). Observe that item (iii) in Lemma 1.3.3 and (2.2) show that for all $k \in \{1, 2, \dots, L\}$ it holds that

$$
\mathcal{V}_{k, \Phi \bullet \Psi} = 
\begin{cases}
\mathbb{R}^{\mathbb{D}_k(\Psi) \times \mathbb{D}_{k-1}(\Psi)} & : k < \mathcal{L}(\Psi) \\
\mathbb{R}^{\mathbb{D}_1(\Phi) \times \mathbb{D}_{\mathcal{L}(\Psi)-1}(\Psi)} & : k = \mathcal{L}(\Psi) \\
\mathbb{R}^{\mathbb{D}_{k-\mathcal{L}(\Psi)+1}(\Phi) \times \mathbb{D}_{k-\mathcal{L}(\Psi)}(\Phi)} & : k > \mathcal{L}(\Psi).
\end{cases}
$$ (2.9)