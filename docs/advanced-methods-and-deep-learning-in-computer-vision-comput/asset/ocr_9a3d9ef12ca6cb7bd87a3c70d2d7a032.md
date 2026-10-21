significantly outperforming five earlier approaches, none of which achieved better than 22% accuracy.

Whereas Kalal et al.’s (2011) work only tracked single objects, Wu et al. (2012) showed how to carry out coupling detection and data association for multiple objects to ensure that complete tracks would be determined. This approach employed network flow data association and relied on an earlier paper by Castañón (1990) entitled “Efficient algorithm for finding the k best paths through a trellis”. This title shows that the method relies heavily on extensive analysis of graphs: while interesting, space does not permit a full discussion of these techniques to be included here. Suffice it to say that tracking multiple objects is a difficult problem that becomes even more difficult as the number of targets increases and the whole scene fills up with objects and tracks. Thus, in this respect, Wu et al.’s (2012) work can be regarded as more thoroughgoing than that of Stalder et al. (2009). We will study more recent developments on this topic in Part F, Section 1.7.7, after introducing deep learning methods.

# 1.6 Part E – Texture analysis

# 1.6.1 Introduction

We have already considered several core aspects of image analysis, including in particular feature detection, object recognition and segmentation. Here we go on to consider texture analysis. To proceed, we start by defining a texture as the characteristic variation in intensity which should allow us to recognize and describe a textured region and to outline its boundaries (Fig. 1.29). Typically, a texture is the intensity pattern that results when light is reflected from a surface having a certain degree of roughness. Clearly, a smooth, uniformly lit surface will exhibit no texture, while a piece of cloth or a sandy beach will have characteristic textures of their own.

Broadly speaking, textures vary in their degrees of randomness and regularity, and in the latter case they may have high or low directionalities. For example, pieces of cloth generally exhibit high degrees of regularity and directionality, while the intensity pattern emanating from the surface of a sandy beach may appear highly random, with negligible directionality. Another factor is the scale of the perceived particle size for the surface, which will be small for sand and much larger for a tray of peas. In fact, the tiny elements composing a textured surface are often called textural elements or texels. These considerations lead us to characterize textures in the following ways:

+   1. The texels will have various sizes and degrees of uniformity.
+   2. The texels will be orientated in various directions.
+   3. The texels will be spaced at varying distances in different directions.
+   4. The contrast will have various magnitudes and variations.
+   5. Various amounts of background may be visible between texels.
+   6. The variations composing the texture may each have varying degrees of regularity vis-à-vis randomness.

The significant number of parameters required to characterize a texture are bound to make texture analysis quite complicated: and of course, many of the parameters will have a high