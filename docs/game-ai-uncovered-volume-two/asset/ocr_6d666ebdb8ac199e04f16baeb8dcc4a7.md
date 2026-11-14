In Image 15.2c, NE returns the greatest length as it would lead the unit to the goals more efficiently than the others. The code to implement this formula is shown in Code Listing 15.1.

```
Code Listing 15.1: The basic formula for increasing the size of each radial.
float influence = DotProduct(Distance.Normal(), Radial[n]);
if(influence > 0)
{
    Radial[n] += influence * Radial[n];
}
```

The same influence scoring for radials can be repeated for other concurrent goals and the score will be cumulative in each direction.

Following the query for objects of interest is the query for dangerous objects. The threat assessment consists of performing ray casts on objects marked as dangerous, as shown in Image 15.2d, which works well for geometry obstacles, but can also include bespoke tests for enemy units that can be cached in a pool for ease of access.

The interest processing, as well as the danger processing, will only affect relevant directions in the alpha plane radials at this time. Once both calculations are concluded, each slot of the radials can be added together as shown in Image 15.3a and b, where N and NE, although with a high-interest score, are disregarded after adding the respective danger, see Image 15.3c. This step leaves E as the most favourable direction at the end of the update cycle and should be considered the resulting vector of the alpha plane Rα, illustrated in Image 15.3d.

![](bbox=[0.11, 0.57, 0.88, 0.71])

IMAGE 15.3 Calculate a context-aware result direction to move to goal Rα. (a) Interest and Danger vectors in each direction, (b) Accumulated vectors, (c) Accumulated vectors overlaid on agent in the environment, (d) The resulting vector assigned.

Once the calculations for optimal direction on the Alpha plane have been performed, the same process can be applied to the Beta plane. At first, three directions seem promising after assessing the Interest Score: N, NE, and E. However, after the obstacle is detected in the NE direction as shown in Image 15.4a, the algorithm must pick between the remaining viable radials, N and E. The latter holds the most promising score due to the dot product calculations. Therefore, E is assigned as the resulting vector for plane Beta, as illustrated in Image 15.4b.