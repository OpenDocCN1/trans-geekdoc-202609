# Deep Learning Method for Hyperspectral Image Classification 339

guiding restoration efforts are all made possible by analyzing the spectral
fingerprints of artifacts, work of art, and historical sites. There might be a
few benefits to this.

+   ix. *Remote sensing in astronomy*: Astronomy can benefit from remote
sensing techniques, such as HSI, to analyze celestial bodies and occur-
rences. This makes it possible to examine cosmic radiation, identify chemi-
 in far-off stars and galaxies, and investigate stellar spectra.

The variety and importance of HSI are demonstrated by the numerous applica-
tions have been developed. Because of its capacity to include the entire spectrum,
it opens the door to new approaches to analysis, categorization, and decision-making
advance a variety of industries, including science, technology, and environmen-
t management. These developments are made possible by the fact that this potential
exists.





Hyperspectral (HSI) classification is the process of assigning a specific class
or label to each pixel in a HSI based on its spectral signature. It plays a vital role
in extracting meaningful information and understanding the composition of the
observed scene [7, 8]. Over the years, various classification techniques have been
developed to effectively analyze hyperspectral data.



Traditional hyperspectral image classification methods [9–11], form the foundation
of hyperspectral data analysis and some of the commonly used traditional classifica-
tion methods are:

+   i. *Spectral angle mapper*: Its main function is to determine the angle between
t spectral signature of a pixel and a reference spectral signature that cor-
sponds to a certain class. The lowest-valued category is given to the pixel
after measuring its spectral angle.

+   ii. *Spectral information divergence (SID) metric*: The amount by which each
pixel's spectral distribution deviates from the reference spectra for the class dis-
is measured using the SID metric. Multiply the SID by the spectral-
of each pixel to obtain this separation. Two statistical methods
employed to use the data: the Kullback–Leibler divergence and the
Bhattaryya distance.

+   iii. *Support vector machines (SVM)*: SVM is a most commonly used machine
learning (ML) algorithm that finds an optimal hyperplane to separate dif-
erent classes based on a training dataset. It maps the input features
into a high-dimensional space to achieve better separability.

+   iv. *Maximum likelihood classifier (MLC)*: MLC assumes that each class fol-
low a multivariate Gaussian distribution and estimates the class parameters