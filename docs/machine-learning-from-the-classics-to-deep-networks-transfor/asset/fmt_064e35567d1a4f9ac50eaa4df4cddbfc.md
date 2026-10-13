
$$
\sum\limits_{x_{3}}P(\mathbf{x}) = \psi^{(2)}(x_{1},x_{2},x_{4})\sum\limits_{x_{3}}\psi_{3}(x_{1},x_{3})\psi_{5}(x_{2},x_{3},x_{5})\psi_{6}(x_{3},x_{6}) = \psi^{(2)}(x_{1},x_{2},x_{4})\widetilde{\psi}^{(3)}(x_{1},x_{2},x_{5},x_{6}).
$$

![Equation](images/B9780443292385000226/si17.png)

Note that this summation is more difficult to perform. It involves four variables ($x_{1}, x_{2}, x_{5}, x_{6}$) besides $x_{3}$, which requires many more combination terms be computed than before. [Fig. 16.3](#Chp016_805-853_B9780443292385000226.xhtml#f0020)C shows the resulting equivalent graph, after eliminating $x_{3}$. Due to the resulting factor $\widetilde{\psi}^{(3)}(x_{1}, x_{2}, x_{5}, x_{6})$ *new* connections implicitly appear, known as *fill-in edges*. This is not a desired situation, as it introduces factors depending on new combinations of variables. Moreover, the new factor depends on four variables, and we know that the larger the number of variables, or the *domain* of the factor as we say, the larger the number of terms involved in the summations, which increases the computational load.
