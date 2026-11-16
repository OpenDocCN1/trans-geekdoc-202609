states, three models achieved errors below 5.15%. Another model based on the Mori-Tanaka formalism did not compare favorably.

+   - We demonstrated that the anisotropic shear-thinning behavior of the considered suspensions can be encoded to engineering accuracy using a generalized distance, which depends on an orientation state specific orthotropic tensor and the strain rate tensor.

# Chapter 5:

+   - By leveraging results for linear elastic laminates, we derived closed form expressions for the effective viscosity of layered emulsions with linearly viscous phases. This paved the way for the development of DMNs for the treatment of fiber suspensions.

+   - For incompressible phases, we derived necessary and sufficient conditions for the rank and the layering directions of a coated layered material, such that its effective properties are non-singular, even if the core phase is rigid. In particular, the rank of the coated layered material must be greater than two, and the layering directions must be mutually non-orthogonal and mutually non-collinear.

+   - We presented the Flexible Deep Material Network (FDMN) architecture as an extension of the direct DMN Framework. In an FDMN, the lowest homogenization layer consists of coated layered materials instead of rank-one layered materials as in a typical direct DMN. This allows the practical treatment of infinite material contrast, which was highly difficult previously. Similar to a direct DMN, the remaining layers of an FDMN consist of rank-one layered materials.

+   - For 31 fiber orientation states, we demonstrated that FDMNs achieve a competitive prediction accuracy for the viscous behavior of rigid fibers suspended in a shear-thinning PA6 matrix. We observed a maximum error of 4.31%, which lies below the prediction error of the models presented in chapter 4.

+   - Compared to the models presented in chapter 4, FDMNs were trained on linear homogenization data, and do not incorporate knowledge