# Vanilla Options and the Black–Scholes Model Section | 4.4 77

The same procedure can be used to compute the implied volatility of a European put; in which case we can replace c(S,E,t,σ) by p(S,E,t,σ), the value of a European put, and from equation (4.4.67), $V_c = \mathcal{V}_p$.

```
double implied_volatility(double value, double s, double x, double sigma[],
{
    // Input parameters:
    double value // the current price of the option
    double s0 //
    double s0 // the current price of the underlying asset
    double x // the strike price
    double sigma[2] // the input bounds on the volatility: sigma[0], the lower bound and, sigma[1], the upper bound
    double t // the maturity
    double r // the interest rate
    double q // the continuous dividend yield
    int put // if put is 0 then a call option, otherwise a put option
    // Output parameters:
    double sigma[] // sigma[0] contains the implied volatility
    int iflag; // an error indicator
    double zero=0;
    double err, vi, sig;
    double val,tol;
    double temp,vega,gaqrt,temp,val1;
    long max_iter, i, ind;
    double greek[5],c[20],sig,vega;
    long done;
    double eps = 0;
    eps=sqrt(EPS); // / a call option /
    if(put==1) {
        temp=MAX(0,x*exp(-r*t)-s*exp(-q*t),0); // / a put option /
    } else {
        temp=MAX(0,s*exp(-q*t)-x*exp(-r*t),0);
    }
    vi=abs(value-temp);
    if (vi<eps) // / the volatility is too small /
        iflag=3;
        return;
    }
    iflag=0;
    i=0;
    max_iter=500;
    sig=sigma[0]; // / initial iteration /
    val=temp; // / Newton iteration /
    while (abs(val-value)>tol && i<max_iter) {
        black_scholes(val,greek,0,x,t,r,q,put,iflag); // / compute the Black Scholes option value, val
        vega=greek[4]; // / and vega /
        sig=sig-(val-value)/vega; // / compute the new estimate of sigma using Newton's method /
        if (abs((sigma[0]-sig)/sig)<eps) // / check whether the specified accuracy has been reached /
            done=1;
        }
        sig=sig;
        i++;
    }
    sigma[0]=sig; // / return the estimate for sigma /
    return;
```

Code 4.3 Function to compute the implied volatility of European options.

If the implied volatility of American options is required, the procedure is exactly the same. However, instead of using the Black–Scholes formula to compute both the option value and vega, we use a binomial lattice to do this. The use of binomial lattices to obtain the option price and the Greeks is described in Chapter 5.

Below, in Code 4.4, is the simple test program which illustrates of the function implied_volatility; the results are presented in Table 4.3.