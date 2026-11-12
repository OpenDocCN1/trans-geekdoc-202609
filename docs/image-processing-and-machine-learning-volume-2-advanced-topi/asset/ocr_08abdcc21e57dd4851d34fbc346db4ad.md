RGB is a very simple color model. It is sufficient for color processing or when it is necessary to transform to a different color model, as will be seen later. For now, problems such as the correspondence between an RGB pixel and its true color or the meaning of the physical representation of the primary colors red, green, or blue will not be considered. Interesting details relating to color and the CIE color space will be covered later.

From the programmer point of view, an RGB color image is an array of size \(M \times N \times 3\), where \(M \times N\) defines the dimensions of the planes, while the dimension corresponding to 3 defines each of them R, G, and B. Based on the above, an RGB image can be considered an array of three grayscale images [4].

# ## 2.1.1 Composition of Color Images

Color images are characterized, like grayscale images, as pixel arrays, where different types of models can be used to compose the different color components that together form the total color. Two types of color images can be distinguished: the so-called full-color images and the so-called indexed or referenced color palettes.

Full-color images completely use the color space. That is, for their construction, the entire space defined for the color model is used for the representation of the image. On the other hand, indexed color images use a reduced number of colors in the representation of the image.

# ## 2.1.2 Full-Color Images

A pixel in a full-color image can assume any value in the space defined in the referenced color model. Full-color images are normally used in cases where the image contains a large number of colors defined by the color model in question, such as photographs [5]. In the composition of the color image, two types of associations can be distinguished: the composition of the planes and the composition of the packaging.

By the composition of the planes, we mean the separation of the different arrangements with the same dimension that constitute the image. A color image

\(I = (I_R, I_G, I_B)\) (2.2)

can be considered as a related set of images of intensity \(I_R(x, y)\), \(I_G(x, y)\) and \(I_B(x, y)\) (see Figure 2.3), where the RGB value of a pixel of the color image is obtained by accessing each of the arrays that constitute the combination in the form: