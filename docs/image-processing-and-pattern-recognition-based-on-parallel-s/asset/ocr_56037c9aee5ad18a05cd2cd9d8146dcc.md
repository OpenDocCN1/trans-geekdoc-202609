| Name of the simple figure | rS | dS |
| :--- | :--- | :--- |
| Triangle | ≈ 10 | ≈ 0,16 |
| Circle | ≈ 5 | ≈ 0,1 |
| Square/rectangle | ≈ 4 | ≈ 0,08 |

From the data table it follows that the value of the acceptable margin of error, which is used in the comparison functions of the area of intersection of the simple shapes with pN = 30 per cent, must be greater than 0.16. However, at lower noise levels, a given value may be smaller. In the software simulation process for testing, the dS value range from 0 to 0.8 is used for the possibility to investigate the recognition efficiency depending on the value of this parameter.

Values of permissible errors were calculated to approximate initial evaluation of these parameters when building software models of the image recognition processes through methods based on the parallel shift technology. Various studies on the efficiency of these methods have been carried out, using a software simulation.

# 6.5 Evaluating the Effectiveness of Image Recognition Process in Various Parameters of Input Information Using Calculated Values of Permissible Errors

To evaluate the effectiveness of the image recognition process with different parameters of input information, it is necessary to define the type of errors, the occurrence of which is possible in this process.

As the first kind of mistake, we shall consider the case when the figure is in the database of templates, but in the process of identification, is assigned to the class of images, consisting of more than one element, and in this class is included the figure that is being recognised. A typical example of an error of this kind is optional, when the parameters of permissible errors are selected incorrectly.

The second kind of error will be called in a situation when the figure is in the template database, but on the detailed step of identification it is assigned to the image class, which does not contain the given image. The main cause of error appearance of this kind is a high noise level. The negative influence of this noise cannot be deleted by the chosen method of noise removal.

The third kind of error occurs when there is a figure-based template, but is not found in the database.

On the basis of the calculated parameter of permissible errors, recognition of simple shapes was carried out to determine the effectiveness