We then next calculate the trace and determinant of matrix M to find R, where R is:

$R = det(M) - k(trace(M))^2$ (2.4)

where,

+   - det(M)=λ1λ2
+   - trace(M)=λ1+λ2
+   - λ1 and λ2 are the eigenvalues of M

So, the magnitudes of these eigenvalues decide whether a region is a corner, an edge, or flat.

+   - When |R| is small, which happens when λ1 and λ2 are small, the region is flat.
+   - When R<0, which happens when λ1>>λ2 or vice versa, the region is edge.
+   - When R is large, which happens when λ1 and λ2 are large and λ1~λ2, the region is a corner.

A simple mathematical method for identifying which windows exhibit significant differences when moved in any direction is the Harris Corner Detector. Each window has a score R connected to it. We determine which ones are corners and which ones are not based on this score [5]. The Harris Corner Detector is found to be invariant to translation, rotation, and illumination changes [11], but not scale invariant, as well see some algorithms

![](bbox=[0.12, 0.7, 0.88, 0.88])

Figure 2.1 Visualizing corner detection.