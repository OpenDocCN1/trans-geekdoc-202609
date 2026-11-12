![](bbox=[0.27, 0.09, 0.78, 0.35])

Figure 15.2 RGB color space.

# 15.3.1.1.2 HSV

The three elements of hue, saturation, and value are used to define colors in the HSV color system. Colors are classified according to their hue (red, blue, etc.), saturation (the more vibrant they are, the less grey is present), and value (brightness). Once more a representation that depends on the device, HSV is defined in relation to the RGB color space. A straightforward formula can be used to convert RGB values to HSV coordinates. Colors with similar values are viewed similarly by the human eye because HSV is perceptually homogeneous. Especially in application interfaces, user browse the color space to choose an example, HSV space is frequently utilised in computer graphics.

# 15.3.1.1.3 Opponent Color Space

To support the hypothesis that human color vision employs an opponentcolor model, wherein certain colors are never perceived to occur together. In contrast, it is simple to recognise mixture of green and yellow, red and blue, green and blue, and, red and yellow. For instance, a color perception is not described as bluish yellows or reddish-greens. It is suggested that the opponent color space be used for encoding the color to the opposite signal considering observations. Three parts—R-G, 2B-RG, and R+B+G—are distinguished from the RGB values. The benefit of this style of representation is that it isolates the brightness of data into the 3rd channel.

# 15.3.1.1.4 CIELUV and CIELAB

These are suitable models for image retrieval because CIELAB and CIELUV spaces satisfy the requirement for spatial homogeneity. They have perceptually homogenous color spaces and are completely independent of the type of device being utilised. The brightness (L) and 2 chromatic elements (A and B), which stand for the separations between magenta, green, yellow and blue, so far, make up the three components of the model. CIE LUV is created to improve the linearity of color perception.