
```matlab
4 >>w=[0 -1 0;-1 5 -1;0 -1 0];
5 >>Rf=imfilter(R,w);
6 >>Gf=imfilter(G,w);
7 >>Bf=imfilter(B,w);
8 >>RGBf(:,:,1)=Rf;
9 >>RGBf(:,:,2)=Gf;
10 >>RGBf(:,:,3)=Bf;
```

Commands 1–3 separate each of the planes and assign them to the variables R, G, and B. Command 4 generates the matrix of coefficients of the spatial filter defined in Equation 2.70 (for more details, see Section 1.5). Commands 5–7 perform spatial filtering on each plane using the filter defined in command 4. Lastly, 8–10 of the filtered planes are integrated to produce the new color image with better sharpness. Figure 2.31 shows a sharpened color image obtained from executing the commands described above.

## 2.14 Vector Processing of Color Images

Until now, in the previous sections, the operations were carried out considering the planes independently. However, there are cases in which it is necessary to work with the entire vector of intensity values in all planes simultaneously. There is an important set of operations that require direct processing of the data vector. In this section, only the case of edge detection in color images will be described since this application is considered one of the most common.

![](img/fa2d7e8bd88af7122f764c748b0a3723_102_0.png)

FIGURE 2.31 Color image whose sharpness has been enhanced by using a Laplacian filter. (a) Original image and (b) image with enhanced sharpness obtained after executing the set of MATLAB® commands described above.

### 2.14.1 Edge Detection in Color Images

The gradient can be considered as the derivative of a multidimensional function along a coordinate axis (with respect to one of the function variables), for example,

\( G_x = \frac{\partial I}{\partial x}(x, y), G_y = \frac{\partial I}{\partial y}(x, y) \quad (2.72) \)

The formulations of Equation 2.72 represent the partial derivative of the image function with respect to the variable \( x \) or \( y \). The vector

\( \nabla I(x, y) = \begin{bmatrix} \frac{\partial I}{\partial x}(x, y) \\ \frac{\partial I}{\partial y}(x, y) \end{bmatrix} \quad (2.73) \)

\( \nabla I(x, y) \) symbolizes the vector of the gradient of the function \( I \) at the point \( (x, y) \). The magnitude of the gradient is defined as follows:

\( |\nabla I| = \sqrt{ \left( \frac{\partial I}{\partial x} \right)^2 + \left( \frac{\partial I}{\partial y} \right)^2 } \quad (2.74) \)

\( |\nabla I| \) is invariant to image rotations and thus also independent of the orientation of the structures contained in it. This property is important for locating the edge points of the image. Under such conditions, the value of \( |\nabla I| \) is the practical value used in most of the algorithms for edge detection. \( |\nabla I| \) is often approximated by using the following model:

\( |\nabla I| = \left| \frac{\partial I}{\partial x} \right| + \left| \frac{\partial I}{\partial y} \right| \quad (2.75) \)

This approximation avoids the calculation of the power and the square root operations, which makes it computationally more economical.

An important characteristic of the gradient vector (Equation 2.73) is its direction, which expresses the angle where the maximum value of the gradient is presented. This direction can be calculated as follows:

\( \theta(x, y) = \tan^{-1} \begin{bmatrix} \frac{\partial I}{\partial y} \\ \frac{\partial I}{\partial x} \end{bmatrix} = \tan^{-1} \left( \frac{G_y}{G_x} \right) \quad (2.76) \)

The difference between pixels within small neighborhood regions approximates the value of the gradient in practice. Equation 2.77 shows the coefficient matrices of the Sobel filter, one of the most common for the calculation of the magnitude of the gradient. Chapter 3 provides a more detailed explanation of how these differences are established, as well as the most common filters used to calculate the magnitude of the gradient.

\( G_x = \begin{bmatrix} -1 & -2 & -1 \\ 0 & 0 & 0 \\ 1 & 2 & 1 \end{bmatrix} \quad \text{and} \quad G_y = \begin{bmatrix} -1 & 0 & 1 \\ -2 & 0 & 2 \\ -1 & 0 & 1 \end{bmatrix} \quad (2.77) \)

The gradient value computed under Equation 2.77 is the most common method for determining the edges in a grayscale image, as discussed in Chapter 3. However, this method is applied only to intensity images. Under such conditions, this process needs to be extended for color images such as RGB. One way to extend the process to color images is to find the gradient for each color plane and combine their results. This methodology is not a good solution since there will be color regions that cannot be detected by this method, and therefore their borders cannot be calculated.

The problem is to define both the magnitude of the gradient and its direction from the color vector defined in Equation 2.61. One of the most common ways to extend the gradient concept to vector functions is described below.

Consider the unit vectors \(\boldsymbol{r}\), \(\boldsymbol{g}\), and \(\boldsymbol{b}\) as the unit vector that describes the RGB color space (see Figure 2.1), from which the following vector relationships are defined:

\(\boldsymbol{u} = \frac{\partial R}{\partial x}\boldsymbol{r} + \frac{\partial G}{\partial x}\boldsymbol{g} + \frac{\partial B}{\partial x}\boldsymbol{b} \\
\boldsymbol{v} = \frac{\partial R}{\partial y}\boldsymbol{r} + \frac{\partial G}{\partial y}\boldsymbol{g} + \frac{\partial B}{\partial y}\boldsymbol{b} \quad (2.78)\)

From these relations, the following vector products are defined:

\(g_{xx} = \boldsymbol{u} \cdot \boldsymbol{u} = \boldsymbol{u}^T \cdot \boldsymbol{u} = \left(\frac{\partial R}{\partial x}\right)^2 + \left(\frac{\partial G}{\partial x}\right)^2 + \left(\frac{\partial B}{\partial x}\right)^2 \\
g_{yy} = \boldsymbol{v} \cdot \boldsymbol{v} = \boldsymbol{v}^T \cdot \boldsymbol{v} = \left(\frac{\partial R}{\partial y}\right)^2 + \left(\frac{\partial G}{\partial y}\right)^2 + \left(\frac{\partial B}{\partial y}\right)^2 \quad (2.79) \\
g_{xy} = \boldsymbol{u} \cdot \boldsymbol{v} = \boldsymbol{u}^T \cdot \boldsymbol{v} = \left(\frac{\partial R}{\partial x}\right)\left(\frac{\partial R}{\partial y}\right) + \left(\frac{\partial G}{\partial x}\right)\left(\frac{\partial G}{\partial y}\right) + \left(\frac{\partial B}{\partial x}\right)\left(\frac{\partial B}{\partial y}\right)\)

An important observation results from the fact that both $R$, $G$, and $B$, as well as the values of $g_{xx}$ $g_{yy}$ and $g_{xy}$ are functions that depend on $x$ and $y$. Considering the previous notation, Di Zenso showed that the direction where the maximum value of change of the color vector $c(x, y)$ is found as a function of $(x, y)$ is defined as follows:

$\theta(x, y) = \frac{1}{2} \tan^{-1} \left[ \frac{2g_{xy}}{(g_{xx} - g_{yy})} \right]$ (2.80)

While the maximum value $M(x, y)$ of the gradient occurs in the $\theta(x, y)$ direction. $M(x, y)$ is calculated as follows:

$M(x, y) = \left\{ \frac{1}{2} \left[ (g_{xx} + g_{yy}) + (g_{xx} - g_{yy}) \cos(2\theta) + 2g_{xy} \sin(2\theta) \right] \right\}$ (2.81)

It is important to note that both $\theta(x, y)$ and $M(x, y)$ produce matrices of the same dimension as the color image whose edges need to be found.

Because $\tan(\alpha) = \tan(\alpha \pm \pi)$, if $\theta$ is a solution of Equation 2.80, then $\theta + \pi / 2$ is also a solution. Considering this, it is true that $M_{\theta}(x, y) = M_{\theta+\pi/2}(x, y)$. Assuming this property, $M(x, y)$ should be calculated only in the middle of the interval $[0, \pi]$. Therefore, the other values can be found by recalculating the values of $M(x, y)$, but this time considering $\theta + \pi / 2$. If the calculation is carried out as described in the previous procedure, there will be two matrices with the values of the gradients $M_{\theta}(x, y)$ and $M_{\theta+\pi/2}(x, y)$. For the final calculation, the maximum of the two will be considered. Figure 2.32 shows the vector gradient magnitude and direction calculated from the algorithm described above.

![](img/fa2d7e8bd88af7122f764c748b0a3723_105_0.png)

![](img/fa2d7e8bd88af7122f764c748b0a3723_105_1.png)

FIGURE 2.32 (a) Vector gradient magnitude and (b) gradient direction.
