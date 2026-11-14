![](bbox=[0.17, 0.09, 0.7, 0.2])

Fig. 2.18: Insufficient views cause artifacts.

**Example 2:** Run a simple Matlab code to show the noise effect. Apply three different window functions to the ramp filter to control noise.

# Solution

The Matlab code:

```
P = phantom(128);
angle = linspace(0,179,180);
R = radon(P,angle);
R = 1e12*imnoise(1e-12*R,'Poisson'); %Add Poisson Noise
I1 = iradon(R,angle,'Ram-Lak');
subplot(1,3,1), imshow(I1, []), title('w/ Ram-Lak filter')
I1 = iradon(R,angle,'Cosine');
subplot(1,3,2), imshow(I1, []), title('w/ Cosine filter')
I1 = iradon (R,angle,'Hann');
subplot(1,3,3), imshow(I1, []), title('w/ Hann filter')
```

The FBP reconstruction results with different window functions are shown in Figure 2.19.

![](bbox=[0.17, 0.64, 0.71, 0.79])

Fig. 2.19: Using different window functions to control noise.