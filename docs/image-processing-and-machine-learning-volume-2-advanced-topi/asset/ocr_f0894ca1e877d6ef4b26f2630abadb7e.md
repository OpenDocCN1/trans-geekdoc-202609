![](bbox=[0.128, 0.123, 0.472, 0.292])

Original

![](bbox=[0.505, 0.123, 0.862, 0.292])

r = 15

![](bbox=[0.128, 0.315, 0.472, 0.485])

r = 50

![](bbox=[0.505, 0.315, 0.862, 0.485])

r = 100

FIGURE 6.3 Returns the approximate matrices for different values of truncation r.

represented in a numerical format that allows each pixel to be given a value between 0 and 255. This numerical range corresponds to integers. It is for this reason that the image values are defined as integers. However, to decompose the data array into its SVD components, it is necessary to manipulate the information in the array as floating point elements. To carry out this process, the function in MATLAB of double is used. On the other hand, once the matrix has been constructed, giving approximate data X̂ considering a truncation level r, it is necessary to convert the data to an integer numeric type that allows the representation of images. This process is carried out by the MATLAB function mat2gray.

Figure 6.3 shows the approximate matrices for different values of truncation r. In the case of r = 15, it is clear that very little information has been used in the reconstruction. As a consequence, the objects in the image are hardly perceived. In the case of r = 50, although only 50 elements have been considered, it seems that they are enough to distinguish the objects and characters present in the image. Finally, in the case of r = 100, the image is already practically the original.