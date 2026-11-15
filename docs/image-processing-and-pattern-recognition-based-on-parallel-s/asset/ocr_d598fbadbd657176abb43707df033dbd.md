maximum value of the shift in the chosen direction was used. This option is simple in the process of implementation and significantly reduces the hardware costs and does not require additional function-processing methods.

The amount of information needed to store template surface as elements of auxiliary function depends on the number of templates in the database.

Based on PST, image processing encourages the development of new methods of information storage. The set of actions for the preparation of comparison of templates and of real FAI at various variants of saving of standard surfaces is shown in Fig. 5.7.

![](bbox=[0.18, 0.31, 0.82, 0.58])

Fig. 5.7: Procedure for preparation of comparison etalon and real FAI in different variants of saving etalon surfaces

A possible solution to the problem of saving standard FAI is the use of their transformation into a Fourier series. As is known, such a transformation brings full information about the function. However, the use in processes of storage and restoration of data of Fourier series, which describes the function of the area of intersection, no given advantage is seen in reducing the amount of stored information. For this, storage may be used only in part of the harmonics of series that is similar to the low-pass filtering process.

In addition, the value of the harmonics of Fourier series depends on the area of the pattern figure. For unification the size of the harmonic values needs to be normalised. To do this, the value of each element of a number should be divided by the value of the input image area. In this case, the values of all harmonics will be close to unity, which simplifies the storage of information in databases.