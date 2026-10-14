
The biological nervous system, which comprises several nodes and replicates biological neurons in the human brain, served as the model for the ANN classification system. The nodes, or neurons, are interconnected and engage in communication. The nodes receive the input data, analyze it, and then transform it before sending it across the connection to other neurons as an output. Each connection will have a weight that may be changed. Every node’s output is processed via the weight. A hidden layer is a layer that resides between the input and the output and conducts calculations on weighted inputs to generate the net input.

The real output is subsequently created by combining the activation function with the net input. Input and output nodes added together may equal one or up to two hidden layers. The network randomly adds weight while passing from the input to the output layer, and the result is sent to the next nodes. The ultimate result is compared with the objective. If the output does not match the goal, it propagates backward and modifies the weights. The architecture of an ANN is shown in [Figure 78.1](#ch78.xhtml#fig78_1). [Figure 78.2](#ch78.xhtml#fig78_2) illustrates a suggested automated rice grain quality evaluation system based on ANN.

![Figure 78.1 ANN architecture](images/fig78_1_C.jpg)

[Figure 78.1 ANN architecture](#ch78.xhtml#R_fig78_1)

![Figure 78.2 Flow chart of the process](images/fig78_2_B.jpg)

[Figure 78.2 Flow chart of the process](#ch78.xhtml#R_fig78_2)

Matta and Ponni, two widely consumed rice types, are the subjects of this research. As seen in [Table 78.1](#ch78.xhtml#tab78_1), there are four grades assigned to them. The rice is divided into two categories, Ponni rice, and Matta rice, using the mean RGB values of various images. [Figure 78.3](#ch78.xhtml#fig78_3) for the Ponni variety and [Figure 78.4](#ch78.xhtml#fig78_4) for the Matta type of rice show the test findings. The rice grains are divided into grades 1, 2, 3, and 4 based on geometrical characteristics.

[Table 78.1 Grade of rice grains](#ch78.xhtml#R_tab78_1)

| Grade || Type |
| --- | --- |
| 1 || Perfect small rice grains |
| 2 || Perfect large rice grains |
| 3 || Rice grains with impurities |
| 4 || Imperfect (mixed) rice grains |

![Figure 78.3 Test image for grade-2 Ponni rice](images/fig78_3_C.jpg)

[Figure 78.3 Test image for grade-2 Ponni rice](#ch78.xhtml#R_fig78_3)

![Figure 78.4 Test image for grade-2 Matta rice](images/fig78_4_C.jpg)

[Figure 78.4 Test image for grade-2 Matta rice](#ch78.xhtml#R_fig78_4)

## Results

The NN-toolbox of MATLAB is used to carry out the classification scheme for rice grains. The NN classifier system has utilized seven data sets. The ANN framework employed in this study is shown in [Figure 78.5](#ch78.xhtml#fig78_5). Seven characteristics have been considered inputs, while rice quality and variety have been considered outputs. To reach the best level of accuracy, this model comprises 48 hidden layers. [Figure 78.6](#ch78.xhtml#fig78_6) presents the outcomes of the NN classifier and regression plots are discussed as shown in [Figure 78.7](#ch78.xhtml#fig78_7).

![Figure 78.5 ANN framework](images/fig78_5_C.jpg)

[Figure 78.5 ANN framework](#ch78.xhtml#R_fig78_5)

![Figure 78.6 Grading of rice grains according to varieties using ANN classifier](images/fig78_6_C.jpg)

[Figure 78.6 Grading of rice grains according to varieties using ANN classifier](#ch78.xhtml#R_fig78_6)

![Figure 78.7 Regression plots](images/fig78_7_C.jpg)

[Figure 78.7 Regression plots](#ch78.xhtml#R_fig78_7)

The different rice seeds are classified on the basis of their perimeter assessment. [Table 78.2](#ch78.xhtml#tab78_2) details the intended value of pixels depending on the particle analysis for every rice seed in one sample image. [Table 78.3](#ch78.xhtml#tab78_3), differentiates the rice seeds among small, normal, large, and broken rice granules using the object detection method. The table also presents the values calculated in percentage depending on the total seeds in each sample using the machine-based system analysis. Further, [Table 78.4](#ch78.xhtml#tab78_4) states the values of different rice seeds as detected by a human inspector, with the corresponding percentage values concerning the total number of seeds present in the sample.

[Table 78.2 Analysis of rice seeds in a random sample](#ch78.xhtml#R_tab78_2)

| S. No. || Perimeter (pixels) |
| --- | --- |
| 1 || 198 |
| 2 || 198 |
| 3 || 176 |
| 4 || 199 |
| 5 || 198 |
| 6 || 236 |
| 7 || 227 |
| 8 || 114 |
| 9 || 177 |
| 10 || 121 |
| 11 || 206 |
| 12 || 190 |
| 13 || 209 |
| 14 || 209 |
| 15 || 116 |
| 16 || 203 |
| 17 || 223 |
| 18 || 226 |
| 19 || 187 |
| 20 || 225 |
| 21 || 237 |
| 22 || 211 |
| 23 || 148 |
| 24 || 216 |
| 25 || 196 |
| 26 || 218 |

[Table 78.3 Results of a random sample regarding the size of the rice seeds with percentage values](#ch78.xhtml#R_tab78_3)

| Sample no || Small seed || % || Normal seed || % || Large seed || % || Broken seed || % || Total seeds |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 3 || 10.71 || 15 || 53.57 || 3 || 10.71 || 7 || 25.00 || 28 |
| 2 || 4 || 12.90 || 20 || 64.52 || 2 || 6.45 || 5 || 16.13 || 31 |
| 3 || 2 || 7.69 || 16 || 61.54 || 2 || 7.69 || 6 || 23.08 || 26 |
| 4 || 2 || 6.25 || 19 || 59.37 || 3 || 9.37 || 8 || 25.00 || 32 |
| 5 || 3 || 10.00 || 19 || 63.33 || 2 || 6.67 || 6 || 20.00 || 30 |
| 6 || 2 || 6.45 || 18 || 58.06 || 4 || 12.90 || 7 || 22.58 || 31 |
| 7 || 2 || 7.41 || 18 || 66.67 || 4 || 14.81 || 3 || 11.11 || 27 |
| 8 || 3 || 10.34 || 19 || 65.52 || 3 || 10.34 || 4 || 13.79 || 29 |
| 9 || 4 || 13.79 || 19 || 65.52 || 2 || 6.90 || 4 || 13.79 || 29 |
| 10 || 2 || 6.90 || 17 || 58.62 || 4 || 13.79 || 6 || 20.69 || 29 |
| 11 || 2 || 6.67 || 18 || 60.00 || 5 || 16.67 || 5 || 16.67 || 30 |
| 12 || 2 || 6.67 || 18 || 60.00 || 4 || 13.33 || 6 || 20.00 || 30 |
| 13 || 2 || 6.25 || 20 || 62.50 || 2 || 6.25 || 8 || 25.00 || 32 |
| 14 || 4 || 13.33 || 17 || 56.67 || 3 || 10.00 || 6 || 20.00 || 30 |
| 15 || 2 || 6.67 || 18 || 60.00 || 4 || 13.33 || 6 || 20.00 || 30 |
| Average || 8.80% ||  || 61.05% ||  || 10.61% ||  || 19.52% ||  ||  |

[Table 78.4 Results of a random sample in terms of the size of the rice seeds with percentage values by Human inspector](#ch78.xhtml#R_tab78_4)

| Sample no || Small seed || % || Normal seed || % || Large seed || % || Broken seed || % || Total seeds |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 || 4 || 14.28 || 14 || 50.00 || 4 || 14.28 || 6 || 21.42 || 28 |
| 2 || 5 || 16.12 || 17 || 54.83 || 3 || 9.67 || 6 || 19.35 || 31 |
| 3 || 3 || 11.53 || 14 || 53.84 || 3 || 11.53 || 6 || 23.07 || 26 |
| 4 || 4 || 12.50 || 17 || 53.12 || 4 || 12.50 || 7 || 21.87 || 32 |
| 5 || 4 || 13.33 || 15 || 50.00 || 4 || 13.33 || 7 || 23.33 || 30 |
| 6 || 3 || 9.67 || 15 || 48.38 || 5 || 16.12 || 8 || 25.80 || 31 |
| 7 || 4 || 14.81 || 14 || 51.85 || 5 || 18.51 || 4 || 14.81 || 27 |
| 8 || 4 || 13.79 || 15 || 51.72 || 4 || 17.24 || 4 || 17.24 || 29 |
| 9 || 6 || 20.68 || 14 || 48.27 || 4 || 13.79 || 5 || 17.24 || 29 |
| 10 || 5 || 17.24 || 15 || 51.72 || 5 || 17.24 || 4 || 13.79 || 29 |
| 11 || 4 || 13.33 || 14 || 46.66 || 6 || 20.00 || 6 || 20.00 || 30 |
| 12 || 3 || 10.00 || 15 || 50.00 || 5 || 16.66 || 7 || 23.33 || 30 |
| 13 || 3 || 9.37 || 16 || 50.00 || 4 || 12.50 || 9 || 28.12 || 32 |
| 14 || 5 || 16.66 || 14 || 46.66 || 4 || 13.33 || 7 || 23.33 || 30 |
| 15 || 3 || 10.00 || 15 || 50.00 || 5 || 16.66 || 7 || 23.33 || 30 |
| Average || 50.46% ||  || 12.21% ||  || 16.48% ||  || 21.06% ||  ||  |
