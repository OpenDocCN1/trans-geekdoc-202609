# 2.1.2.2 Macroscale modeling

When modeling composites, fundamentally different approaches have to be considered. The previous homogenization equations are the basis for the following rule of mixture (ROM) and the Voigt and Reuss bounds as first-order energy principles, which can be classified as a macroscopic homogenization approach, as well as the semi-empirical approach of Halpin-Tsai. When modeling on the macroscale, the material is considered as a homogeneous, anisotropic material. Stresses and strains in different directions can be determined by experiments, and reverse-engineering can be used to determine the unknown constants in the phenomenological models ultimately. Although these methods are an obvious simplification of the true situation, since they ignore locally varying material properties that a composite always exhibits, they are popular due to their computational simplicity, especially in industry or for large systems. [5]

# Rule of mixture (Reuss and Voigt bounds)

The simplest micromechanical, energy-based model is the so-called rule of mixture (ROM). Assuming a perfectly aligned unidirectional fiber reinforced composite under uniaxial tension \(\sigma_{11}\) (cf. Figure 2.2) and a still intact material, the strains of matrix and fibers have to be equal as they are bonded to each other.

This follows the so-called Voigt assumption [21]. Furthermore assuming linear elastic behavior of both constituents according to Hooke, this can be written as

\(\varepsilon_c = \varepsilon_m = \varepsilon_f = \frac{\sigma_c}{E_c} = \frac{\sigma_m}{E_m} = \frac{\sigma_f}{E_f}.\) (2.6)

In this and in the following equations, the subscripts c, m and f describe the respective composite, matrix and fiber property.