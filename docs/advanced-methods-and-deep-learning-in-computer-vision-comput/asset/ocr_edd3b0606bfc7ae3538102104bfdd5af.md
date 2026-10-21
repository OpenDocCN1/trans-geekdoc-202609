operators applied 8 or 12 template masks to ensure that edges of different orientations could be detected. Oddly, it was some time before it was fully realized that as edges are vectors, just two masks should be sufficient to detect them. However, this did not immediately eliminate the problem of deciding what mask coefficients should be used in edge detectors—even in the case of 3 × 3 neighborhoods—and we next proceed to explore this further.

In what follows we initially assume that 8 masks are to be used, with angles differing by 45°. However, 4 of the masks differ from the others only in sign, which makes it unnecessary to apply them separately. At this point, symmetry arguments lead to the following respective masks for 0° and 45°:

$$\begin{bmatrix} -A & 0 & A \\ -B & 0 & B \\ -A & 0 & A \end{bmatrix}\qquad\begin{bmatrix} 0 & C & D \\ -C & 0 & C \\ -D & -C & 0 \end{bmatrix}\tag{1.7}$$

It is clearly of great importance to design masks so that they give consistent responses in different directions. To find how this affects the mask coefficients, we make use of the fact that intensity gradients must follow the rules of vector addition. If the pixel intensity values within a 3 × 3 neighborhood are

$$\begin{bmatrix} a & b & c \\ d & e & f \\ g & h & i \end{bmatrix}\tag{1.8}$$

the above masks will lead to the following estimates of gradient in the 0°, 90° and 45° directions:

$$\begin{aligned} g_0 &= A(c + i - a - g) + B(f - d) \\ g_{90} &= A(a + c - g - i) + B(b - h) \\ g_{45} &= C(b + f - d - h) + D(c - g) \end{aligned}\tag{1.9}$$

If vector addition is to be valid, we also have:

$$g_{45} = (g_0 + g_{90})/\sqrt{2}\tag{1.10}$$

Equating coefficients of a, b, …, i leads to the self-consistent pair of conditions:

$$\begin{aligned} C &= B/\sqrt{2} \\ D &= A\sqrt{2} \end{aligned}\tag{1.11}$$

Next, notice the further requirement—that the 0° and 45° masks should give equal responses at 22.5°. In fact, a rather tedious algebraic manipulation (Davies, 1986) shows that

$$B/A = (13\sqrt{2} - 4)/7 = 2.055\tag{1.12}$$

If we approximate this value as 2 we immediately arrive at the Sobel operator masks

$$S_x = \begin{bmatrix} -1 & 0 & 1 \\ -2 & 0 & 2 \\ -1 & 0 & 1 \end{bmatrix}\qquad S_y = \begin{bmatrix} 1 & 2 & 1 \\ 0 & 0 & 0 \\ -1 & -2 & -1 \end{bmatrix}\tag{1.13}$$