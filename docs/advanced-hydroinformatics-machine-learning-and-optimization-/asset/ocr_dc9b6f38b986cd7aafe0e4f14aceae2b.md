package in Python version 3.7 (van der Walt et al., 2014). The approach consists of the following steps (see also Fig. 6.4):

+   1. Clipping of the precipitation imagery to the Jubones basin (Fig. 6.4a).
+   2. Identification and localization of precipitation objects (latitude, longitude, see Fig. 6.4b). For this we defined a precipitation threshold

![](bbox=[0.18, 0.3, 0.35, 0.5])

![](bbox=[0.45, 0.27, 0.75, 0.48])

![](bbox=[0.18, 0.53, 0.35, 0.7])

![](bbox=[0.45, 0.52, 0.7, 0.7])

![](bbox=[0.18, 0.74, 0.35, 0.9])

![](bbox=[0.45, 0.74, 0.7, 0.9])

Figure 6.4 Precipitation identification with an object-based Connected Component Analysis Illustration of the PERSIAN-CCS 2021-12-25 05:00 UTC image: (a) Jubones basin clipping, (b) precipitation identification in mm from PERSIANN-CCS imagery, (c) initial identification of seven precipitation objects with CCA analysis, and (d) selection of two precipitation objects according to object size filtering and morphological closing.