+   (iv) Take the derivative of the results of (iii) with respect to t, in the normal direction of the plane.

+   (v) Perform the 3D Radon backprojection (see Figure 5.8).

We now expand on Step (iii). For a practical focal-point orbit, the (s, \(\bar{\theta}\)) Radon space is not uniformly sampled. Data redundancy must be properly weighted. For example, if the value at a particular Radon space location (s, \(\bar{\theta}\)) is measured three times, then after rebinning this value needs to be divided by 3.

Grangeat's algorithm is not an FBP algorithm, and it requires data rebinning, which can introduce large interpolation errors.

# 5.3.3 Katsevich's algorithm

Katsevich's cone-beam algorithm was initially developed for the helical orbit cone-beam geometry and was later extended to more general orbits. Katsevich's algorithm is in the form of FBP, and the filtering can be made shift invariant. By shift invariant we mean that the filter is independent of the reconstruction location.

Using a helical orbit (Figure 5.9), Tuy's data sufficiency condition is satisfied. The main issue in developing an efficient cone-beam FBP algorithm is to properly normalize the redundant data. Katsevich uses two restrictions to handle this issue.

It can be shown that for any point (x, y, z) within the volume surrounded by the helix, there is a unique line segment that passes through the point (x, y, z) where both endpoints touch two different points on the helix and are separated by less than one pitch, say, at s<sub>b</sub> and s<sub>t</sub> shown in Figure 5.13. This particular line segment is referred to as the \(\pi\)-segment (or \(\pi\)-line). The first restriction is the use of the cone-beam measurements that are measured only from the helix orbit between s<sub>b</sub> and s<sub>t</sub>.

The second restriction is the filtering direction, which handles the normalization of redundant data. In order to visualize the data redundancy problem, let us look at three cone-beam image reconstruction problems: (a) data are sufficient and not redundant; (b) data are insufficient; and (c) data are sufficient but redundant.

(a) The scanning cone-beam focal-point orbit is an arc (i.e., an incomplete circle). The point to be reconstructed is in the orbit plane and on the line that connects the two endpoints of the arc. The line connecting the arc's endpoints is the \(\pi\)-segment of the reconstruction point. For our special case that the object is only a point, the cone-beam measurement of this point at one focal-point position can provide a set of plane integrals of the object. Those planes all contain the line that connects the focal point and the reconstruction point. After the focal point goes through the entire arc, all plane integrals are obtained. Recall the central slice theorem for the 3D Radon transform; an exact reconstruction requires that the planar integrals of the object are available for all directions \(\bar{\theta}\), which is indicated in Figure 5.14 (top).