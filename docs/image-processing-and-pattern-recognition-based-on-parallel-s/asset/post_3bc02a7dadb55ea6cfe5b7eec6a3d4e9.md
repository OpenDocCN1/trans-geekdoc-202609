
All the images used examples of simulations were binary. They could be convex, irregularly shaped or comprise several objects.

The Fourier series harmonic number depends on the amount and form of patterns. In the process of software modelling it was revealed that to create a pattern FAI of convex figures, it is better to use the first five Fourier harmonics. To create a pattern FAI of no convex figures it is enough use the first ten harmonics of the Fourier. To create a pattern FAI of figures consisting of several objects it is enough to use the first twenty Fourier harmonics. In all these cases the deviation reconstructed FAI and the real FAI do not exceed 10 per cent of the value of the real function at each displacement step. Also, when choosing an etalon that corresponds to a specific FAI, the average deviation of the real value and the pattern value for a specific section of the FAI function may be used. Examples of graph template of functions by using different numbers of the Fourier series harmonics for the restoration of FAI are shown in Fig. 5.9.

| Direction FAI | Number of the Fourier series harmonics used in the recovery of etalon FAI | | |
|---|---|---|---|
| | 4 | 12 | 20 |
| X | | | |
| Y | | | |
| real object FAI<br>recovered etalon FAI | | | |

Fig. 5.9: Graphs of real object FAI and recovered etalon FAI

With the saving of pattern functions in the form of a Fourier series it is possible to simulate the process of forgetting information by man. Assume that at the initial stage (immediately after the learning process) pattern function is described by a complete set of the harmonics of Fourier series. The amount of the series of elements will be of the same length as digitised FAI. At predetermined time intervals the highest numbered harmonics from the pattern series may be removed. Some of the information about the pattern will be lost, but will be less of necessary information to store. Repeated restoration of data about the object becomes necessary when the function is built on the basis of the existing number of harmonics, and will differ from the original more than a specified value. When the selected number of harmonics of the Fourier series (NH) is for recovery of the function of the area of intersection, the formula (5.3) is converted into the following:

```
FAI(j) = S_0 \cdot \left( \frac{FFTN_0}{\sqrt{X_{max}}} + \frac{\sqrt{2}}{\sqrt{X_{max}}} \sum_{i=1}^{NH-1} FFTN_i \cdot \cos \left( \frac{\pi \cdot i \cdot (2 \cdot j + 1)}{2 \cdot X_{max}} \right) \right) (5.4)
```

Saving the reference data as a function information will significantly reduce the amount of data required to store. Storing information about the images as of standard surfaces will ensure implementation of tasks of recognition and determining the spatial orientation of the 2D-objects.

## 5.3 Application of Image-processing Methods Based on PST for Prosthetic Visual Organs

The use of parallel shift technology ensures the implementation of the main tasks of video processing and simulates the processes related with human vision. Therefore, the processing of information obtained as a result of PST can be used in medicine to create artificial bodies of view. The basis of this technology is to obtain FAI, which can be converted, for example, into audio signals. Using the human brain’s ability to learn and adapt, it is possible to teach blind people to ‘hear’ the image and nor is it difficult to obtain the information in a suitable format for the human ear from device of cyclic generation of the function signal of the area of intersection. But, to determine the parameters of output signal, additional research with specialist’s ophthalmologists and otolaryngologists is needed. The brightness and the amount in the scene elements may be converted to frequency and amplitude of the audio signal. In future, with the development of neurosurgery, it may be possible to give signals from receptor field directly to the visual area of the brain. In this case, the system ‘sensor-analysis unit’ will perform the role of the sensor device receiving FAI and the analysis unit will serve as the human brain.

In Fig. 5.10 three possible options are shown for connecting the device forming of continuous functions of the area of intersection in the human body. In the first two embodiments, the imaging device is built into the glasses and the third—in the eye prosthesis. The information is transmitted in the first embodiment in the earpiece, and in the second and third—directly on the visual area of the brain. All the three options differ in the degree of operative interference.

![](img/d6ed6c69a61b1252a9084096bb4904c6_92_0.png)

Fig. 5.10: Embodiment connections of the information-processing device to the human bodies

Research in this direction is underway since long ago, but the developers of such systems in the brain are supplied a set of pixels that make up an image. The transition information about all the elements that make up an object is quite difficult. When transmitting selected information it gets lost in perception accuracy. The image-processing systems based on parallel shift technology can use almost all the information about the visual scene. Data about areas of the image are summarized. Their number is limited, but they carry a lot of information about the object.

This machine vision system quite accurately simulates the human vision. Parallel shift technology of copy image may explain the cause of the eye pupil movement in recognition of images and edge detection of the figures. The method of calculating the basic parameters of the object allows the processes that have occurred in experiments to determine the properties of the viewed organs of living things to respond to movement. The ability to determine the angles of plane location, on which there is a figure, simplifies the operation of the system ‘eye-hand’. Storage of patterns as of the pattern surfaces can explain the process of forgetting by man of the visual images. For example, if to scale the digitised pattern surface of the images that have not been used to reduce memory usage, then, when the need arises, scale them towards increasing. This way the data loss will be apparent. There is the necessity of updating this pattern. In addition, the image studied carefully, by those who have long not seen, needs to be updated in memory.

FAI graphs difference can explain how a person defines a set of letters belonging to one word (Fig. 5.11).

If an object length is equal to the maximum shift, the letters belong to the same word; else each letter is perceived separately. Then the word is formed for a set of letters. In the pattern databases for each word, for each group of characters and for each letter can be put into correspondence the individual pattern surface.

![](img/d6ed6c69a61b1252a9084096bb4904c6_93_0.png)

Fig. 5.11: FAI(x) of the word ‘interval’ at different distances between the letters

Usually people during analysis of the visual scene pay attention only to some of the main objects; other information about the environment is processed as some model. The system built of parallel shift technology allows simulation human vision. However, for accurate modelling it is necessary to build hybrid systems of technical view. They should include the possibility of digital image processing. The hybrid human vision can be explained as follows. In determination of the movement parameters, taking into account the Doppler effect, the object moves much faster than the shift copies. This movement will not be registered, as if there was no object in the visual scene. This is similar to the effect of 25 frame, but this effect confirms the presence of other information-processing systems, where the entire video stream is divided into frames, stored and processed subconsciously.

## 5.4 Perspective Directions of Image-processing Research Using PST

The system of images perception, which is used in the construction of parallel shift technology, has advantages in performing certain image-processing tasks. In the process of implementation of the algorithm, the information is aggregated and ordered that, in some cases, it leads to productivity improvement, but sometimes, these properties make it impossible to perform certain tasks.

Let us consider the image-restoration issues processed by using the parallel shift technology. If image description is only a set of functions of the area of intersection, then restoration is possible in the following ways.

Suppose we know the initial image area (parameter \(S_0\)). Let us divide this value into the largest possible number (\(n\)) of identical elements. The area of each of them is equal to \(\frac{S_0}{n}\). The visual field is divided into sections of the same area. The complete enumeration method determines all the possible options for the location of \(n\) elements of the object in the visual field. Thus, it is possible to choose the location of the image elements, such that in the formation of set FAI, these features are close in value to the elements of the pattern surface, which describes the object. The process of performing the complete enumeration is very simple, but requires a very large amount of time to perform.

The second method may be stored in the image-copy memory. If required to restore the data from memory, the stored image is scaled to the required size. The FAI set in restoration is not involved. In this case, additional costs of storing reference image are needed. Also, if a certain class of images is stored in one pattern, then in restoring it cannot be identical to the required image.

To reduce the stored information, the pattern can be represented by a set of syntax expression for simple shapes. Then the image reconstruction
