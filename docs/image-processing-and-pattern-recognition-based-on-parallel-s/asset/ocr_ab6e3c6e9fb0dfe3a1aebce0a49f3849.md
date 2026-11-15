![](bbox=[0.143, 0.106, 0.854, 0.153])

Fig. 7.23: The form of the function of the area of intersection for one of the directions of the shift

The number of functions of the area of intersection depends on the size of the image and the number of discretisation steps of the image field. Typically, a length corresponding to the width (height) of the image field is selected.

When the FAI vector is formed, a vector of the template is searched for, which is to be determined by it. For this, there is the task of efficiently locating and storing the template codes. There are several options for presenting the template codes. The easiest way to represent the codes is shown in Fig. 7.23.

Each field is the time-step number of the shift. The first coordinate is the step number of the shift, and the second coordinate is the code in this field. The search for the template code, which coincides with the code at the input, consists of a sequential search in memory. The implementation of this method consumes a lot of time, which dramatically reduces the performance of the recognition system.

The second option implements the creation of another code that has other meanings than the first version. The code structure is divided into a number of fields (Fig. 7.24). However, each field contains values that have a different value.

![](bbox=[0.135, 0.555, 0.865, 0.6])

Fig. 7.24: The code structure based on the received function of the area of intersection for one direction of the shift

The code is also divided into code fields. Each field contains a Si^j value (where i is the number of partitions of the axis of the shift direction and j is the number of the partition field), which determines the curvature of the function of the area of intersection at the chosen increment. For example, the FAI(x) was obtained in the following values (Table 7.2):

Table 7.2: Example of FAI(x) values

| FAI(x) | 20 | 15 | 12 | 10 | 8 | 6 | 4 | 3 | 2 | 1 | 0 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |

For this example, we get the following values, which form the template code: