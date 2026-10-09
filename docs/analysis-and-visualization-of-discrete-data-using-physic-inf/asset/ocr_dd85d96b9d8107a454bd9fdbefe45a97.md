![](bbox=[0.13, 0.11, 0.89, 0.44])

Figure 4.42. NN structure and $E_{\mathrm{int}}$.

exact solutions. For comparison, in FDM, $\Delta x$, $\Delta t$ (mesh width) are determined so that the Courant number is 1 or less and the average is as large as possible within the domain. Figure 4.43 shows the results of comparison with FDM. Of these two methods, the PINN method provides the most accurate solution (Figure 4.43).

Figure 4.44 shows the parallel coordinates of $E_{\mathrm{int}}$ when the approximate solution of the KdV equation is computed in N10.

# 4.3.4.4. *One-dimensional Poisson’s equation*

This section compares the results of solving a one-dimensional Poisson’s equation using PINNs with the results of solving it using FDM based on their exact solutions. For comparison, in FDM, $\Delta x$, $\Delta t$ (mesh width) are determined so that the Courant number is 1 or less and the average is as large as possible within the domain. Figure 4.45 shows the results of comparison with FDM. Of these two methods, the PINN method provides the most accurate solution (Figure 4.45).

Figure 4.46 shows the parallel coordinates of $E_{\mathrm{int}}$ when the approximate solution of Poisson’s equation is computed in N10.