
## Grid Methods for Vanilla Options | 5.4

![](img/9db5fe198f89b66da8d21f3e2bc8868a_156_0.png)

**FIGURE 5.7** The absolute error in the estimated values for a European down and call option ($B < E$) as the number of asset grid points

```
$$\hat{b}_j = 1 - \Theta_m \Delta t - \frac{\Theta_m \sigma^2 S_j^2 \Delta t}{2\Delta S} = 1 - \Theta_m \Delta t \{r + \sigma^2 j^2\}}$$

$$\{\tilde{c}_j = \Theta_m \Delta t + \frac{(r-q)S_j \Delta t + \frac{\sigma^2 S_j^2 \Delta t}{2\Delta S} = \Theta_m \Delta t \{(r-q)j + \sigma^2 j^2\}}$$
```

It can be seen that these coefficients are identical to those given in Section 5.4.2 equation (5.4.16) to equation (5.4.21).

We provide now examples of using nonuniform grids to evaluate European down and call options.

## Valuation of a Down and Out Call Option

Here, the improved accuracy can be achieved by using nonuniform grids instead of uniform grids is illustrated in Figs 5.7 and 5.8. The uniform grids are constructed using the method outlined in Section 5.4 and Code excerpt 5.18. That is, an asset grid line is to coincide with the current asset price $S_0$, and the other grid lines are placed above and below $S_0$ with a uniform spacing of $\Delta S$. The disadvantage of this approach is that there will be an unspecified pricing error depending on the distance, $d_s$, of the barrier level, $B$, to

![](img/9db5fe198f89b66da8d21f3e2bc8868a_157_0.png)

**FIGURE 5.8** The absolute error in the estimated for a European down and out barrier error ($E < B$) as the number of asset grid points, $n_s$, is varied. We show a comparison of the results obtained using both uniform and nonuniform grids; logarithmic transformations are not employed. The algorithm for the uniform grid is described in Section 5.4.3. The Crank–Nicolson method ($\Theta_{m_i} = 0.5$) was used and for the nonuniform grid is outlined in Section 5.4.2, and for the parameters $E = 50.0$, $S_0 = 52.5$, $S_s = 65.0$, $S_{max} = 300.0$, $T = 0.5$, $\sigma = 0.2$, $r = \log(1.1)$, $q = 0.0$, and $n_1 = 100$. The correct option value is 17.0386 obtained using the analytic formulae in Code excerpt 4.7. nearest asset grid. Furthermore, as the number of asset points, $n_s$, increases, the magnitude of $d_s$ will oscillate within the range 0 to $\Delta S/2$.

When $d_s < 0$ the grid will be accurate, but when $|d_s| \sim \Delta S/2$ there will be a large pricing error. This gives rise to the oscillating pricing errors shown in Figs 5.7 and 5.8.

It can be seen from Figs 5.7 and 5.8 that in this case the pricing error is very much less and does not exhibit the profound oscillations that produced by a uniform grid. In Code excerpt 5.19 below, we give the computer program which was used to obtain the nonuniform grid values for the down and out call options presented in Figs 5.7 and 5.8. Although this program only deals with European options, it can be easily altered, using the same techniques as in Code excerpt 5.18, to deal with American style options; this is left as an exercise for the reader.

## Grid Methods for Vanilla Options Section | 5.4

```cpp
void barrier_downout(double barrier_level, double theta_m, double asset_price, double sigma, double r, double T, double strike, double put, double option_value, double greeks[], double q, long ns, long nt, double smax) {
    // the number of asset intervals
    nt // the number of intervals
    double a,b,c,a1,b1,c1,opt_vals,rhs,s,u;
    double ds,time_step;
    long i;
    double t0,t1,t2,mat=0.0;
    long n1,n2,n3;
    double ds_plus,ds_minus,temp1,temp2;
    double D=0;

    n1 = floor(asset_price/smax);
    if (n1 < 0) {
        printf("increase the number of asset points %d\n", n1);
    }
    n2 = ns;
    ds = asset_price/n1;
    time_step = T/n2;
    n3 = n2+2 // number of nodes allocate the required arrays (all of size n3+1)
    s[0]=0;
    s[n1]=asset_price;
    for(i=0; i<n1; i++) {
        s[i+1]=(double)ds;
    }
    // sets below asset price
    for(i=0; i<n2; i++) {
        s[i+1]=asset_price+(double)i;
    }

    // find the index corresponding to barrier level
barrier_index=0;
    while(barrier_level > s[barrier_index]) {
        barrier_index++;
    }
    if (barrier_level == s[barrier_index]) { // decrement barrier index
        barrier_index--;
    }
    if (barrier_level < s[barrier_index]) // then barrier does not correspond to an existing line create another one
        for(i=0; i<n1-barrier_index; i++) {
            s[barrier_index+i+1]+=(double)ds;
        }
        barrier_index++;
        s[barrier_index]=barrier_level;
        if (n1-barrier) {
            n1++;
        }
    }
    // set the RHS and LS coefficients (time step j) a[j], b[j] and c[j] are the LS coefficients for the unknown option values (time step j)
    sig[0]=0;
    time2=time_step/2;
    t1=time_step // theta (for theta method)
    // assign elements of the (n1-2)*(n1-2) tridiagonal matrix */
    for(i=1; i<n1; i++) {
        ds_plus=ds;
        ds_minus=ds;
        D=(ds_plus+ds_minus);
        a[i]=temp1(r-0.5*q-sig[i]*sig[i])*temp1-ds_plus*s[i]*s[i-1]/2;
        b[i]=time_step;
        c[i]=temp1(r-0.5*q-sig[i]*sig[i])*temp1+ds_minus*s[i]*s[i+1]/2;
    }
    c[i]=-time_step*temp1(r-0.5*q-sig[i]*sig[i])*temp1*temp2;
    d[i]=min(ds_plus,ds_minus)/D;
    b[i]=1.8*time_step*temp1(r-0.5*q-sig[i]*sig[i])*temp1+sig[2]*s[i]*s[i+1]*temp2;
```

Code excerpt 5.19 to compute the value of a European down and out barrier option using a nonuniform grid.

The elements of the option but not out of L (they are stored in the array a).
The upper elements of the barrier elements are stored in the array a and the upper diagonal elements of U are just zero.

Matrix L: For the lower triangular matrix L, the diagonal elements are 1 and the lower diagonal elements are l[i]=a[i]/u[i-1], where u is the upper diagonal of U.

```cpp
if (u[0] == 0) printf("error in array u");
for (int i=1; i<n; i++) {
    l[i] = a[i]/u[i-1];
    if (u[i] == 0) printf("error in array u");
}
```

Set values at maturity. Note: opt_vals[i] are the lower and upper (put/call) boundary values.

```cpp
for (int i=0; i<n; i++) {
    opt_vals[i] = max(strike[i], 0);
}
// modify option values to include the barrier
for (int i=0; i<n_barrier; i++) {
    opt_vals[barrier_indices[i]] = 0;
}
```

else { a = p

```cpp
for (int j=0; j<nt; j++) {
    // set up the recursion for the Theta method
    for (int i=1; i<n; i++) {
        rhs[i] = a[i]*opt_vals[i+1] - b[i]*opt_vals[i-1];
    }
    // incorporate constraints at the boundary
    rhs[0] = a[0]*opt_vals[1] - b[0]*opt_vals[0];
    rhs[n-1] = a[n-1]*opt_vals[n-2] - b[n-1]*opt_vals[n-2] - c[n-1]*opt_vals[n-1];
    }
    // solve the triangular system
    for (int i=1; i<n; i++) {
        work[i] = a[i]/u[i-1];
    }
    // solve the system that can compute theta
    for (int i=1; i<n; i++) {
        opt_vals[i] = (rhs[i] - work[i]*opt_vals[i-1])/u[i];
    }
    // store values that can be restored
    if (c[i] == -1 || c[i] == -2) {
        temp[ind] = opt_vals[i];
        ind++;
    }
    // modify values for barrier
    for (int i=0; i<n_barrier; i++) {
        opt_vals[barrier_indices[i]] = 0;
    }
    if (grids[i] // assume an irregular grid) {
        ds_min = s[i]-s[i-1];
        ds_max = s[i+1]-s[i];
        temp[ind] = min(ds_min,ds_max) + (ds_max-ds_min)/0.5;
    }
    gamma = (gamma[i]*ds_min+ds_max+gamma[i+1]*ds_max)/(0.5*(ds_min+ds_max));
    // compute theta like this
    grids[i] = -(temp[i]-4.6*temp[i+1]+3.6*temp[i+2])/(2.6*time_step);
    option_value = opt_vals[i]; // Return option value
}
```

Code example 5.19 (Continued).

## 5.4.4 The Log Transformation and Uniform Grids

Up to this point, we have dealt with the standard Black–Scholes equation, which is
