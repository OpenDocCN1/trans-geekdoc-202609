The data set consists of n_t = 2000 velocity fields, sampled at f_s = 2 kHz over a grid of 60 × 114 points. The spatial resolution is approximately Δx = 0.33 mm. The script provided in the book’s website26 describes how to manipulate this data set, plot a time step, and more. For the mPOD of this test case, the frequency splitting vector used in Mendez, Balabane and Buchlin (2019) is constructed in terms of Strouhal number St = f H / U_J, that is, the dimensionless frequency computed from the advection time H / U_J, with H the standoff distance and U_J the mean velocity of the jet at the nozzle outlet. These are H = 4mm and U_J = 6.5 m/s.

The reader is encouraged to compare the mPOD results with those achievable from other decompositions. The spatial structures and the spectra of the temporal structures in the first five modes are produced by the script TUT_1.PY. These are shown in Figure 8.4 for the dominant mPOD mode in the scale St = 0.1 – 0.2. This mode isolates the roll-like structures produced by the evolution of the shear layer instability downstream the potential core of the jet. Recall that the velocity components are stacked into a single vector.

![](bbox=[0.17, 0.4, 0.88, 0.7])

Figure 8.4 On the left: example snapshot from the first tutorial test case on the TR-PIV of an impinging gas jet. Colormap in m/s. On the right: example of spatial structure (top) and frequency content (bottom) of the temporal structures of a mPOD mode.

# 8.5.2 Test Case 2

To download this data set and store it into a local directory, run the following script

```
```python
import urllib.request
print('Downloading Data for Tutorial 2...')
url = 'https://osf.io/qa8d4/download'
urllib.request.urlretrieve(url, 'Ex_5_TR_PIV_Cylinder.zip')
print('Download Completed! I prepare data Folder')
```
```