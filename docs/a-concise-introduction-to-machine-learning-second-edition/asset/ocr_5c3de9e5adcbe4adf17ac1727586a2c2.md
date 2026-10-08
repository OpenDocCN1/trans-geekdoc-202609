![](bbox=[0.258, 0.165, 0.741, 0.493])

Figure 9.8: Basis functions and bias of an autoencoder with ten hidden neurons.

to the hidden neurons. While nearly all digits are present close to zero, near one some digits are dominant. This means these neurons “fire” for particular digits.

The following table indicates for which digits an individual neuron “fires”.

| Neuron | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---||
| 1 | | | | | | | | | | |
| 2 | | | | | | | | | | |
| 3 | | | | | | | | | | |
| 4 | | | | | | | | | | |
| 5 | | | | | | | | | | |
| 6 | | | | | | | | | | |
| 7 | | | | | | | | | | |
| 8 | | | | | | | | | |
| 9 | | | | | | | | | | |
| 10 | | | | | | | | | | |

The table can also be read in the other direction telling the input from which neurons is necessary to construct a particular digit. For example, digit