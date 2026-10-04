
Along with other parameters, light intensity is a major factor responsible for image quality. It always depends on level of light. Often infrared (IR) images are great substitute for visible images under poor light conditions. For IR imaging, IR sensor is required, which will capture IR radiations. Normally these radiations are not visible to human eye. Very simple application of IR is remote control. Every remote control works on different IR ranges. Low light-sensitive CCD camera is used to capture IR images. Image fusion is a method that fuses distinct images into a picture comprising wealthy data from various sensors. The merged picture can be used for the extraction, segmentation, target detection, and identification of characteristics. Target sensing ([Xin et al., 2013](#bodymatter-009.xhtml#b_9783110648195-009_ref_058)), army surveillance ([Sadjadi 2006](#bodymatter-009.xhtml#b_9783110648195-009_ref_043)), and robot (Science n.d.) and medical diagnosis ([Haddadpour et al., 2017](#bodymatter-009.xhtml#b_9783110648195-009_ref_010)) are now commonly used image fusion application areas. Spatial domain (SD) and transform domain (TD) are its two major categories ([Yang and Li 2010](#bodymatter-009.xhtml#b_9783110648195-009_ref_059)). Direct manipulation of pixel is performed in SD and conversion of spatial to frequency domain happens in TD ([Chandra 2015](#bodymatter-009.xhtml#b_9783110648195-009_ref_006); [Wang et al., 2014](#bodymatter-009.xhtml#b_9783110648195-009_ref_055)). SD algorithms are computationally cheap but resultant image suffers from contrast distortion and loss of information issues. It is the art of merging different pictures in one picture that complements source data. The general approach adopted in this is shown in [Figure 9.1.](#bodymatter-009.xhtml#b_9783110648195-009_fig_001)

![Figure 9.1: Approach to image fusion.](graphic/converted/b_9783110648195-009_fig_001.png)

Figure 9.1: Approach to image fusion.

The images captured using the same sensor may vary in time coordinates, so in order to combine multiple images, it is necessary to bring the input images to a common coordinate system. The process used for this purpose is image registration, where two or more images are aligned geometrically. Geometrically aligning two or more images is called image registration ([Jiang et al., 2017](#bodymatter-009.xhtml#b_9783110648195-009_ref_014); [Kubota and Aizawa, 2005](#bodymatter-009.xhtml#b_9783110648195-009_ref_021); [Manchanda and Sharma, 2018](#bodymatter-009.xhtml#b_9783110648195-009_ref_034); [Wu et al., 2011](#bodymatter-009.xhtml#b_9783110648195-009_ref_057)). It is not the scope of this chapter but yet it needs to be discussed here because it is the assumption that either all source images are already registered or acquired with the help of tripod from the static scene used here.

In practice all fusion algorithms perform the image fusion process directly on the source images with complementary information as given in [Figure 9.2](#bodymatter-009.xhtml#b_9783110648195-009_fig_002).

![Figure 9.2: Fused image after acquiring complementary information.](graphic/converted/b_9783110648195-009_fig_002.png)

Figure 9.2: Fused image after acquiring complementary information.

![Figure 9.3: Structure of survey paper.](graphic/converted/b_9783110648195-009_fig_003.png)

Figure 9.3: Structure of survey paper.

![Figure 9.4: Fusion process for spatial domain. Yang B. and Shutao L. 2010.](graphic/converted/b_9783110648195-009_fig_004.png)

Figure 9.4: Fusion process for spatial domain. Yang B. and Shutao L. 2010.

![Figure 9.5: Fusion process for transform domain. Yang B. and Shutao L. 2010.](graphic/converted/b_9783110648195-009_fig_005.png)

Figure 9.5: Fusion process for transform domain. Yang B. and Shutao L. 2010.

The structure of the chapter is as follows (Figure 9.3).

## 9.2 Related work

In SD analysis all the algorithms are applied straightaway on the pixels, that is, we play with pixel values to perform image fusion at pixel level and extract information only through pixel values. Although this method is quiet easy and computationally cheap but resultant images suffers from issues related to contrast disorder, distortion, and information lost. Fused image shows artifacts due to noisy weighing map.

Whereas in TD, (Bhatnagar and Li et al. 2013a; [Jiang et al., 2018](#bodymatter-009.xhtml#b_9783110648195-009_ref_013); [Wang et al., 2004](#bodymatter-009.xhtml#b_9783110648195-009_ref_056); [Wu et al., 2011](#bodymatter-009.xhtml#b_9783110648195-009_ref_057)) image is shifted to frequency domain through discrete Fourier transform ([Kazemi and Moghaddam, 2003](#bodymatter-009.xhtml#b_9783110648195-009_ref_018)), curvelet transform ([Yang and Shutao, 2010](#bodymatter-009.xhtml#b_9783110648195-009_ref_059)), nonsubsampled contourlet transform ([Yin et al., 2010](#bodymatter-009.xhtml#b_9783110648195-009_ref_064)), and so on. Image is segregated into different frequency components, that is, high- and low-frequency components. Detailed image information is shown by low-frequency component and information related to edges is given by high-frequency components. In order to apply TD in image fusion, subblock size must be defined and results may vary according to the change in size of mask. It is very difficult to find the optimum value of window.

TD image fusion methods can be further subdivided into three categories: pyramid methods, wavelet, and multiscale decomposition (MSD). Burt and Adelson proposed Gaussian and Laplacian pyramid techniques in 1983 ([Burt and Adelson 1983](#bodymatter-009.xhtml#b_9783110648195-009_ref_035)) and provided good spectral information about the image, but the resultant image lost information and also showed artifacts. The main drawbacks of this technique are edges are not preserved and texture details, phase, and directional information is missing ([Pohl and Genderen 2010](#bodymatter-009.xhtml#b_9783110648195-009_ref_039)). It may also include blocking effect in resultant image. The block of decomposition is accompanied by the block of fusion rule. The aim of the fusion rule block is to fuse source images based on the extracted information. Pixel level image fusion, feature level image fusion, and decision level image fusion are three categories of rules according to extensive literature review. Pixel value of source images are processed in the operation of fusion at pixel level. Higher and lower frequency components in image are bifurcated in feature level operation. Wavelet and transform vectors are used for detection and classification in decision level operation.

Image fusion process may be applied to unimodal and multimodal images. Unimodal images are the images captured from single sensor and multimodal means images captured from different sensors. The examples of unimodal image fusion that includes multifocus and multi exposure are discussed in the forth coming sections.

### 9.2.1 Multifocus image fusion

In multifocus fusion process, images are taken from same camera at different focal length. Foreground (objects) and background are focused in different images. In multifocus image fusion process, multiple images acquired from the same camera focuses at different objects are joined/fused together as shown in [Figure 9.6](#bodymatter-009.xhtml#b_9783110648195-009_fig_006). The foremost objective is to improve the various properties of an image ([Feng et al., 2013](#bodymatter-009.xhtml#b_9783110648195-009_ref_008)).

![Figure 9.6: Multifocus image fusion: (a) focused background, (b) focused foreground, and (c) fused image.](graphic/converted/b_9783110648195-009_fig_006.jpg)

Figure 9.6: Multifocus image fusion: (a) focused background, (b) focused foreground, and (c) fused image.
