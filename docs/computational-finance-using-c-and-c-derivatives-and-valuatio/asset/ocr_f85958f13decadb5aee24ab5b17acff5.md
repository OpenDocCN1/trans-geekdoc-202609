# Grid Methods for Vanilla Options Section | 5.4 151

void barrier_downout, double barrier_level, double theta_m, double asset_price, sigma, r, double T,
double strike, long put, double option_value, double greeks[2], double q, long ns, long nt, double smax, long ifail)

```
{
    // the number of asset intervals
    nt // the number of intervals
    double a,b,c,a1,b1,c1,opt_vals,rhs,s,work,u;
    double ds,time_step;
    long i;
    double t0,t1,t2,3mat=0.0;
    long n1,n2,n3;
    double sig[4],ds_plus,ds_minus,temp1,temp2;
    double D=0;

    n1 = floor((asset_price/smax)/ds);
    if (n1 < 0) {
        printf("increase the number of asset points %d\n", n1);
    }
    n2 = ns;
    ds = asset_price/n1;
    time_step = T/n2;
    n3 = n2+2 // number of nodes including grid line'
    // allocate the required arrays (all of size n3+1)
    s[0]=0;
    s[n1]=asset_price;
    for(i=0; i<n1; i++) {
        s[i+1]=(double)ds;
    }
    // sets sets below asset price /
    for(i=0; i<n2; i++) {
        s[i+1]=asset_price+(double)i;
    }

    // find the index corresponding to barrier level /
    barrier_index=0;
    while(barrier_level > s[barrier_index]) {
        barrier_index++;
    }
    if (barrier_level == s[barrier_index]) { // decrement barrier index /
        barrier_index--;
    }
    if (barrier_level < s[barrier_index]) // then barrier does not correspond
        to an existing line so create another one/
        for(i=0; i<n1-barrier_index; i++) {
            s[barrier_index+i+1]+=(double)ds;
        }
        barrier_index++;
        s[barrier_index]=barrier_level;
        if (n1-barrier) {
            n1++;
        }
    }
    // set the RHS and LS coefficients (time step j) a[j], b[j] and c[j] are the LS coefficients
    for the unknown option values (time step j)
    Note: a[j] and c[j] are used to form the vector rhs[j] of the tridiagonal system. /
    sig[0]=0;
time2=time_step/2;
t1=time_step/4 // theta (for theta method) */
    // assign elements of the (n1-2)*(n1-2) tridiagonal matrix */
    for(i=1; i<n1; i++) {
        ds_plus=ds;
        ds_minus=ds;
        D=(ds_plus+ds_minus);
        a[i]=temp1(r-0.5*q-sig[i]*sig[i])*temp1-ds_plus*s[i]*s[i-1]/sig[2);
        b[i]=time_step;
        c[i]=temp1(r-0.5*q-sig[i]*sig[i])*temp1+ds_minus*s[i]*s[i+1]/sig[2);
    }
    c[i]=-time_step*temp1(r-0.5*q-sig[i]*sig[i])*temp1*temp2;
    d[i]=min(ds_plus,ds_minus)/D;
    b[i]=1.8*time_step*temp1(r-0.5*q-sig[i]*sig[i])*temp1+sig[2]*s[i]*s[i+1]*temp2;
```

Code excerpt 5.19 to compute the value of a European down and out barrier option using a nonuniform grid.

The elements of the option but not out of L (they are stored in the array a).
The upper elements of the barrier elements are stored in the array a and the upper
diagonal elements of U are just zero.