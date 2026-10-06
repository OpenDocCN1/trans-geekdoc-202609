# Distribution Shift

Problems are often caused by a distribution shift between train and inference time

Training Dataset
Real Scenario: Out of Distribution (O.O.D) data

![](bbox=[0.107, 0.345, 0.436, 0.503])

![](bbox=[0.536, 0.345, 0.665, 0.523])

![](bbox=[0.676, 0.442, 0.863, 0.672])

![](bbox=[0.182, 0.526, 0.351, 0.683])

![](bbox=[0.506, 0.536, 0.656, 0.693])

Source: https://www.bdd100k.com/
Source: https://www.youtube.com/2016/4/21/11447838/self-driving-cars-challenges-obstacles
https://autuncar.com/1262/Autonomous-Cars-are-Having-Trouble-With-Animals
https://www.extremetech.com/extreme/189486-how-googles-self-driving-cars-detect-and-avoid-obstacles

Independent and Identically Distributed (L.I.I.D.) : $P_{train}(x,y) = P_{test}(x,y)
Out of Distribution (O.O.D): $P_{train}(x,y) 
eq P_{test}(x,y)$

Gerhard Neumann | Machine Learning | KIT | SS2024