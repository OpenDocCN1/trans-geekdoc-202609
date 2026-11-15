Thus, modification of the image can be attributed to methods of low pretreatment. The process of transformation cannot unambiguously hold a similar definition. Such converting steps, as object selection and the edge detection methods, are obviously is low-level methods. Other transformation methods are used depending on the methods for further analysis and have a set of image properties on the output. Therefore, they belong to the image-processing methods of mid-level.

Existing pre-treatment video information methods include the use of rather complex mathematical calculations, especially concerning the various filtering methods (frequency filtering, noise filters). Effectiveness of their use is based on the increasing power of computer technique.

Modern signal preprocessing means include its conversion to digital form, because of which are called digital signal processing (DSP). In the general case, DSP complex consists of a computer, dedicated hardware and software. Personal computers may be used for solving problems with low demands on information processing speed as the analysis unit.

Preprocessing of images based on parallel shift technology requires the creation of specialised means. At this stage, the process carried out by the authors uses the software model.

Use of parallel shift technology for image processing is convenient to demonstrate on the example of Chinese characters. They have complex and varied shapes, with their shape being important and thus are suitable for creating binary images. In this book, a variety of image processing methods are used by the Chinese character for ‘dragon’ (Fig. 3.1).

![](bbox=[0.59, 0.432, 0.85, 0.592])

**Fig. 3.1: Image of Chinese character ‘dragon’**

To create the possibility of applying image processing methods based on a parallel shift technology, the following must be done.

+   - Delamination is a separation of the image into several grades according to the brightness. The number of luminance ranges is selected depending on the need to address those or other problems.

+   - Binarisation is transformation of the image into a binary matrix. This process is based on a comparison of the brightness of each pixel with the luminance threshold value. The value of the brightness of the pixel above the threshold of brightness in the binary image corresponding to a pixel is set to 0, and otherwise to 1.

+   - Denoise is reduction existing in image extraneous information, which is not part of the input image and appears due to certain actions of external factors. A typical method of execution of the process is to remove the high frequency components of the signal spectrum.