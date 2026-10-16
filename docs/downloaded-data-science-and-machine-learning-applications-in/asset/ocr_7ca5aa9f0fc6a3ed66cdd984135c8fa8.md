The summary of the GMDH model's equations for two layers is expressed in Eqs. (7.24) to (7.26) as:

# Layer #1

Number of neurons: 2

$A = a_o + a_1 \times OCP + a_2 \times CLSWI + a_3 \times OCP \times CLSWI + a_4 \times (OCP)^2 + a_5 \times (CLSWI)^2 \tag{7.24}$

$a_0 = 0.03088 \quad a_1 = 0.94845 \quad a_2 = 0.04723$
$a_3 = 0.05133 \quad a_4 = 0.02253 \quad a_5 = 0.00212$

$B = -b_o + b_1 \times LSWIR + b_2 \times OCP - b_3 \times OCP \times LSWIR - b_4 \times (LSWIR)^2 + b_5 \times (OCP)^2 \tag{7.25}$

$b_0 = 0.00396 \quad b_1 = 0.00360 \quad b_2 = 0.99753$
$b_3 = 0.00431 \quad b_4 = 0.00041 \quad b_5 = 0.01058$

# Layer #2

Number of neurons: 1

$ORF = -c_o + c_1 \times B + c_2 \times A + c_3 \times A \times B - c_4 \times (B)^2 + c_5 \times (OCP)^2 \tag{7.26}$

$c_0 = 0.00038 \quad c_1 = 0.61360 \quad c_2 = 0.37942$
$c_3 = 409.55682 \quad c_4 = 205.30898 \quad c_5 = 204.23896$

where A and B are virtual independent inputs or nodal variables used in the GMDH neural network.

![](bbox=[0.25, 0.89, 0.75, 0.97])

Fig. 7.8. Schematic for the GMDH topology.