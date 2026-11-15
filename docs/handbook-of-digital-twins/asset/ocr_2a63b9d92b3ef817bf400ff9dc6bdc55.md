# 40.3.3.4 Closure of Stiff Skeleton

Skeleton closure is critical for the completed bridge alignment. If stress-free lifting alignment control isn't met, the jointed section length is typically adjusted on-site, making construction harder and causing alignment errors. Ensuring no deviation in the joint section fabrication and installing the cantilever in a stress-free state allows smooth jointing and stress-free lifting of the entire rigid skeleton.

Utilizing 3D scanning technology, point cloud data are gathered for each section before lifting and pre-assembly completion, determining the feasibility of successful skeleton joining. Cable force adjustments are made based on end deviation values, ensuring a seamless arch bridge closure.

Assuming that the deviations of the jointing opening in the stiff skeleton's maximum cantilever state are \(dx_i\) and \(ry_i\), the influence matrix of the unit variation of the initial tensile force on the deviations of the jointing opening is C. The optimization of the cable force can be attributed to the cable force adjustment, and the specific adjustment methods are as follows:

```
\[[C] \begin{Bmatrix} T_1 \\ T_2 \\ \vdots \\ T_n \end{Bmatrix} = \begin{Bmatrix} dx_1 \\ ry_1 \\ \vdots \\ dx_i \\ ry_i \end{Bmatrix} \tag{40.8}\]
```

where \(T_1, T_2, ..., T_n\) denotes the \(n\)th buckler's unit change.

Control of the jointed end deviation from the embedded section is crucial for smooth installation and achieving designed alignment in the completed bridge. Hinge end deviation is derived from assembly results, while distance deviation between cantilever and hinge section ports is obtained through point cloud data-based hinge port plane fitting, utilizing the plane's central coordinate point (Figure 40.3c).

The objective function is the minimum sum of squared deviations or the minimum maximum deviation to achieve collocation with the optimal attitude. The following attitude adjustment equation produces a better collocation attitude and optimal results:

```
\(R_{xyz} = R_\alpha R_\beta R_\gamma T_{xyz} \tag{40.9}\)
```

where \(\alpha, \beta, \text{and } \gamma\) are the rotation angles around the X, Y, and Z axes during the merging section's attitude adjustment, and \(x, y, \text{and } z\) are the translation distances along the X, Y, and Z directions. The following is the splicing error function:

```
\(f \left( \alpha, \beta, \gamma, x, y, z \right) = \sum_{i=1}^{n} \sqrt{(a_1 - b_1)^2 + (a_2 - b_2)^2 + \cdots (a_n - b_n)^2} \tag{40.10}\)
```