
is unavailable but the analyst knows about the identity of the device that is suspected of being the source device, another set of images or an earlier video recorded by that device can be used to estimate the reference noise pattern for that device, which can then be matched against the noise characteristics of the given image or video. For instance, if the video under examination is a surveillance footage recorded by a certain CCTV camera (whose identity is known), and if that camera is unavailable at the time of investigation, then another video recorded by the same CCTV camera at some earlier point in time can be used to estimate reference noise characteristics for that camera. **Blind SCI:** If the analyst is uncertain of the identity of the acquisition device, or if no other image or video captured by that same device exists or is available at the time of examination, then the process of source camera identification becomes a bit more complicated, because now the analyst must identify the source camera in a blind manner. The most commonly used approach in such a circumstance is to train a machine-learning based classification algorithm to categorize the available test noise patterns and infer the identity of the source device. We learn more about blind SCI in Section 23.6.4; first, we study the various non-blind device-linking methods.

It is important to note at this point that though acquisition devices generally encode the device related information and recording parameters, such as camera model, date and time of file creation/access/modification, image/video resolution, video frame rate, and compression details as *metadata*, this information is easy to modify and/or remove. It is therefore advisable to refrain from relying solely on this data for forensic purposes and utilize other artifacts obtained from alternative sources as well; we explore such artifacts in the upcoming sub-sections.

## 23.6.1.1 Image/Video Acquisition Pipeline

In order to understand how and why different acquisition devices leave unique traces on the content they capture, we first need to acquire a basic understanding of a typical image/video acquisition pipeline. Figure 23.10 illustrates the flow of data within a standard digital camera.

Acquisition of the digital visual data begins with light passing through the camera lens and possibly through a filter (which is generally used to remove infrared or ultra-violet light). Color cameras contain an additional Color Filter Array (CFA), which is placed over the sensor to generate different color channels. An RGB Bayer

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_709_0.png)

Figure 23.10 A typical digital image/video acquisition pipeline.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_710_0.png)

Figure 23.11 Color image acquisition process. (a) represents a Bayer mosaic; each two-by-two cell contains two green, one blue, and one red filter, and (b) illustrates how each filter allows only one wavelength of the incoming light—red, green, or blue, to pass through to any given pixel, allowing only one color to be recorded at each pixel location. (Courtesy of Wikimedia Commons.)

Pattern, also known as a Bayer filter mosaic, is the most commonly used CFA. It is a 2 × 2 array that contains alternative rows of red and green, and green and blue filters (Figure 23.11a). A demosaicing (aka debayering or demosaicking) algorithm then reconstructs a full color image using the incomplete color samples output from a CFA-overlaid sensor; this process is known as CFA interpolation or color reconstruction. An alternative CFA configuration is the CMYK subtractive color model; it is relatively lesser known and is only available in very few high-end sensors.

The incoming light waves (of variable attenuation) pass through the CFA and reach the imaging sensor, which converts them into signals that constitute the captured image. A typical imaging sensor is either a silicon CCD (Charge Coupled Device) or CMOS (Complementary Metal Oxide Semiconductor). The captured image then undergoes several processing operations, such as aperture correction, gamma correction, white balancing, sharpening, and compression.

Though the aforementioned camera components and processing operations represent standard phases in a digital camera pipeline, the precise manner in which each component operates or processes the data varies from manufacturer to manufacturer, and may even vary between different camera models manufactured by the same company. What remains universal however is that each component of the digital camera operates in an imperfect manner, which causes it to introduce certain inconsistencies in the image or video it acquires, and since these inconsistencies are inimitable, they act as unique identifying characteristics or artifacts that can be used to trace the given image or video back to the camera that captured it.

## 23.6.2 Classes of Source Camera Identification

Source camera identification entails identification of the model and/or manufacturer of the device that produced the image or video in question (a task generally referred to as source model identification or device class identification), and identification of the exact device that produced the image or video in question (a task generally referred to as individual source identification or specific device identification).

### 23.6.2.1 Source Model or Device Class Identification

In order to identify the model and/or manufacturer of the camera used to capture the image or video in question, the forensic analyst takes advantage of the variations in component technologies and processing techniques used by different camera manufacturers. Optical distortions caused by different type of camera lenses, variations in the sizes of the imaging sensors, the choice of CFA, or the respective demosaicing algorithm employed within a particular camera, all serve as identifying traces that can be quantitatively characterized to perform source model identification.

Now, since several camera models and brands use common components produced by a few manufacturers, and since different models of a brand use similar image/video processing algorithms, reliable identification of a source camera-model necessitates that the analyst characterizes and analyzes those specific features that differ from one camera model to another; these features have been examined below.

### 1. CFA and Demosaicing Algorithms

The choice of CFA and the particulars of the demosaicing algorithm used in a particular camera, are responsible for some of the most pronounced dissimilarities between content captured by different camera-models. The demosaicing algorithm that creates the final color image/video frame from three separate color channels is basically a kind of interpolation. Interpolation, a process used to estimate new pixel values from existing values, inevitably introduces certain correlations or interdependencies amongst neighboring pixels in an image or video frame. Based on the nature of correlations present in the given image/video frame, the presence of a particular demosaicing algorithm can be identified, which can then help identify the camera-model that was used to capture the image/video in question.

### 2. Lens Distortions

Digital cameras with spherical lenses introduce radial distortions in the images or frames of the videos they capture. Radial distortions refer to the phenomenon that causes straight lines in object space to be rendered as curved lines (Figure 23.12).

Radial distortions are most prominent when the widest angle, i.e., shortest focal length, is selected either with a fixed or a zoom lens. Though such distortions seldom affect the quality of the image or video, they have a substantial impact on the geometry of solid objects present in the scene, which is why camera manufacturers try to counterbalance their effect by adjusting several parameters during image formation. This process yields unique artifacts, which can be utilized for camera-model identification.
