quantitative values of which identify only the image. This approach has been given the right to life due to the fact that it gives strict quantitative values that increase the accuracy of image recognition. Such characteristic features include: wavelet transformation coefficients (Daubechies, 1990), potential functions (Aizerman et al., 1970), area intersection functions (Belan and Yuzhakov, 2013; Belan and Yuzhakov, 2013a; Belan et al., 2014a), pulse sequence characteristics (Belan, 2011; Belan and Belan, 2013), features of wireless sensor networks (Lu et al., 2008; Simek et al., 2011; Heinzleman et al., 2002) and other quantities.

All these values are obtained by using additional transformations that represent the image by an array of quantities. In fact, the geometric characteristics can be represented by a set of quantities that depend on the structure of the converter. This approach can be represented by the following model:

I \xrightarrow{T} F

where I is an array of image points that have a certain brightness, colour and geometric shape; T is the function of transformation of input I array; and F is a vector of characteristic features that is obtained due to superimposition transformation of T into I array.

Consider a simple example of image transformation and description. To do this, we choose the Radon transformation, which differs from the methods considered in this book (Belan and Motornyuk, 2013; Bilan et al., 2014). Using the Radon transformation, the image is represented by projections that are received in selected directions. The more projections is the more accurate the image description.

Each projection consists of numbers. Each number is determined by the number of ones on the corresponding line. Each logic '1' encodes the state of a single image point. For example, if the number in the projection is 5, then on the straight perpendicularical projection there are five single cells. A set of projection codes describes an input image. Examples of the graphic representation of Radon projections for simple and complex images are shown in Fig. 8.1.

![](bbox=[0.65, 0.27, 0.81, 0.78])

Fig. 8.1: Examples of graphic representation of Radon projections for a brightness level of 37 per cent