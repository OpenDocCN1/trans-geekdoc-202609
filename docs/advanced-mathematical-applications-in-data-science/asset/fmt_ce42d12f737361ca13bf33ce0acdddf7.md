
### The Estimate Update equation

|![](Images/9789815124842-C2-EQ41.jpg)||(41)|

### The Error in the Estimate Update equation

|![](Images/9789815124842-C2-EQ42.jpg)||(42)|

The equation **(40)** determines the Kalman Gain (`K`), which depends on `E[EST]` and `E[MEA]`. The value of `K` is restricted between 0 and 1. This can be proved by considering the following two cases:

1. `E[EST]`![](Images/9789815124842-C2-E0001.jpg)`E[MEA]` then **(40)** approximates to `K` ≈ 1.
2. `E[EST]`![](Images/9789815124842-C2-E0002.jpg)`E[MEA]` then **(40)** approximates to `K` ≈ 0.

The equation **(41)** updates the Estimated value. The following two cases illustrate the two ideal cases.

1. `E[EST]`![](Images/9789815124842-C2-E0001.jpg)`E[MEA]` and `K` ≈ 1, then the new estimated value (`EST[k]`) is changed to a greater extent from the previous value (`EST[k]`[−1]).
2. `E[EST]`![](Images/9789815124842-C2-E0002.jpg)`E[MEA]` and `K` ≈ 0, then the new estimated value (`EST[k]`) is not changed that much from the previous value (`EST[k]`[−1]).

The equation **(42)** updates the Error in the Estimated value. The following two cases illustrate the two ideal cases.

1. `E[EST]`![](Images/9789815124842-C2-E0001.jpg)`E[MEA]` and `K` ≈ 1, then the error in the estimated value `E[ESTk]` remains almost same.
2. `E[EST]`![](Images/9789815124842-C2-E0002.jpg)`E[MEA]` and `K` ≈ 0, then the error in the estimated value `E[ESTk]` reduces, making estimates more accurate.

The basic algorithm of the Kalman Filtering process is shown in Fig. ([**1**](#9789815124842-C2.html#f1)).

![](Images/9789815124842-C2-F1.jpg)**Fig. (1))**  
Algorithm for One Dimension.

We present here some very simple examples to give the reader an insight into the usage of Kalman filter.

## EXAMPLE 1: FINDING THE TRUE VALUE OF TEMPERATURE

A room with no drastic change in temperature is considered. The main aim is to find out the actual or *true* value using a temperature sensor, *i.e.*, 72^◦*C*. Every second, the temperature is recorded. This is done till the number of observations reaches a large value.

Let Matrix `M` represent the Measurement values, where `M` = \[75, 71, 72, 75, 68, 73, 69*, ....*\] in^◦*C (degree Celsius)* and Error in the Measurement `E[MEA]` = 2^◦*C.* The initial values considered are:

Initial Estimate `EST[o]` = 68^◦*C*

Initial Error in the Estimate `E[ESTo]` = 2^◦*C*

### First Iteration

|![](Images/9789815124842-C2-EQ42A.jpg)|

### Second Iteration

|![](Images/9789815124842-C2-EQ42B.jpg)|

Further iterations are carried out and eventually, the estimated value (`EST[k]`) reaches the true value. The more data points, the more accurate the final results (final estimates) will be.

## EXAMPLE 2: FINDING THE TRUE VALUE OF ACCELERATION DUE TO GRAVITY

Kalman Filtering can be used to find out the true value of a measurable quantity. There are many constants used in physical systems like *acceleration due to gravity*, *Planck’s Constant*, *Boltzmann constant*, *etc.* But, to find out their exact value or true value, one should not be restricted to one or two experimental outcomes, as it may not be accurate. To overcome this problem, a large number of observations are taken (preferably using more than one type of apparatus to measure one single parameter). In this example, various observations are recorded for the *time period* of a simple pendulum. These observations are then used to find out the true value of time period of a simple pendulum (of finite length) and thus find out the value of acceleration due to gravity. This true value is found using Kalman Filter technique.

The value of acceleration due to gravity (`g`) is thus calculated using the formula:

|![](Images/9789815124842-C2-EQ42D.jpg)||(43)|

`T`: True value of Time Period (in seconds) found out using Kalman Filter.

`l`: Length of the simple pendulum (in metres).

`N`: Total number of observations.

The value of parameters used are: `l` = 1.04m, `N`= 126

The experimental values of time period are given in Table [**1**](#9789815124842-C2.html#t1) below:

Table 1 **Experimental Values of Time Period in second.**  

| 2.021 || 2.041 || 2.036 || 2.024 || 2.054 || 2.044 || 2.051 |
| --- | --- | --- | --- | --- | --- | --- |
| 2.043 || 2.043 || 2.047 || 2.04 || 2.045 || 2.053 || 2.042 |
| --- | --- | --- | --- | --- | --- | --- |
| 2.035 || 2.025 || 2.058 || 2.047 || 2.046 || 2.042 || 2.04 |
| 2.057 || 2.037 || 2.041 || 2.033 || 2.057 || 2.061 || 2.065 |
| 2.05 || 2.038 || 2.042 || 2.036 || 2.038 || 2.04 || 2.048 |
| 2.045 || 2.036 || 2.044 || 2.047 || 2.042 || 2.051 || 2.04 |
| 2.047 || 2.043 || 2.035 || 2.058 || 2.064 || 2.042 ||  |
| 2.044 || 2.045 || 2.052 || 2.041 || 2.036 || 2.023 ||  |
| 2.056 || 2.064 || 2.044 || 2.042 || 2.043 || 2.034 ||  |
| 2.042 || 2.042 || 2.046 || 2.053 || 2.025 || 2.052 ||  |
| 2.041 || 2.043 || 2.03 || 2.044 || 2.047 || 2.04 ||  |
| 2.02 || 2.054 || 2.041 || 2.035 || 2.041 || 2.044 ||  |
| 2.044 || 2.057 || 2.043 || 2.036 || 2.032 || 2.066 ||  |
| 2.035 || 2.036 || 2.025 || 2.047 || 2.053 || 2.038 ||  |
| 2.048 || 2.045 || 2.037 || 2.048 || 2.044 || 2.043 ||  |
| 2.037 || 2.042 || 2.038 || 2.061 || 2.045 || 2.055 ||  |
| 2.052 || 2.024 || 2.036 || 2.042 || 2.056 || 2.037 ||  |
| 2.044 || 2.04 || 2.043 || 2.061 || 2.037 || 2.04 ||  |
| 2.046 || 2.047 || 2.045 || 2.042 || 2.048 || 2.029 ||  |
| 2.03 || 2.033 || 2.042 || 2.043 || 2.055 || 2.04 ||  |

The graph in Fig. (**2**) shows the data points found experimentally. The X-axis shows the sample space, and Y-axis indicates the **time period** of a simple pendulum in seconds.

![](Images/9789815124842-C2-F2.jpg)**Fig. (2))**  
Experimental Observations.

The program below uses basic MATLAB commands.

|![](Images/9789815124842-C2-F3A.jpg)|

Fig. ([**3**](#9789815124842-C2.html#f3)) shows the output screen.

The estimated value of **Time Period** after the Kalman Filter process is equal to 2.0432 *seconds*. Using Equation (3.1), the value of **acceleration due to gravity** for Earth (`g`) is calculated and is equal to 9.8248 *ms*^(−2)

Fig. ([**4**](#9789815124842-C2.html#f4)) shows a graph for the *estimated values* (solid line), which eventually converges to a particular true value. Although, the result may not be accurate because of external factors like air resistance, extensible string, string with mass, *etc.* But these have been neglected. The scattered points show the experimental data values, while the solid line shows the estimated values.

![](Images/9789815124842-C2-F3.jpg)**Fig. (3))**  
Output Screen. ![](Images/9789815124842-C2-F4.jpg)**Fig. (4))**  
Experimental Observations with Kalman Filtered Estimated Values.

## EXAMPLE 3: VERIFYING HUBBLE’S LAW

Hubble’s Law was stated by Hubble in his article (PNAS) in 1929. It is the observed relation between the recession velocity of galaxies and their distance. This law is a landmark in observational cosmology, the study of the big vast universe, which is supposed to be nearly 14-18 billion years [[6](#9789815124842-C2.html#r6)].

The study of the universe is totally incomplete without the observations which are to be suitably analysed and assessed to make conformity with the theoretical models [7, 8].

Let `V[r]` be the **recessional velocity** in *kms*^(−1) and `D` be the **distance** from the observer (Earth in this case) in mega-parsecs *Mpc*. The Hubble’s Law states that:

|![](Images/9789815124842-C2-EQ44.jpg)||(44)|

where, `H[o]` is known as **Hubble’s constant**, it represents the constant rate of cosmic expansion caused by the stretching of space-time itself. The Hubble’s Law is now well established for the Local Universe (`V[r]` < 30,000*kms*^(−1)) [[9](#9789815124842-C2.html#r9)].
