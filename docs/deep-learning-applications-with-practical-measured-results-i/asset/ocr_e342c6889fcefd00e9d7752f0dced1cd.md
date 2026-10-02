and GUM-S2 [22,23] and other bibliographies [19,24]. The GUM uncertainty framework has two main limitations [2,25]. The first limitation is the lack of generality of the procedure to obtain an interval to contain the values of the measurand with a stipulated coverage probability [25]. In the GUM uncertainty framework, the way a coverage interval is constructed to contain values of the measurand with a stipulated coverage probability is approximate [22]. The second limitation is that insufficient guidance is given for the multivariate case in which there is more than one measurand, namely, more than one output quantity [22,25]. In order to address these limitations, Working Group 1 of the Joint Committee for Guides in Metrology (JCGM) has produced two specific guidance documents, namely GUM-S1 and GUM-S2 [23,24], on the Monte Carlo method (MCM) for uncertainty evaluation and extensions to any number of measurands (output quantity), respectively [22].

The MCM provides a general approach to obtain a numerical representation G of the distribution function GY(η) for Y. The heart of the approach is making repeated draws from the probability density functions (PDFs) for the input variables Xi (or joint PDF for X) and the evaluation of the output quantity. Assignment of the PDFs for the input variables is dependent on each experiment. The same case applies to the evaluation of the output quantity. The distribution function GY(η) encodes all information known about the output quantity Y. Properties of Y can be approximated using GY(η). The quality of G depends on the number of draws made. The symbol y represent the output measurement results. It is determined by the input measurement results xi:

y = f(x1, ..., xN) (1)

The relationship between the PDF of output measurement results and input measurement results is:

gY(η) = ∫ gX1,...,XN(ξ1, ..., ξN) × δ[η − f(ξ1, ..., ξN)] dξ1 ... dξN (2)

where η denotes possible values that can be distributed to Y, δ[·] denotes the Dirac delta function.

Figure 1 provides an illustration of the propagation of distributions for input and output quantities. The expectation of the output quantities can be obtained by its PDF gY(η) as:

E(Yi) = ∫_{-∞}^{∞} ηi gYi(ηi) dηi (3)

![](bbox=[0.25, 0.6, 0.78, 0.85])

Figure 1. Illustration of the propagation of distributions for input quantities and the obtained output quantities [19].

The variance of the output quantities can be obtained by its PDF gY(η) as:

V(Yi) = ∫_{-∞}^{∞} [ηi − E(Yi)]² gYi(ηi) dηi (4)