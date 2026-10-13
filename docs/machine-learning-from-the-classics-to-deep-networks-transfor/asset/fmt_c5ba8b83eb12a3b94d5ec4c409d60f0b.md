
The interested reader will find more information concerning kernels and their construction in, for example, [52,106,112].

### String kernels

So far, our discussion has been focused on input data that were vectors in a Euclidean space. However, as we have already pointed out, the input data need not necessarily be vectors, and they can be elements of more general sets.

Let us denote by $\mathcal{S}$ an alphabet set; that is, a set with a finite number of elements, which we call `symbols`. For example, this can be the set of all capital letters in the Latin alphabet. Bypassing the path of formal definitions, a `string` is a finite sequence of any length of symbols from $\mathcal{S}$. For example, two cases of strings are

$T_1 = \text{“MYNAMEISSERGIOS”}, \quad T_2 = \text{“HERNAMEISDESPOINA”}$.

In a number of applications, such as in text mining, spam filtering, text summarization, and bioinformatics, it is important to quantify how “similar” two strings are. However, kernels, by their definition, are similarity measures; they are constructed so as to express inner products in the high-dimensional feature space. An inner product is a similarity measure. Two vectors are most similar if they point to the same direction. Starting from this observation, there has been a lot of activity on defining kernels that measure similarity between strings. Without going into details, let us give such an example.

Let us denote by $\mathcal{S}^*$ the set of all possible strings that can be constructed using symbols from $\mathcal{S}$. Also, a string `s` is said to be a `substring` of `x` if $x = bsa$, where `a` and `b` are other strings (possibly empty) from the symbols of $\mathcal{S}$. Given two strings $x, y \in \mathcal{S}^*$, define

$$
\kappa(x,y) := \sum_{s \in \mathcal{S}^*} w_s \phi_s(x) \phi_s(y),
$$

where $w_s \ge 0$, and $\phi_s(x)$ is the number of times the substring `s` appears in `x`. It turns out that this is indeed a kernel, in the sense that it complies with the condition in (11.10); such kernels constructed from strings are known as `string kernels`.

Obviously, a number of different variants of this kernel are available. The so-called `k`-`spectrum` kernel considers common substrings only of length `k`. For example, for the two strings given before, the value of the 6-spectrum string kernel in Eq. (11.15) is equal to one (one common substring of length 6 is identified and appears once in each one of the two strings: “NAMEIS”). The interested reader can obtain more on this topic from, for example, [106]. We will use the notion of the string kernel in the case study in Section 11.15.

## 11.6 Representer theorem

The theorem to be stated in this section is of major importance from a practical point of view. It allows us to perform `empirical` loss function optimization, based on a finite set of training samples, in a very efficient way even if the function to be estimated belongs to a very high (even infinite)-dimensional RKHS $\mathbb{H}$.

**Theorem 11.2**

Let

$\Omega : [0, +\infty) \mapsto \mathbb{R}$

be an arbitrary strictly monotonic increasing function. Let also

$\mathcal{L} : \mathbb{R}^2 \mapsto \mathbb{R} \cup \{\infty\}$

be an arbitrary loss function. Then each minimizer $f \in \mathbb{H}$ of the regularized minimization task
