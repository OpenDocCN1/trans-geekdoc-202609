![](bbox=[0.13, 0.108, 0.865, 0.18])

# Fig. 7.16: Graphical interface of RS-flip-flop and time diagrams describing its operation

The first matrix consists of N×M with element RS flip-flops (where N×M is the dimension of the first matrix A1). Thus, the first matrix consists of N×M inputs and the same number of outputs.

The second A2 matrix has the same dimension as the first A1 matrix. Each output of the first matrix is connected to the corresponding input of the second A2 matrix. In the previous sections, the second matrix A2 is represented as a two-dimensional shift register. Therefore, for its modelling, a one-dimensional reverse shift register was initially implemented. At first, one bit of such a register was described. Its main element is the controlled D-flip-flop (Fig. 7.17).

This controlled D-flip-flop is the main element of one bit of the second A2 matrix (Fig. 7.18).

Using the hierarchical principle of creating a VHDL project, a one-dimensional reverse shift register (Fig. 7.19), from which a two-dimensional reverse shift register (Fig. 7.20) were realised. The resulting two-dimensional reverse shift register is the second A2 matrix.

The resulting time diagrams show the operation of the second A2 matrix in one direction of the shift. The model has 8×8 dimension and 64 outputs as in the first A1 matrix.

![](bbox=[0.13, 0.585, 0.865, 0.675])

# Fig. 7.17: Graphic interface of the controlled D-flip-flop

![](bbox=[0.13, 0.725, 0.865, 0.845])

# Fig. 7.18: Graphic interface of one digit of the second A2 matrix and time diagram of its operation