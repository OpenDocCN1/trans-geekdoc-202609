\( FAI(x) = 2 \cdot \frac{S_0}{\pi} \left( arctg \left( \sqrt{\frac{4S_0}{\pi \cdot x^2} - 1} \right) \right) - x \cdot \sqrt{\frac{S_0}{\pi} - \frac{x^2}{4}} \) (2.15)

\( FAI(y) = 2 \cdot \frac{S_0}{\pi} \left( arctg \left( \sqrt{\frac{4S_0}{\pi \cdot y^2} - 1} \right) \right) - y \cdot \sqrt{\frac{S_0}{\pi} - \frac{y^2}{4}} \) (2.16)

If \( x = 0 \) (\( y = 0 \)), then \( FAI(x) = S_0 \) (\( FAI(y) = S_0 \)). When identifying the input image as a circle, determine its radius using the basic parameters of the function of the area of intersection.

\( R = \sqrt{\frac{S_0}{\pi}} = \frac{X_{\max}}{2} \) (2.17)

We define the FAI of the rectangle with sides \( a \) and \( b \) and the tilt angle \( \alpha \) for direction shift \( \varphi \) (Fig. 2.7.):

\( A = a \cdot \cos \alpha + b \cdot \sin \alpha \) \n\( B = a \cdot \sin \alpha + b \cdot \cos \alpha \)

![](bbox=[0.3, 0.44, 0.7, 0.67])

Fig. 2.7: Graphic description of the process obtaining FAI (x) of rectangle

\( FAI(x) = (b - x \cdot \sin \alpha)(a - x \cdot \cos \alpha) = S_0 - Bx + \frac{x^2}{2} \sin(2\alpha) \) (2.18)

\( FAI(y) = (b - y \cdot \cos \alpha)(a - y \cdot \sin \alpha) = S_0 - Ay + \frac{y^2}{2} \sin(2\alpha) \) (2.19)

where

\( A = \frac{S_0}{Y_{\max}} + \frac{Y_{\max}}{2} \cdot \sin(2\alpha) \)