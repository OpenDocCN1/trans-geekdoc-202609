
Fig. 21.1 Schematic diagram of single pull-off test for FRP to concrete

![](img/4048998719320644ee88964326fd7995_428_0.png)

The maximum transferable load is related to the mechanical characteristics of the materials and the interfacial fracture energy. Generally, \( P_{max} \) for FRP externally bonded reinforcement on supports made of brittle materials is defined as:

\( P_{max} = b_f \int_{0}^{\infty} \tau(x)dx \quad (21.1) \)

where \( b_f \) is the width of FRP plate, \( x \) is the longitudinal axis, and \( \tau(x) \) is the bond shear stress distribution along the interface. The interfacial fracture energy is defined as the work done by the interfacial shear stress until the complete separation of the FRP plate from concrete substrate. According to many studies in literature, the maximum transferable load is directly proportional to the square root of the interfacial fracture energy, \( \sqrt{G_f} \), regardless of the shape of the bond-slip curve [36]. The interfacial fracture energy is defined as:

\( G_f = \int_{0}^{\infty} \tau(s)ds \quad (21.2) \)

where \( s \) represents the FRP local slip. The general expression for \( P_{max} \) (debonding load) is derived as a function of \( G_f \) and material properties as follows:

\( P_{max} = b_f \sqrt{2E_p t_p G_f} \quad (21.3) \)

where \( E_p \) and \( t_p \) are elastic modulus and thickness of the FRP, respectively. The fracture energy can be estimated as:

\( G_f = k_b k_G \sqrt{f_c f_{ut}} \quad (21.4) \)

in which \( k_b \) is a width factor coefficient for considering the effect of reinforcement width on \( P_{max} \). \( k_G \) is a calibration parameter, which is determined through experimental results of bond tests, \( f_c \) is the compressive strength and \( f_{ut} \) is the tensile strength of the concrete substrate.

## 21.2.1 Existing Bond Strength Models

Since the 1980s many researchers have developed various equations for predicting bond strength between FRP and concrete substrate, including Van Gemert [9], Tanaka [10], Hiroyuki and Wu [11], Maeda et al. [5], Neubauer and Rostasy [12], Khalifa et al. [13], Adhikary and Mutsuyoshi [14], Chen and Teng [8], De Lorenzis et al. [15], Yang et al. [16], Izumo (from [17]), Iso (from [17]), Sato (from [17]), Dai et al. [18], Lu et al. [19], Camli and Binici [20]. Furthermore, the international federation for structural concrete (fib) [37] and CNR-DT200/2004 [38] design guidelines also present different formulae for estimating the bond strength of FRP-to-concrete elements. These equations are presented in Table 21.1. These relations are mainly based on either fracture mechanics based theory or on derived empirical equation calibrated with experimental datasets or combinations of the two. Most of these equations neglect the influence of the adhesive material properties. The accuracy of these empirical and combined theoretical and empirical models seems to be limited. These formulae were developed mainly based on regression analysis on experimental datasets and do not completely consider the nonlinearity between input and output parameters. Recently, the machine learning approaches have been widely applied in engineering problems. The main advantage of these approaches can be mentioned as: they consider all possible relations between input and output parameters and also unlike the regression approaches, checked different combinations of input parameters for estimating output parameter.

## 21.3 Methodology

The data mining approaches such as Artificial Neural Networks (ANN) and adaptive neuro-fuzzy inference system (ANFIS) have been employed as useful tools for modeling and forecasting complex engineering problems. Among these methods, the extreme learning machine (ELM) has not yet been widely applied in structural engineering. The description of the ELM is described in the following subsection. The ANN and ANFIS algorithms are also outlined in this section.

### 21.3.1 Extreme Learning Method

Extreme Learning Method (ELM) was firstly introduced by Huang et al. [33] as a fast computing learning algorithm. It uses single-layer feed-forward neural networks (SLFN) architecture to estimate an unknown function. The topological structure of ELM is depicted in the Fig. 21.2. Unlike the conventional methods of neural networks, ELM theories determine the output weights of SLFN analytically and generate the input weights randomly. The main advantages of ELM algorithm can be listed as:

Table 21.1 Existing equations for predicting maximum transferable load

| Model | Equation |
| :--- | :--- |
| Chen and Teng [8] | \( P_{max} = 0.315 B_p B_L \sqrt{f_{ck}} b_p L_e \)<br>\( L_e = \sqrt{E_p t_p / 4 G_f}; B_p = \sqrt{(2 - \frac{b_p}{t_p}) / ((1 + \frac{b_p}{t_p}))}; B_p = \begin{cases} 1 & \text{if } L_b \ge L_e \\ \sin \pi L_b / 2L_e & \text{if } L_b < L_e \end{cases} \) |
| De Lorenzis et al. [15] | \( P_{max} = b_p \sqrt{2 E_p t_p G_f} \)<br>\( G_f \): the fracture energy per unit area of the joint, assumed equal to 1.43 (N/mm) |
| Yang et al. [16] | \( P_{max} = (0.5 + 0.08 \sqrt{E_p t_p / 1000}) b_p L_e^{0.5} f_{cm} \) |
| Izumo (from [17]) | \( P_{max} = (3.8 f_{ck}^{2/3} + 15.2) L_b b_p E_p t_p \times 10^{-3} \) |
| Iso (from [18]) | \( P_{max} = b_p L_e^{0.93} f_{ck}^{0.44}; L_e = 0.125 (E_p t_p)^{0.57} \) |
| Sato (from [18]) | \( P_{max} = (b_p + 7.4) L_e^{2.68} f_{ck}^{0.2} E_p t_p \times 10^{-5}; L_e = 1.89 (E_p t_p)^{0.4} \) |
| Van Gemert [9] | \( P_{max} = 0.5 b_p L_b f_{cm} \) |
| Tanaka [10] | \( P_{max} = (6.13 - Ln(L_b)) b_p L_b \) |
| Hiroyuki and Wu [11] | \( P_{max} = b_p L_p (5.88 L_p^{-0.669}) \) |
| Maeda et al. [5] | \( P_{max} = 110.2 \times 10^{-6} E_p b_p L_e; L_e = e^{6.13 - 0.58 Ln(E_p t_p)} \) |
| Neubauer and Rostasy [12] | \(\begin{cases} P_{max} = 0.64 K_p b_p \sqrt{f_{cm}} E_p t_p & \text{if } L_b \ge L_e \\ P_{max} = 0.64 K_p b_p \sqrt{f_{cm}} E_p t_p \frac{L_p}{L_e} (2 - \frac{L_p}{L_e}) & \text{if } L_b < L_e \end{cases}\)<br>\( K_p = \sqrt{1.125 \left( (2 - \frac{b_p}{t_e}) / (1 + \frac{b_p}{400}) \right)} \) |
| Khalifa et al. [13] | \( P_{max} = 110.2 \times 10^{-6} (f_{ct} / 42)^{2/3} E_p t_p b_p L_e; L_e = e^{6.13 - 0.38 Ln(E_p t_p)} \) |

Table 21.1 (continued)

| Model | Equation |
| :--- | :--- |
| Adhikary and Mutsuyoshi [14] | \( P_{max} = b_p L_b \left( 0.25 f_{ck}^{2/3} \right) \) |
| Dai et al. [18] | \( P_{max} = (b_p + 7.4) \sqrt{2 E_p t_p G_f}; G_f = 0.514 f_c^{0.236} \) |
| Lu et al. [19] | \( P_{max} = B_1 b_p \sqrt{2 E_p t_p G_f} \)<br>\( L_e = a + (1/2\alpha) Ln(\lambda_1 + \lambda_2 \tan \lambda_2 a) / (\lambda_1 - \lambda_2 \tan \lambda_2 a); \lambda_1 = \sqrt{r_{max} S_0 E_p t_p} \)<br>\( \lambda_2 = \sqrt{r_{max}} / (S_f - S_0) E_p t_p; a = (1/\lambda_2) arcsin[0.99 \sqrt{S_f - S_0 / S_f}] \)<br>\( \tau_{max} = \alpha_1 b_p w_f; \alpha_1 = 1.5; G_f = 0.308 B_2^w \sqrt{f_{c0}} = 0.0195 b_w f_c; B_w = \sqrt{(2.25 - b_p/b)(b)(1.25 + p_p/1.25 + p_p/b)}; B_1 = sin(\pi L_b / 2L_e) \) |
| Camli and Binici [20] | \( P_{max} = \sqrt{\pi r_f} \sqrt{E_p t_p} tanh(\theta L_b / L_e) \)<br>\( L_e = \sqrt{E_p t_p / f_c}; \theta = \sqrt{t_f / (\sigma_{st} f_c)}; t_f = 3.5 f_c^{0.19}; \sigma_{ut} = f_c^u (L_b / L_0)^b (b_p)^Y; \alpha = -0.4; \beta = 0.8; \gamma = 0.4 \) |
| fib model [37] | \(\begin{cases} P_{max} = 0.64 \alpha k_c k_p b_p \sqrt{f_{cm} E_p t_p} \text{ if } L_b \ge L_e \\ P_{max} = 0.64 \alpha k_c k_p b_p \sqrt{f_{cm} E_p t_p} (L_b / L_e) \text{ if } L_b < L_e \\ K_p = 1.06 \sqrt{(2 - b_p / b_c)} / (1 + b_p / 400); \alpha = 1; k_c = 1 \end{cases}\) |
| CNR-DT200/2004 [38] | \( P_{max} = b_p \sqrt{2 E_p t_p K_b K_v K_s \sqrt{f_c^2}} \)<br>\( K_t = \begin{cases} 1 & \text{if } L \ge L_e \\ L_b / L_c (2 - L_b / L_e) & \text{if } L < L_e \end{cases}; K_b = \begin{cases} \sqrt{(2 - 0.33) / (1 + b_p / 400)} & \text{if } b_p / b_c < 0.33 \\ \sqrt{(2 - b_p / b_c) / (1 + b_p / 400)} & \text{if } b_p / b_c \ge 0.33 \end{cases} \)<br>\( K_G = 0.03; L_e = \sqrt{E_p t_p / 2t_f} \) |

![](img/4048998719320644ee88964326fd7995_432_0.png)

Fig. 21.2 The topological structure of the extreme learning machine network

the least human interventions, favorable universal capability, fast learning speed and suitability for activation and also kernel functions [34].

To explain the ELM algorithm, let suppose a set of input and output variables in a database as follows:

```
D = \{(x_i, y_i)\}_{i=1}^N \quad (21.5)
```

where $x_i$ is the input vector, $y_i$ is the output vector and $N$ is the number of observations. As stated, the ELM employs the SLFN to find the relation between input and output variables as:

```
Y = \sum_{i=1}^{L} \beta_i G(\omega_i, x_j, b_i) \quad j = 1, \dots, N \quad (21.6)
```
