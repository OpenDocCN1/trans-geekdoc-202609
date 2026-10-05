Indeed, the Green filter and the delta filter operator are related:

$$\delta(EI-H) = -\frac{1}{\pi}	ext{Im}G(E) \quad [71]$$

and the spectral method illustrated for the delta filter can be readily implemented for the Green filter. To that end, the exponential Fourier transform replaces a cosine Fourier transform.

The major shortcoming of the spectral method is the rate of convergence. Its ability to resolve eigenvalues is restricted by the width of the filter, which in turn is inversely proportional to the length of the Fourier series (the uncertainty principle). To accurately characterize an eigenpair in a dense spectrum, one might have to use a very long Chebyshev recursion.

# FILTER-DIAGONALIZATION

Spectral methods, whether based on time or Chebyshev propagation, converge slowly because of the uncertainty principle. This behavior stems from the fact that the time or Chebyshev propagation is energy global, providing a uniform convergence in the entire energy range. Nehauser suggested an elegant scheme that combines propagation with diagonalization to overcome this shortcoming. The central idea is to first construct a set of primitive energies in a specified energy window via a propagation, which is denoted as filtering. These primitive bases need not be well resolved in energy. Consequently, the propagation length can be shortened significantly by solving a small local generalized eigenproblem via direct diagonalization. The original *filterdiagonalization (FD)* method of Nehauser was formulated based on time propagation and the time-conjugacy. It has been extended to other types of propagation. Here, we discuss two implementations based on the Chebyshev and Lanczos recursions.

# Filter-Diagonalization on Chebyshev Recursion

To define the method, we first define a filter operator using the Chebyshev propagator. The definition given in a similar manner, but it is not discussed here because it is considered to be inferior to the Chebyshev-based approach. However, we note in that the time-based FD is very important in signal processing, which is an important topic in many fields. The form of the filter is flexible, but it should enrich components near the energy of interest and depress contributions elsewhere. Both the Green operator and the spectral