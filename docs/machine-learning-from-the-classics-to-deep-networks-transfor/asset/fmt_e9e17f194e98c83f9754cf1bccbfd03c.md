
$$
\max_{x_1}\max_{\mathbf{x}_A \in V_A}\psi_A(x_1,\mathbf{x}_A) = \max_{x_1}\max_{x_2,x_3,x_4}f_a(x_1,x_2,x_3,x_4)f_c(x_3)\max_{x_7,x_8}f_d(x_4,x_7,x_8) \times \max_{x_9,x_{10}}f_e(x_4,x_9,x_{10})\max_{x_5,x_6}f_b(x_2,x_6,x_5).
$$

![Equation](images/B9780443292385000214/si311.png)(15.58)

Eq. [(15.58)](#Chp015_755-803_B9780443292385000214.xhtml#deq84) suggests that everything that was said before for the sum-product message passing algorithm holds true here, provided we replace summations with the max operations, and the definitions of the messages passed between nodes change to

$$
\mu_{x \rightarrow f}(x) = \prod_{s:f_s \in \mathcal{N}(x) \smallsetminus f}\mu_{f_s \rightarrow x}(x),
$$

![Equation](images/B9780443292385000214/si312.png)(15.59)

and

![Equation](images/B9780443292385000214/fx010.jpg)(15.60)

with the same definition of symbols as for Eq. [(15.50)](#Chp015_755-803_B9780443292385000214.xhtml#deq73). Then the mode of $P(\mathbf{x})$ is given by
