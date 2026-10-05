
## 332 Recursive Solutions to Large Eigenproblems

and their discretization schemes. 12,261,272,319–325 The appropriate kinetic energy operator used in a variational calculation depends on the molecular geometry of the potential energy minimum of interest. Understandably, it is difficult to choose a coordinate system for floppy molecules or for highly spectral regions where more than one molecular configuration is possible.

Much progress has also been made recently on basis contraction schemes for recursive methods. The essence of these schemes is to construct non-direct product bases that have smaller sizes and narrower spectral ranges. One possibility is to prune the direct product basis using a set of criteria such as energy. In a DVR, for example, this amounts to the removal of all grid points above a cut-off potential energy. This strategy has been successfully used by several authors. 241,264,272,326 An alternative contracting scheme is to treat the system into several subsystems, on which the Hamiltonians can be used to construct the complete basis. 262,273 This approach involves solving not only the full eigenproblems, but also for the smaller subsystems, which are all amenable to recursive diagonalization methods. Applications of this contraction idea have allowed for the determination of energy levels in polyatomic systems with up to 12 degrees of freedom.200,201,205,327 It is expected that this research area will remain active and vital to advance further the recursive methods. 328–331

## ACKNOWLEDGMENTS

I am deeply indebted to my research group, Guohui Li, Shenmin Li, Shi Lin Gu, Daqiang Xie, and Dingguo Xu, especially Rongqing Chen. I would also like to thank Stephen Gray, Vladimir Mandelstam, Tucker Carrington, Jr., and Hua-gen Yu for many-depth discussions regarding recursive diagonalization approaches and related topics. I dedicate this review to my parents for their eternal love and encouragement. This work was funded by the National Science Foundation.

## REFERENCES

- 1. A. Messiah, Quantum Mechanics, Wiley, New York, 1968.
- 2. W. J. Jehre, L. Radem, P. R. Scholz, and J. A. Pole, Ab Initio Molecular Orbital Theory, New York, 1996.
- 3. D. G. Carney, L. Spandel, and C. W. Kern, Adv. Chem. Phys., 37, 305 (1978). Variational Approaches to Vibrational-Rotation Spectroscopy for Polyatomic Molecules.
- 4. S. Carter and N. C. Handy, Comput. Phys. Rep., 5, 115 (1986). The Variational Method for the Calculation of Ro-Vibrational Energy Levels.
- 5. Z. Bacic and J. C. Light, Annu. Rev. Phys. Chem., 40, 469 (1989). Theoretical Methods for Rovibrational States of Floppy Molecules.
- 6. D. G, Truhlar, Resonances in Electron-Molecule Scattering, van der Waals Complexes, and Reactive Chemical Dynamics, ACS, Washington, D.C., 1984.
- 7. J. Z. H. Zhang, Theory and Application of Quantum Molecular Dynamics, World Scientific, Singapore, 1999.
- 8. R. Shinke, Photodissociation, Cambridge University Press, Cambridge, United Kingdom, 1993.
- 9. R. Kosloff, in Dynamics of Molecular and Chemical Reactions, R. E. Wyatt and J. Z. H. Zhang, Marcel Dekker, New York, 1996, pp. 185–230. Quantum Dynamics on Grids.
- 10. J. C. Light and T. Carrington Jr., Ads: Chem. Phys., 114, 263 (2000). Discrete-Variable Representations and Their Utilization.
- 11. D. Feller and E. R. Davies, in Reviews in Computational Chemistry, Vol. 1, K. R. Lipkowitz and D. B. Boyd, VCH, Wiley, 1990, pp. 1–43. Base Sets for Ab Initio Molecular Calculations and Intermolecular Interactions.
- 12. J. M. Bradley and T. Carrington Jr., Chem. Phys., 99, 8519 (1993). A General Variable Method to Calculate Vibrational Energy Levels of Three-Four Atoms.
- 13. J. M. Bradley and T Carrington Jr., J. Chem. Phys., 101, 8494 (1994). Calculation of Triatomic Vibrational Eigenvalues: Contracted Basis Sets, Lanczos or Conventional Eigensolver? What is the Most Efficient Combination?
- 14. G. C. Corey, Y. W. Tromp, and D. Lemoine, Numerical Methods and Their Applications to Schrödinger Equation, C. Cerjan, Ed., Kluwer, Dordrecht, The Netherlands, 1993, pp. 1–23. Pseudospectral Galerian Curvilinear Coordinates.
- 15. J. M. Bradley, J. W. Tromp, T Carrington Jr., and G. C. Corey, Chem. Phys., 100, 6175 (1994). Calculation of Highly Excited Vibrational Energy Levels of Polyatomic Modes of H up to 35000 cm⁻¹.
- 16. G. Gazko, V. Szalay, A. G. Costar, and T. Furrenbach, J. Chem. Phys., 122, 024101 (2005). Treating Singularities in the Surface-Vibrational Hamiltonian in Orthogonal Internal Coordinates.
- 17. J. K. L. McDonald, Rev. Phys., 48, 830 (1993). Successive Approximations for the Rayleigh-Ritz Method. The Johns Hopkins University Press, Baltimore, 1996.
- 18. W. H. Press, S. A. Teukovsky, W. T. Vertering, and B. P. Flannery, Numerical Recipes, 2nd ed, Cambridge University Press, Cambridge, United Kingdom, 1992.
- 19. B. Parker, The Symmetric Eigenvalue Problem, Prentice-Hill, Englewood Cliffs, New Jersey, 1980.
- 20. J. M. Bowen and B. Gazay, J. Chem. Phys., 94, 454 (1991). A Truncation/Recycling Method for Base Sets for Calculations of Eigenvalues and Eigenvectors.
- 21. S. E. Choi and J. C. Light, J. Chem. Phys., 97, 7031–7054 (1992). Highly Excited Vibrational Eigenvalues of Nonlinear Triatomic Molecules. Application to H2O.
- 22. C. Offenschfeld, J. Kassmann, and D. S. Barnett, in Reviews in Computational Chemistry, Vol. 23, K. B. Lipkowitz and T. R. Cund,, Wiley, New York, 2006. Linear Scaling Methods in Quantum Chemistry.
- 23. Y. Saad, Numerical Methods for Large Eigenvalue Problems, Manchester University Press, Manchester, United Kingdom, 1992.
- 24. C. Lanczos, Res. Nat. Bur. Stand., 45, 255 (1950). An Iteration Method for the Solution of the Eigenvalue Problem of Linear Differential and Integral Operators.
- 25. C. C. Paige, J. Inst. Math. Appl., 10, 373 (1972). Computational Variants of the Lanczos Method for the Eigenproblem.
- 26. J. K. Callum and R. Willoughby, Res. Nat. Bur. Stand., 45, 255 (1950). An Iteration Method for the Solution of the Eigenvalue Problem of Linear Differential and Integral Operators.
- 27. K. B. Lipkowitz and T. R. Cund,, Wiley, New York, 2006. Linear Scaling Methods in Quantum Chemistry.
- 28. Y. Saad, Numerical Methods for Large Eigenvalue Problems, Manchester University Press, Manchester, United Kingdom, 1992.
- 29. C. C. Paige, J. Inst. Math. Appl., 10, 373 (1972). Computational Variants of the Lanczos Method for the Eigenproblem.
- 30. Y. Saad and M. Schultz, SIAM J. Sci. Comput., 7, 856 (1986). Conjugate Gradients
- 31. R. W. Freund and N. A. Nach, Numer. Math., 60, 315 (1991). QMR: A Quasi-Minimal Method.
- 32. R. W. Freund, SIAM J. Sci. Comput., 13, 425 (1992). Conjugate Gradient-Type Methods
- 33. R. Barrett, M. Terry, J. Demmel, J. Dong, V. Eijhout, R. Pozo, and H. van der, Templates for the Solution of Linear Systems: SIAM, Philadelphia, 1994.
- 34. J. H. Wilkinson, The Eigenvalue Problem, Clarendon Press, Oxford, 1965.
- 35. C. C. Paige, J. Inst. Math. Appl., 18, 34 (1976). Error Analysis of the Lanczos Algorithm
- 36. C. C. Paige, Linear Algebra and Appl., 34, 235 (1980). Accuracy and Effectiveness of the Lanczos Algorithm
- 37. J. Callum and R. Willoughby, Comput. Phys., 44, 329 (1981). Computing Eigenvalues of Symmetric Matrices
- 38. R. Chen and H. Guo, Chem. Phys., 111, 9994 (1999). A Single Lanczos Algorithm
- 39. N. Pauline, M. J. Bramley, T. Carrington, Jr., G. Kjaergaard, and B. R. Henry, J. Chem. Phys., 104, 7807 (1996). Calculation of Vibrational (J) Excitation Energies and Binding Interactions of Formaldehyde
- 40. R. Chen and H. Guo, Chem. Phys., 277, 191 (1997). Benchmark Calculations of Convergence in Lanczos Algorithm
- 41. R. Chen and H. Guo, Chem. Phys., 369, 650 (2003). Effect of Spectral Range on Lanczos and Chebyshev Residual Methods.
- 42. R. Chen and H. Guo, Chem. Phys., 319, 5762 (2003). On the Convergence Scaling of Lanczos: The Recursive-Residual Generation Method.
- 43. A. Nauts and R. E. Wyatt, Phys. Lett., 51, 2238 (1983). New Approach to Many-State Quantum Dynamics: The Recursive-Residual Generation.
- 44. A. Nauts and R. E. Wyatt, Phys. Rev. A, 30, 872 (1984). Theory of Laser-Molecule Interaction: The Recursive-Residual Generation.
