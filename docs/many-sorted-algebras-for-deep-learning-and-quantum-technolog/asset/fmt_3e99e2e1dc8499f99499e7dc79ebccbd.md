
4. Generating function: `e^((2*x*t - t^2))` ![Equation](Images/F000102si24.png) times the sum ∑ ![Equation](Images/F000102si25.png) `(t^(k) / k! Hk)`, k=0, 1, 2, …

When they are normalized, they are symbolized by `Hn`, become an ON basis (not weighted and no longer polynomials) for `L2` and are given by `Hn = e^(-1/2*x^2) h_n / (2^(n) n! (pi)^(1/2))^(1/2)` ![Equation](Images/F000102si26.png). These are called Hermite ON functions.

Also for the Laguerre polynomials, `y = Ln(x)`, they satisfy the following:

1. Differential equation: `x y'' + (1 - x) y' + n y = 0`, x in `[0, infinity)`, or in terms of Sturm–Liouville `(e^(-x) x y')' + n e^(-x) y = 0`.

2. Rodrigues formula: `Ln(x) = [(d/dx - 1)^(n)] x^(n) / n!`.

3. Difference equation: `L(n+1)(x) = [(2 n + 1 - x) Ln(x) - n L(n - 1)(x)] / (n + 1)`, for n=1, 2, 3, 4, …

4. Generating function: Sum, `∑ t^(n) L_n(x) = (1 - t)^(-1) e^(-t x / (1 - t))` ![Equation](Images/F000102si27.png), n=0, 1, 2, …

A second-order linear homogenous DE can be represented as a Sturm–Liouville DE by defining an integrating factor `p`. The method is outlined below, more rigorously. For a linear operator, `L(y) = a y'' + b y' + c y`, if `p = e^(∫ (b - a') / a dx)` ![Equation](Images/F000102si28.png) is finite over an interval `I`, and `V` is a vector space of functions such that

1. `V` is invariant under `L`.
2. For every `y` in `V`, the integral of `p y^2` over `I` is finite.
3. For `u` and `y` in `V`, the difference of `p a (u' y - u y') = p a (u' y - u y')` evaluated at the end points of `I` vanishes, then `L` is self-adjoint with respect to the inner product `<y, u> = ∫ p y u dx`.

### References
* [Birkhoff and Rota, 1978](#AppendixG_387-389_B9780443136979000102.xhtml#BIB_1) Birkhoff G, Rota G-C. *Ordinary Differential Equations* 3rd ed. John Wiley and Sons 1978;.
* [Bochner, 1929](#AppendixG_387-389_B9780443136979000102.xhtml#BIB_2) Bochner S. Uber Sturm-Liouville. *Plansysteme Math Z.* 1929;29.

# Index
*Note*: Page numbers followed by “*f*” refer to figures.

## A
*   A\* homomorphism, [158](#Ch008_145-164_B9780443136979000059.xhtml#p0760)
*   Abelian group, [6](#Ch001_1-19_B9780443136979000199.xhtml#p0240), [10](#Ch001_1-19_B9780443136979000199.xhtml#p0465)
    *   structure, [321–322](#Ch017_307-325_B9780443136979000023.xhtml#p0420), [374](#FigureC1_373-376_B9780443136979000114.xhtml#p0020)
*   Absolute convergence, [151](#Ch008_145-164_B9780443136979000059.xhtml#p0315)
*   Accretive operator, [134](#Ch007_131-144_B9780443136979000205.xhtml#p0235), [241](#Ch013_231-253_B9780443136979000138.xhtml#p0445)
*   Activation function, [25](#Ch002_21-40_B9780443136979000266.xhtml#p0095), [27–28](#Ch002_21-40_B9780443136979000266.xhtml#p0135)
    *   for neural net, [28–30](#Ch002_21-40_B9780443136979000266.xhtml#s0035)
*   Active learning, [329](#Ch018_327-348_B9780443136979000163.xhtml#o0015)
*   Addition, [255](#Ch014_255-270_B978044313697900028X.xhtml#p0010)
*   Adiabatic quantum computing (AQC), [105–107](#Ch006_103-128_B9780443136979000217.xhtml#s0015), [327](#Ch018_327-348_B9780443136979000163.xhtml#p0010), [328](#Ch018_327-348_B9780443136979000163.xhtml#p0030)
*   Adiabatic theorem, [103](#Ch006_103-128_B9780443136979000217.xhtml#p0010), [124–128](#Ch006_103-128_B9780443136979000217.xhtml#s0060)
*   Affine line, [330–331](#Ch018_327-348_B9780443136979000163.xhtml#p0095)
*   Affine space, many-sorted algebra description of, [35–37](#Ch002_21-40_B9780443136979000266.xhtml#s0050)
*   Affine transformations for nodes within neural net, [24](#Ch002_21-40_B9780443136979000266.xhtml#s0025)
*   Algebraic solution to harmonic oscillator, [349–350](#Ch019_349-364_B9780443136979000278.xhtml#s0010)
*   Algebraic structures, [1–2](#Ch001_1-19_B9780443136979000199.xhtml#s0015), [191](#Ch011_191-216_B9780443136979000126.xhtml#s0010)
*   Almost periodic functions, [148–149](#Ch008_145-164_B9780443136979000059.xhtml#p0200)
*   Alternating multilinear functional, [84](#Ch005_83-101_B9780443136979000084.xhtml#p0035)
*   Amplitude amplification, [303–304](#Ch016_291-305_B9780443136979000060.xhtml#s0055), [304](#Ch016_291-305_B9780443136979000060.xhtml#p0470), [313–314](#Ch017_307-325_B9780443136979000023.xhtml#p0135)
*   Analytic function, [251](#Ch013_231-253_B9780443136979000138.xhtml#p0895)
*   Analytic functional calculus, [250](#Ch013_231-253_B9780443136979000138.xhtml#p0875)
*   Analytic vector bundles, [182–183](#Ch010_171-188_B9780443136979000047.xhtml#s0040)
*   Andreev effect, [120](#Ch006_103-128_B9780443136979000217.xhtml#p0510)
*   Andreev reflection, [117](#Ch006_103-128_B9780443136979000217.xhtml#p0455), [119](#Ch006_103-128_B9780443136979000217.xhtml#p0475)
*   Angular momentum, [264](#Ch014_255-270_B978044313697900028X.xhtml#p0380)
*   Anion, [113](#Ch006_103-128_B9780443136979000217.xhtml#p0295)
*   Annealing-type operations, [29–30](#Ch002_21-40_B9780443136979000266.xhtml#p0220)
*   Annihilation operator, [273](#Ch015_271-288_B9780443136979000291.xhtml#p0060), [273–274](#Ch015_271-288_B9780443136979000291.xhtml#p0070), [274–275](#Ch015_271-288_B9780443136979000291.xhtml#p0090), [276](#Ch015_271-288_B9780443136979000291.xhtml#p0130)
*   Anomaly detection, [95](#Ch005_83-101_B9780443136979000084.xhtml#p0430)
*   Antisymmetric Levi-Civita symbol, [90](#Ch005_83-101_B9780443136979000084.xhtml#p0255)
*   Antiunitary linear unitary operations, [81](#Ch004_57-81_B9780443136979000011.xhtml#p1005)
*   Antiunitary map, [81](#Ch004_57-81_B9780443136979000011.xhtml#p1005)
*   Approximate spectrum, [248](#Ch013_231-253_B9780443136979000138.xhtml#p0745)
*   Arbitrary data sets, [95](#Ch005_83-101_B9780443136979000084.xhtml#p0435)
*   Arbitrary elements, [196](#Ch011_191-216_B9780443136979000126.xhtml#p0220)
*   Arity, [3](#Ch001_1-19_B9780443136979000199.xhtml#p0055)
*   Arsenic (As), [114](#Ch006_103-128_B9780443136979000217.xhtml#p0360)
*   Arzela–Ascoli theorem, [384](#AppendixF_383-385_B9780443136979000229.xhtml#u0025)
*   Associative, commutative unital algebra, [42–43](#Ch003_41-55_B9780443136979000175.xhtml#p0110)
*   Associative algebra, [193](#Ch011_191-216_B9780443136979000126.xhtml#p0115)
*   Associative law, [154](#Ch008_145-164_B9780443136979000059.xhtml#p0600), [222](#Ch012_217-230_B9780443136979000254.xhtml#p0185)
*   Associativity, [374](#FigureC1_373-376_B9780443136979000114.xhtml#p0025)
*   Atlas, [177](#Ch010_171-188_B9780443136979000047.xhtml#p0225)
*   Atoms, basic structure of, [111–114](#Ch006_103-128_B9780443136979000217.xhtml#s0030)
*   Aufbau principle, [112](#Ch006_103-128_B9780443136979000217.xhtml#p0290)
*   Automorphism, [133](#Ch007_131-144_B9780443136979000205.xhtml#p0175)
*   Autonomous vehicles, [21](#Ch002_21-40_B9780443136979000266.xhtml#p0010)

## B
*   Backpropagation
    *   algorithms, [25](#Ch002_21-40_B9780443136979000266.xhtml#p0100)
    *   for neural net learning, [31–35](#Ch002_21-40_B9780443136979000266.xhtml#s0045)
*   Backward substitution, [234](#Ch013_231-253_B9780443136979000138.xhtml#p0140)
*   Baire category theorem, [384](#AppendixF_383-385_B9780443136979000229.xhtml#u0050)
*   Baire measurable set, [371](#FigureB1_369-372_B9780443136979000035.xhtml#p0085)
*   Banach algebras, [163](#Ch008_145-164_B9780443136979000059.xhtml#p0945)
    *   ideals in, [157–158](#Ch008_145-164_B9780443136979000059.xhtml#s0040)
    *   as many-sorted algebra, [51–52](#Ch003_41-55_B9780443136979000175.xhtml#s0040)
    *   spectrum in, [155–157](#Ch008_145-164_B9780443136979000059.xhtml#s0035)
    *   subgroup in, [149–151](#Ch008_145-164_B9780443136979000059.xhtml#s0020)
*   Banach space, [135](#Ch007_131-144_B9780443136979000205.xhtml#p0260), [241](#Ch013_231-253_B9780443136979000138.xhtml#p0440)
    *   many-sorted algebra description of, [49–51](#Ch003_41-55_B9780443136979000175.xhtml#s0035)
    *   rank, [145–147](#Ch008_145-164_B9780443136979000059.xhtml#s0010)
