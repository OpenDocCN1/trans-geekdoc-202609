

![](img/d6ed6c69a61b1252a9084096bb4904c6_129_0.png)

Fig. 7.16: Graphical interface of RS-flip-flop and time diagrams describing its operation

The first matrix consists of N×M with element RS flip-flops (where N×M is the dimension of the first matrix A1). Thus, the first matrix consists of N×M inputs and the same number of outputs.

The second A2 matrix has the same dimension as the first A1 matrix. Each output of the first matrix is connected to the corresponding input of the second A2 matrix. In the previous sections, the second matrix A2 is represented as a two-dimensional shift register. Therefore, for its modelling, a one-dimensional reverse shift register was initially implemented. At first, one bit of such a register was described. Its main element is the controlled D-flip-flop (Fig. 7.17).

This controlled D-flip-flop is the main element of one bit of the second A2 matrix (Fig. 7.18).

Using the hierarchical principle of creating a VHDL project, a one-dimensional reverse shift register (Fig. 7.19), from which a two-dimensional reverse shift register (Fig. 7.20) were realised. The resulting two-dimensional reverse shift register is the second A2 matrix.

The resulting time diagrams show the operation of the second A2 matrix in one direction of the shift. The model has 8×8 dimension and 64 outputs as in the first A1 matrix.

![](img/d6ed6c69a61b1252a9084096bb4904c6_129_1.png)

Fig. 7.17: Graphic interface of the controlled D-flip-flop

![](img/d6ed6c69a61b1252a9084096bb4904c6_129_2.png)

Fig. 7.18: Graphic interface of one digit of the second A2 matrix and time diagram of its operation

![](img/d6ed6c69a61b1252a9084096bb4904c6_130_0.png)

![](img/d6ed6c69a61b1252a9084096bb4904c6_130_1.png)

The third element of the system is the third matrix A3, by means of which the function of the area of intersection is determined at each time-step. Each elementary area is determined by a logic ‘1’ signal at the corresponding output of the second A2 matrix. Each signal of logical ‘1’ comes from the second A2 matrix. The third matrix A3 counts all the signals of the logical ‘1’ at its inputs.

The third A3 matrix was implemented on a hierarchical basis. The first scheme was implemented to count the number of units in the four-digit binary code. From the two four-bit circuits, a circuit was implemented for counting the ones in an eight-bit binary code. These schemes were implemented in accordance with the logical expressions described in the previous paragraph.

In accordance with this approach, a scheme for counting the number of units in a 64-bit binary code was implemented (Fig. 7.21). Its time diagrams are shown in Fig. 7.22.

![](img/d6ed6c69a61b1252a9084096bb4904c6_131_0.png)

Fig. 7.21: Graphic interface for counting the number of ones in 64-bit binary code

Fig. 7.22: Time diagrams of the counting scheme of the number of ones in a 64-bit binary code

The implementation of such a scheme required a large number of searches of outputs in the 32-bit codes at the input. This approach allows us to construct a scheme for calculating the number of ones in a code of any dimension.

The resulting schemes were implemented in CAD systems, such as WebPack and Vivado, which showed the cost of FPGA elements in the implementation of the system.

## 7.5 Selection and Storage of Patterns in UMFP

The chief importance lies in the formation of a vector of basic quantitative characteristics that describe the image after the implementation of a parallel shift. It is necessary to generate a form that is easily accessible and understandable and also, effectively stored in the memory of templates. In addition, the generated set of values should not cause problems when comparing. The comparison unit should be simple and perform with a minimal time spent.

In the electronic digital scheme, the received FAI is represented by a code that is divided into fields (Fig. 7.23), which determine the value of the function of the area of intersection at the appropriate time.

![](img/d6ed6c69a61b1252a9084096bb4904c6_132_0.png)

Fig. 7.23: The form of the function of the area of intersection for one of the directions of the shift

The number of functions of the area of intersection depends on the size of the image and the number of discretisation steps of the image field. Typically, a length corresponding to the width (height) of the image field is selected.

When the FAI vector is formed, a vector of the template is searched for, which is to be determined by it. For this, there is the task of efficiently locating and storing the template codes. There are several options for presenting the template codes. The easiest way to represent the codes is shown in Fig. 7.23.

Each field is the time-step number of the shift. The first coordinate is the step number of the shift, and the second coordinate is the code in this field. The search for the template code, which coincides with the code at the input, consists of a sequential search in memory. The implementation of this method consumes a lot of time, which dramatically reduces the performance of the recognition system.

The second option implements the creation of another code that has other meanings than the first version. The code structure is divided into a number of fields (Fig. 7.24). However, each field contains values that have a different value.

![](img/d6ed6c69a61b1252a9084096bb4904c6_132_1.png)

Fig. 7.24: The code structure based on the received function of the area of intersection for one direction of the shift

The code is also divided into code fields. Each field contains a $S_i^j$ value (where i is the number of partitions of the axis of the shift direction and j is the number of the partition field), which determines the curvature of the function of the area of intersection at the chosen increment. For example, the FAI(x) was obtained in the following values (Table 7.2):

Table 7.2: Example of FAI(x) values

| FAI(x) | 20 | 15 | 12 | 10 | 8 | 6 | 4 | 3 | 2 | 1 | 0 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |

For this example, we get the following values, which form the template code:

S_1^1 = \frac{20}{10} = 2

S_1^2 = \frac{10-6}{5} = 0.8 ; S_2^2 = \frac{6-0}{5} = 1.2

S_1^3 = \frac{20-10}{3} = 3.3 ; S_2^3 = \frac{10-4}{3} = 2 ; S_3^3 = \frac{4-1}{3} = 1

S_1^4 = \frac{20-12}{2} = 4 ; S_2^4 = \frac{12-8}{2} = 2 ; S_3^4 = \frac{8-4}{2} = 2 ; S_4^4 = \frac{4-2}{2} = 1

S_1^5 = \frac{20-12}{2} = 4 ; S_2^5 = \frac{12-8}{2} = 2 ; S_3^5 = \frac{8-4}{2} = 2 ; S_4^5 = \frac{4-2}{2} = 1 ;

S_5^5 = \frac{2-0}{2} = 1

With such an organisation, the code length may be less than that in the first method. In addition, this code allows determination of the scale changes in the shape of objects, as well as simplifies the process of the template code.

Along with little spending of time, this code requires additional non-complex computing resources. The memory devices with various forms of organisation can also be used.

Fields of vectors of template images and images at the input of the system are formed according to the principle, which is shown in Fig. 7.25.

| $V_{x=}$ | $S_1(1)$ | $S_2(1)$ | $S_3(1)$ | $S_4(1)$ | $S_5(1)$ | $S_6(1)$ | ... | $S_1(4)$ | $S_2(4)$ | ... | $S_4(1)$ |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| $V_{x=w}$ | $S_1(2)$ | $S_2(2)$ | $S_3(2)$ | $S_4(2)$ | $S_5(2)$ | $S_6(2)$ | ... | $S_1(4)$ | $S_2(4)$ | ... | $S_4(2)$ |
| . | . | . | . | . | . | . | ... | . | . | ... | . |
| . | . | . | . | . | . | . | ... | . | . | ... | . |
| . | . | . | . | . | . | . | ... | . | . | ... | . |
| $V_{x=w}$ | $S_1(w)$ | $S_2(w)$ | $S_3(w)$ | $S_4(w)$ | $S_5(w)$ | $S_6(w)$ | ... | $S_1(w)$ | $S_2(w)$ | ... | $S_4(w)$ |

Fig. 7.25: Structure of the field comparison in the image recognition system based on the parallel shift technology

The first one compares the $S_1^1$ parameter and selects those vectors in which coincidences occur within the error margin. Further, in the selected fields of vectors, the fields are compared by the $S_1^2$ and $S_2^2$ values and a group with matched mask values is singled out. Thus, there is a sequential sorting of each group of fields. The field group is determined by the superscript in each field. The value of the upper index indicates the number of fields in the group. For example, if the superscript is 3, then the group includes three values $S_1^3, S_2^3, S_3^3$.

There is a sequential sorting of each group of fields in parallel in all vectors and one vector is selected, which defines the image at the input of the recognition system.

