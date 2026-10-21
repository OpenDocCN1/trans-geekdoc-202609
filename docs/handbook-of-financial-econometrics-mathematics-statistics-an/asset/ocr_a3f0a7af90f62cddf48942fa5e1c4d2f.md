Using $P = P(t, x_t)$ for shorthand notation and recalling that bond prices satisfy the partial differential equation (PDE):

$$rP = -\frac{\partial P}{\partial \tau} + \sum_{i=1}^{N}\frac{\partial P}{\partial x_i}m_i^{\mathbb{Q}} + \frac12\sum_{i,j,k=1}^{N}\frac{\partial^2 P}{\partial x_i\partial x_j}\sigma_{ik}\sigma_{jk}\tag{61.40}$$

with

$$\frac{\partial P}{\partial \tau}=\frac{\partial(e^{-\tau Y(x_t,\tau)})}{\partial \tau}=e^{-\tau Y(x_t,\tau)}\Big[-\tau\frac{\partial Y(x_t,\tau)}{\partial \tau}-Y(x_t,\tau)\Big]=P[-\tau Y_\tau -Y]$$

$$\frac{\partial P}{\partial x_i}=\frac{\partial(e^{-\tau Y(x_t,\tau)})}{\partial x_i}=-\tau\frac{\partial Y(x_t,\tau)}{\partial x_i}e^{-\tau Y(x_t,\tau)}=-\tau Y_i P$$

$$\frac{\partial^2 P}{\partial x_i\partial x_j}=\frac{\partial}{\partial x_i}\Big(\frac{\partial P}{\partial x_j}\Big)=\frac{\partial}{\partial x_i}(-\tau Y_j P)=-\tau\Big[\frac{\partial P}{\partial x_i}Y_j+P\frac{\partial Y_j}{\partial x_i}\Big]$$
$$=-\tau\Big[-\tau Y_i P Y_j+P\frac{\partial}{\partial x_i}\Big(\frac{\partial Y}{\partial x_j}\Big)\Big]$$
$$=\Big[\tau^2 Y_i Y_j-\tau\frac{\partial^2 Y}{\partial x_i\partial x_j}\Big]P=[\tau^2 Y_i Y_j-\tau Y_{ij}]P$$

and,

$$Y_\tau=\frac{\partial Y}{\partial \tau}$$

$$Y_i=\frac{\partial Y}{\partial x_i}$$

$$Y_{ij}=\frac{\partial^2 Y}{\partial x_i\partial x_j}.$$

Thus,

$$rP=P[\tau Y_\tau+Y]-\tau P\sum_{i=1}^{N}Y_i m_i^{\mathbb{Q}}+P\frac12\sum_{i,j,k=1}^{N}[\tau^2 Y_i Y_j-\tau Y_{ij}]\sigma_{ik}\sigma_{jk}\tag{61.41}$$

or

$$r=[\tau Y_\tau+Y]-\tau\sum_{i=1}^{N}Y_i m_i^{\mathbb{Q}}+\frac12\sum_{i,j,k=1}^{N}[\tau^2 Y_i Y_j-\tau Y_{ij}]\sigma_{ik}\sigma_{jk}.\tag{61.42}$$

Next, we note that we can use a Taylor series expansion to write out bond yields as,

$$Y(x_t,\tau)\equiv Y^0(x_t)+\tau Y^1(x_t)+\frac12\tau^2 Y^2(x_t)+\cdots\tag{61.43}$$