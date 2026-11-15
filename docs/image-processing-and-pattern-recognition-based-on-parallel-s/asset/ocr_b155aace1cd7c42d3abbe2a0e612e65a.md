![](bbox=[0.25, 0.1, 0.75, 0.28])

Fig. 6.2: Formation of ranges of subclasses of integral coefficients based on permissible accuracy dk

templates (nAi = 1). With increase in the number of subclasses nAi the required value of this parameter will only decrease.

With technical implementation of the pattern recognition system based on PST, the calculation roundings, loss of data and other information distortion are possible. These factors limit the values of this error. Due to the mentioned circumstances, the formula for real integral factors will change slightly.

```
k_{xN} = \frac{kNc \cdot \frac{S_0}{S_A} \cdot X_{max} + \int_{0}^{X_{max}} FAI(x)dx}{(S_0 + kNc)X_{max}}
```

where k_{xN} is the real integral coefficient for the x direction in the presence of noise in the image, kNc is the amount of noise elements that are not deleted and S_A is the total area of the receptor field.

Then the value is

```
dk \ge |k_{xN} - k_x|
```

After transformation, this formula takes the following form:

```
dk \ge \left| \frac{kNc}{S_A} \right| \left| \frac{S_A - S_0}{2S_0 + \frac{kNc}{S_A}S_A} \right| .
```

The data of normalised values of the number of elements that are not removed in the process of noise control using 3x3 matrix can be taken from Fig. 6.1a. The ratio of area of the receptor field to the area of the image will be called rS.

```
rS = \frac{S_A}{S_0} .
```