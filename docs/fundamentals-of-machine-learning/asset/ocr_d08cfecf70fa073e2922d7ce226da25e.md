a photograph. Lets say we are given a picture as an RGB image like that is shown in Fig.2.9A. The corresponding program to read this image into an array and to plot it is

# Listing 2.42 CV1.ipynb (part 2)

```
img=plt.imread(`red_dot.png`); img=img[:,:,3]
plt.show(img)
img.shape
```

This is a very small image of size (8,8,3). We had to strip off the fourth channel of the loaded png as a channel in which transparency can be specified. We can modify this image by changing pixels. For example, the code

# Listing 2.43 CV1.ipynb (part 3)

```
img[6,5,1]=0=img[6,5,2]=0
plt.show(img)
```

creates a new red pixel in the image shown in Fig.2.9B. We use this image
The spot that we want to detect with the following program is the structure in
t upper left and not the red pixel with coordinate (6,5) which we just added by
ave we added this red pixel to discuss how we can distinguish between the main
object we are looking for and other objects in the picture. It is interesting to look
at the red, green, and blue channels separately, as in Fig.2.9C. Each of these
 can be produced with a code in an following example for the red channel.

# Listing 2.44 CV1.ipynb (part 4)

```
img\_r=np.zeros((8,8,3))
img\_r[:,:,0]=img[:,:,0]
plt.show(img\_r)
```

Interestingly, when looking at the color channels, one can see that there is a lot of red
t figure, as well as green and blue. The reason that we perceive the red blobs in
 original figure is that there is less green and less blue in these areas.
We can use this fact to handcraft a filter that looks for red pixels. In particular,
s a red pixel is characterized by a large value in the red channel and small values
t other channels, we define a red index by

# Listing 2.45 CV1.ipynb (part 5)

```
red\_index=2+img[:,:,1]-img[:,:,2]
```

The value of red\_index is only if the red channel has a large value and
 if the green and blue channels have small values. This red index is shown in Fig.2.9D.
By taking the maximum of this mapping we find the pixel (6,5) which is the pixel
t with the highest index.

# Listing 2.46 CV1.ipynb (part 6)

```
plt.show(red\_index, cmap='gray')
max\_index=np.argmax(red\_index)
max\_position=np.unravel(max\_index, (8,8))
print(max\_position)
```