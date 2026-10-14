expansion S-boxes will introduce significant complexities in your S-box design. Therefore straight S-boxes are far more common.

# 4.8.2 Cryptographic Properties of S-Boxes

While many of the Boolean function properties discussed in previous sections have conceptual equivalences when applied to S-boxes, there are fundamental differences in the manner by which these properties are derived. As an S-box is comprised of a number of component Boolean functions, it is important to observe that when considering the cryptographic properties of an S-box, it is not sufficient to consider the cryptographic properties of the component Boolean functions individually. Rather, it is also necessary to consider the cryptographic properties of all the linear combinations of the component functions. This is illustrated in the following selection of relevant S-box properties.

An n × m S-box which is balanced is one whose component Boolean functions and their linear combinations are all balanced. Because of this balance, there does not exist an exploitable bias in that the equally likely number of output bits over all output vector combinations ensures that an attacker is unable to trivially approximate the functions or the output.

The well-known concept of confusion due to Shannon [11,12] is described as a method for ensuring that in a cipher system a complex relationship exists between the ciphertext and the key material. This notion has been extrapolated to mean that a significant reliance on some form of substitution is required as a source of this confusion. The confusion in a cipher system is achieved through the use of nonlinear components. As expected, S-boxes tend to provide the main source of nonlinearity to cryptographic cipher systems. We now define the measure of nonlinearity for an n × m S-box.

**Definition 4.59:** *The nonlinearity of an n × m S-box S, denoted by N_{S_{n,m}} is defined as the minimum nonlinearity of each of its component output Boolean functions and their linear combinations. Let S = (s₁, s₂, ..., sₘ) where sᵢ (i = 1, ..., m) are n-variable Boolean functions. Let hⱼ be the set of linear combinations of sᵢ (i = 1, ..., m) (which includes the functions sᵢ). Then the nonlinearity of S can be expressed as follows:*

$N_{S_{n,m}} = \min_{h} \{ N_{S_{n,m}} (h_j) \} \quad (j = 1, ..., 2^m - 1). \tag{4.35}$

Clearly, as n and m increase, the task of merely computing the nonlinearity value of an n × m S-box quickly becomes computationally infeasible. The importance of this property for the security of cipher systems becomes evident in the next section when we discuss some of the effective cryptanalytic attacks which exist.