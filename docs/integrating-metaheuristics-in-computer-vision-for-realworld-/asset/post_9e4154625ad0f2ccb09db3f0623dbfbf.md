
![](img/07f0bb0f402fd4e2f1880bf37d1ea963_275_0.png)

Figure 15.2 RGB color space.

### 15.3.1.1.2 HSV

The three elements of hue, saturation, and value are used to define colors in the HSV color system. Colors are classified according to their hue (red, blue, etc.), saturation (the more vibrant they are, the less grey is present), and value (brightness). Once more a representation that depends on the device, HSV is defined in relation to the RGB color space. A straightforward formula can be used to convert RGB values to HSV coordinates. Colors with similar values are viewed similarly by the human eye because HSV is perceptually homogeneous. Especially in application interfaces, users browse the color space to choose an example, HSV space is frequently utilised in computer graphics.

### 15.3.1.1.3 Opponent Color Space

To support the hypothesis that human color vision employs an opponent-color model, wherein certain colors are never perceived to occur together. In contrast, it is simple to recognise mixture of green and yellow, red and blue, green and blue, and, red and yellow. For instance, a color perception is not described as bluish yellows or reddish-greens. It is suggested that the opponent color space be used for encoding the color to the opposite signal considering observations. Three parts—R-G, 2B-RG, and R+B+G—are distinguished from the RGB values. The benefit of this style of representation is that it isolates the brightness of data into the 3rd channel.

### 15.3.1.1.4 CIELUV and CIELAB

These are suitable models for image retrieval because CIELAB and CIELUV spaces satisfy the requirement for spatial homogeneity. They have perceptually homogenous color spaces and are completely independent of the type of device being utilised. The brightness (L) and 2 chromatic elements (A and B), which stand for the separations between magenta, green, yellow and blue, so far, make up the three components of the model. CIELUV is created to improve the linearity of color perception.

### 15.3.1.2 Method of Representation

The depictions of each feature can vary. The color feature of an image is represented, for instance, by color histograms, color moments [24], color or color correlograms [25], coherence vectors [26], etc. Moreover, a wide range of color histogram variations have been put out, each with a unique color quantization method. The mathematical operations carried out on pixel values represented in a particular color space are connected to the color descriptors. Most common adjectives include:

### 15.3.1.2.1 Color Histogram

In CBIR systems, color histograms are the primary tool for representing the color information of images. A type of bar graph known as a color histogram is one in which each individual bar represents an actual color in the currently used color space. A color histogram is a rough illustration of the likelihood of the three color channels’ combined values. By dividing the data range into bins of equal sizes, the histogram’s most prevalent form can be derived. The likelihood that a pixel will fall into a certain bin is then determined for each bin by counting and normalising the number of colours of the pixel in a picture which fall into each bin to total points. The fact that the colour histogram does not account for the spatial data contained in pixels is one of its fundamental flaws.

The fact that two quite diverse photos have a similar colour distribution allows us to compare them. The cumulated colour histogram, first put forth by Stricker and Orengo, is an enhancement of the colour histogram approach. The benefits of the suggested approach over the traditional colour histogram approach were shown by their findings. Nevertheless, the approach has the drawback that there is no obvious way to organise bins when there are multiple-dimensional histograms.

### 15.3.1.2.2 Color Moments

Stricker and Orengo suggested employing the colour moments technique to get around the quantization issues. Color moments, are the statistical moments of colour probability distributions, are often employed in retrieval systems, particularly when a picture only contains the item itself. It has been shown that the mean, variance, and skewness color moments can be used to accurately represent the colour distributions of photographs. The issue with colour moments is that they have the same shortcomings as the colour histogram technique in that they do not encode any spatial information surrounding colour inside an image.

### 15.3.1.2.3 Color Correlogram

The color correlogram is a method for recording an image’s color information. Unlike color histograms and moments, this approach adds spatial data in the encoded color information, which solves some of the issues with previous representations. The color correlogram has the advantages of being easy to compute, including color spatial correlation, and being able to describe the worldwide distribution of color spatial correlation.

### 15.3.1.2.4 Color Coherence Vector

In a split histogram, pixels are divided into color coherence vectors based on their spatial coherence. The image’s pixels are divided into two categories, coherent and incoherent, depending on whether they are a part of a wider area of uniform color. So that the feature vector contains some spatial information, separated histograms subsequently be generated for relevant and non-relevant pixels. Because of the spatial data, it is observed that CCV performs in a better extraction way than the color histogram, especially for pictures with a preponderance of uniform color or texture regions. In addition, the HSV color space performs better for both the representation of the color histogram and the color coherence vector than the CIELUV and CIELAB color spaces.

### 15.3.2 Texture

Texture is a term used to describe visual patterns that exhibit uniformity without being limited to a single hue or level of intensity. It is present on almost every surface in nature, including trees, brickwork, hair, fabrics and clouds. It holds vital data of structural makeup and surfaces. Figure 15.3 displays several different textures.

### 15.3.2.1 Method of Depiction

There are three types of texture representation techniques:

- The grey level statistical properties of pixels that make up a picture are used by statistical techniques to characterise texture. In photographs, various grey levels typically appear on occasion. Grayscale distribution in space is computed.
- Texture is defined as being created via structural processes from texels (texture elements). These texels are set up in a predetermined pattern on a surface, following predetermined layout rules.
- Spectral approaches, which are based on Fourier spectrum characteristics, high-energy peaks in Fourier spectrum to describe the worldwide periodicity of a surface’s grey levels are found. For texture classification, statistical approaches are crucial because it is through them that texture properties are computed. Tamura features, co-occurrence matrices, and filters with many resolutions, such as the Gabor and Wavelet transform are a few examples of statistical representations of texture.

![](img/07f0bb0f402fd4e2f1880bf37d1ea963_277_0.png)

Figure 15.3 Texture.

### 15.3.2.1.1 Tamura Features

The psychological research on how people perceive texture in their environment served as inspiration for investigations of a new angle [27] on texture representation. The aspects of the visual texture that psychological research has shown to be significant were approximated by computers. The six properties of visual texture are directionality, coarseness, contrast, linelikeness, and roughness and regularity. These characteristics are highly valued in image retrieval systems because the texture properties have visual meaning. This allows for the representation of texture attributes in an interface that is user-friendly and allows the user to utilise a verbal description of the image. A few early retrieval systems used coarseness, contrast, and directionality. For example, the MPEG-7 standard [28] accepted directionality as a texture browsing description.

### 15.3.2.1.2 Co-Occurrence Matrices

Yalavarthi _et al_. [29] is credited with the invention of the co-occurrence matrix. According to the orientation and distance between the pixels, this method creates a co-occurrence matrix. To represent the texture, useful statistics are then taken from the matrix. The same approach was taken by numerous other researchers, who also put out improved versions. For instance, Hung C. _et al_. examined the statistics [30] first proposed in and discovered experimentally that inverse difference moment, contrast, and entropy had the greatest power of discriminatory [31].

### 15.3.2.1.3 Gabor Filters

The wavelets that make up Gabor filters (GF) are all different-sized and oriented wavelets that capture energy. Hence, Gabor helps in identification of local energy among all signals or a picture. It is used to extract accurate texture features, rather than picture features [32]. Resolving vision and spatial frequency, is provided by Gabor filters. GF is used for a wide range of tasks due to their versatility, including retina identification, image coding, document analysis, target detection, texture segmentation, fractal dimension measurement, line characterization, image representation, edge detection, and others.

### 15.3.2.1.4 Wavelet Transform

Wavelet transforms, an alternative multi-resolution method, are most frequently utilised in various areas of image processing. In order to reduce picture noise, compress images, rebuild images, and retrieve images, a variety of wavelet-based techniques and concepts have been suggested and investigated. It has used the multi-resolution wavelet transform to extract images. A high level of retrieval accuracy is not attained using wavelet characteristics. To increase retrieval accuracy using wavelet transform, numerous techniques have been devised. The efficacy of CBIR is increased by giving weights to wavelet features calculated from discrete wavelet coefficients.
