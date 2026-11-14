![](bbox=[0.168, 0.095, 0.703, 0.358])

Fig. 5.10: The coordinate system for Feldkamp's cone-beam algorithm.

Feldkamp's cone-beam algorithm (Section 5.4) is nothing but a modified fan-beam FBP algorithm (Section 3.4.1). It consists of the following steps: (i) Pre-scale the projections by a cosine function cos α (see Figure 5.10 for angle α). (ii) Row-by-row ramp filter the pre-scaled data. (iii) Cone-beam backproject the filtered data with a weighting function of the distance from the reconstruction point to the focal point.

# 5.3.2 Grangeat's algorithm

Feldkamp's algorithm converts the cone-beam image reconstruction problem to the fan-beam image reconstruction problem; Grangeat's algorithm, on the other hand, converts it to the 3D Radon inversion problem (Section 5.2). Feldkamp's algorithm is derived for the circular orbit; Grangeat's algorithm can be applied to any orbit. If the orbit satisfies Tuy's condition, Grangeat's algorithm can provide an exact reconstruction.

Grangeat's method first tries to convert cone-beam ray sums to plane integrals, by calculating the line integrals on the cone-beam detector (see Figure 5.11).

We observe that the line integral on the detector plane gives a weighted plane integral of the object with a special nonuniform weighting function 1/r. Here r is the distance to the cone-beam focal point. We must remove this 1/r weighting before we can obtain a regular unweighted plane integral.

From Figure 5.12 we observe that the angular differential da multiplied by the distance r equals the tangential differential dt, that is, r da = dt. If we perform the angular derivative on the 1/r weighted plane integral, we will cancel out this 1/r weighting