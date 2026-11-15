analysis unit will need to transfer not only the m×n values of the functions of the area of intersection, but also the images of m areas edge of the object and 2m values of their coordinates.

For the processing of objects with dimensions of more than two in such devices, the camera must be replaced by a corresponding detector. The forming units of intersection object functions and its copy must also be modified.

In the analysis of continuous functions, it is necessary to know what areas of FAI graphics is responsible for performing certain operations. In Fig. 5.5 certain functions of the area of intersection with the specified areas are and the analysis of which allows performing certain image-processing tasks (Dai and Nakano, 1998).

![](bbox=[0.28, 0.335, 0.72, 0.545])

Fig. 5.5: Distribution of parts of the FAI graph to perform certain operations

The a graph segment is used to implement the pattern recognition process for determining the spatial orientation of objects—segment b—in determination of the coordinates of the initial location, area c—in determining the outline of the image and in the fight against noise, area d—in determination of the parameters of the object. The FAI graph on Fig. 5.5 is schematically shown and only in one displacement direction of the image copy. The right boundary of b segment is chosen arbitrarily. It depends on the actual distance from the centre of mass of the object to the edge of the field receptor. The FAI area specialisation for other areas is similar. Here the function of the area of intersection depends on the time (t). In order to determine the function values dependent on the distance, it is sufficient to multiply the corresponding time periods on a shear rate of object copy.

The need to take into account the Euclidean coordinate system, some of the image-processing tasks are enough to only perform orthogonal directions shear copy. These tasks include determination of initial coordinates of an object and its movement parameters.