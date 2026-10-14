where l and u are integers, the subscripts l = {0 ≤ x2m(n) ≤1} with l ∈ [1,v], and u = {0 ≤ y2m(n) ≤1} with u ∈ [1,w] define the rows and columns respectively to determine the positions of the elements for the new DNA matrix G. This matrix contains the same elements as matrix D (10.10). The initial coordinates g_{l,u} allow the finding of the initial position of a sequence until 16 positions are completed and the last position is referred to as g_{l,u+15},

$G = \begin{pmatrix} g_{l,u} & g_{l,u+1} & \dots & g_{l,u+31} \\ g_{l+1,u} & g_{l+1,u+1} & \dots & g_{l+1,u+31} \\ \vdots & \vdots & \ddots & \vdots \\ g_{l+23,u} & g_{l+23,u+1} & \dots & g_{l+23,u+31} \end{pmatrix} \tag{10.17}$

The vector F contains m(t), and the confusion process is calculated using Equations 10.14 through 10.17. We obtain the new row vector H. The first element h_u of vector H contains the first element f_j of vector F, and the last element f_{j+15} is referred to as h_{u+15},

$H = [f_j, f_{j+2},..., f_{j+15}] = [g_{l,u}, g_{l,u+1},..., g_{l,u+15}] = [h_u, h_{u+1},..., h_{u+15}] \tag{10.18}$

# 10.5.2.2 Reverse Process of Diffusion Method

This method uses the MACM CS in DV standard (10.15), and one state z_{2m(n)} of the MACM CS in DV depurated (10.16). We calculated a numerical arrangement to generate values from 0 to 65535 and the result is defined by

$O_{ex(u2)} = z_{2m(n)}2^k = [(1.3 + z_{2(n)})1000 - floor((1.3 + z_{2(n)})1000)]2^k, \tag{10.19}$

where the vector P defines the 16 equivalent elements,

$P = [p_1, p_2, ..., p_{16}] \tag{10.20}$

The OR-EX logic operation is calculated on each element of vector H with respect to vector P. Finally, the decrypted message m'(t) is found and the data are contained in the vector Q,

$Q = [h_1 \oplus p_1, h_2 \oplus p_2, ..., h_{16} \oplus p_{16}] = [q_1, q_2, ..., q_{16}] \tag{10.21}$

# 10.5.3 Transmission of Recovered Message

Once the decrypted message is recovered, we configured the second SPI protocol using U2 to receive the data in 16 bits. The hardware of Mikromedia U2 is