
```cpp
}
sum_opt_vals += total_probability_above * opt_val * disc;
else
    // don't use the Brownian Bridge
    sum_opt_vals += opt_val * disc;
}
double temp = sum_opt_vals / (double)fNumberScenarios;
return temp;
}
```

Code excerpt 4.8 (Continued).

# 5 Single asset American options

## 5.1 Introduction

In Chapter 4 we discussed single asset European options and the analytic formulae that can be used to price them. Here we will consider the valuation of single asset American-style options using numeric methods and analytic formulae; in addition we discuss the use of numerical techniques to value certain European options. The coverage in this chapter is as follows:

- Analytic approximation techniques for the valuation of American options
- Binomial lattice techniques used for the valuation of American and European options
- The valuation of American and European vanilla and barrier options using finite-difference grids
- The valuation of American options via Monte Carlo simulation.

It should be mentioned that although much of the discussion here concerns the valuation of vanilla European and American puts and calls, the techniques used can be modified without much difficulty to include more exotic options with customized payoffs and early exercise features.

## 5.2 Approximations for vanilla American options

### 5.2.1 American call options with cash dividends

In this section we will consider the valuation of vanilla American call options with cash dividends and discuss the methods of Roll, Geske, Whaley, and Black. We will first consider the Roll–Geske–Whaley method.

### The Roll–Geske–Whaley approximation

This method uses the work of Roll (1977), Geske (1979), and Whaley (1981). Let S be the current (t) price of an asset which pays a single cash dividend $D_1$ at time ex-dividend date, $t_1$, there will be a decrease in the asset's value from $S_{t_1}$ to $S_{t_1}-D_1$. The current asset price net of escrowed dividends is:

```
$S_D = S - D_1 \exp(-r(t_1 - t)) \quad (5.2.1)$
```

* Whaley

where r is the riskless interest rate.

Now consider an American call option, with strike price E and expiry time T, which is taken out on this asset. At $t_1$ there will be a ex-dividend asset price, $S^*$, over which the option will be exercised early. This value can be found by solving the following equation:

```
$$c(S^*, E, \tau_1) = S^* + D_1 - E \quad (5.2.2)$
```

where $c(S^*, E, \tau_1)$ is the Black-Scholes value of a European call option with strike price $E$ and maturity $\tau_1 = T - t_1$, on an asset with current value $S^*$ at time $t_1$. If prior to the ex-dividend date $S_t > S^*$ the American option will be exercised and realize a payoff of $S_{t_1} + D_1 - E$. On the other hand if $S_{t_1} \le S^*$ then the option is more exercised and will be held until option maturity at time T.

We can rewrite Eq. (5.2.2) as $S^*$ is the root of the following equation:

```
$K(S^*) = c(S^*, E, \tau_1) - S^* - D_1 + E = 0 \quad (5.2.3)$
```

where $K(S^*)$ denotes the function in the single variable $S^*$. A well-known technique for solving Eq. (5.2.3) is Newton's method, which we use in this case the:

```
$S_{i+1}^* = S_i^* - \frac{K(S_i^*)}{K'(S_i^*)} \quad (5.2.4)$
```

where $S_i^*$ is the $i^{th}$ approximation to $S^*$ and $S_{i+1}^*$ is the improved $(i+1)$th approximation. If we consider the case in Eq. (5.2.4) we have from Eq. (5.2.2) and (5.2.3) that

```
$K(S^*) = c(S^*, E, \tau_1) - S^* - D_1 + E$
```

and

```
$K'(S^*) = \frac{\partial K(S_i^*)}{\partial S_i^*} = \frac{\partial c(S_i^*, E, \tau_1)}{\partial S_i^*} - 1$
```

Also from Eq. (A.3.2) in Appendix A.3:

```
$\frac{\partial c(S_i^*, E, \tau_1)}{\partial S_i^*} = N_1(d_1(S_i^*))$
```

we note that the continuous dividend yield $q = 0$. So

```
$K'(S^*) = \frac{\partial K(S_i^*)}{\partial S_i^*} = N_1(d_1(S_i^*)) - 1$
```

```
$d_1 = \frac{\log(S_i^*/E) + (r + \sigma^2/2)\tau_1}{\sigma\sqrt{\tau_1}}$
```

Substituting these results into Eq. (5.2.4) gives:

```
$S_{i+1}^* = S_i^* - \frac{c(S^*, E, \tau_1) - (S^* + D_1)}{N_1(d_1(S^*)) - 1}$
```

Single asset American options On rearrangement this yields:

```
$S_{i+1}^* = \frac{c(S^*, E, \tau_1) + D_1 - E}{N_1(d_1(S^*)) - 1}$
```

for $i = 0, \dots, max$ (5.2.5) where a convenient initial approximation is to consider $S_0^* = E$, and $max$ is the maximum number of iterations to be used. We now use the Roll, Geske, and Whaley formula for the current value of an American call which pays a single dividend $D_1$ at time $t_1$; it is

```
$C(S, E, \tau) = S_D \left\{ N_1(b_1) + N_2(a_1, -b_1, \frac{t_1-t}{\tau}) + D_1 \exp(-r(t_1-t))N_1(b_2) - E \exp(-r\tau)N_1(b_2)\exp(r\tau) + N_2(a_2, -b_2, \frac{t_1-t}{\tau}) \right\}$ (5.2.6)
```

where $S_D$ is given by Eq. (5.2.1), $E$ is the exercise price, $T$ is the option expiry date, $t$ represents the current time, $\tau$ is the option maturity, $N_1(a)$ is univariate cumulative density function with upper integral limit $a$, and $N_2(a,b,\rho)$ is bivariate cumulative density function with upper integral limits $a$ and $b$ and correlation coefficient $\rho$. The other symbols in Eq. (5.2.6) are defined as

```
a_1 = \frac{\log(S/E) + (r + \sigma^2/2)\tau}{\sigma\sqrt{\tau}},\quad a_2 = a_1 - \sigma\sqrt{\tau}$
$b_2 = \frac{\log(S/S^*) + (r + \sigma^2/2)(t_1-t)}{\sigma\sqrt{\tau}},\quad b_2 = b_1 - \sigma\sqrt{t_1}$
```

and $S$ is the current (t) asset price, $S^*$ is found using Eq. (5.2.5), $r$ is the riskless interest rate, $\sigma$ is the asset's volatility, $\tau = T-t$ and $\tau_1 = T-t_1$. To compute the value of an American call pays $n$ cash dividends $D_i, i=1,...,n$, at times $t_i, i=1,...,n$, we can use the fact that optimal exercise occurs at the final ex-dividend date $t_n$; for example the American call but not $t_1$ should be set to $t_n$, $D_1$ should be set to $D_n$, and $S_D$ is given by

```
$S_D = S - \sum_{i=1}^n D_i \exp(-r(t_i-t))$ (5.2.7)
```

A program to compute the Roll-Geske-Whaley approximation for an American call option with multiple dividends is given in Code excerpt 5.1. Here the functions $cum\_norm$ and $cum\_norm2$ are used to calculate the values of $N_1(a)$ and $N_2(a,b,\rho)$, respectively. Code excerpt 5.3 was used to compute the values

```cpp
voidGM_approx(double *opt_value, double *critical_value, long n_divs, double dividends[],
    double Divs_T[],
{
    /* Input parameters:
    n_divs              = the number of dividends
    dividends[]         = dividends[0] contains the first dividend, dividend[1]
                        = the second etc.
    Divs_T[]            = the times at which dividends are paid: Divs_T[0] is the time at
                        Divs_T[1] is the time at which the second dividend is paid, etc.
    S0                  = the current value of the underlying asset
    X                   = the strike price
    sigma               = the volatility
    T                   = the time to maturity
    r                   = the interest rate
    Output parameters:
    opt_value           = the value of the option
    critical_value      = the critical value
    iflag               = an error indicator
*/
    double A1,A2,S_star,alpha1,alpha2,nt1,nt2;
    double b1,b2,di1,di2,sqrt,temp,temp1,temp2,temp3;
    double pdf,f,eur,var,fac,tol,loc_q,error=0;
    long iterate,flag=0;
    temp=0.0;
    for (i=0; i<n_divs; i++) { /* Check the Divs_T array */
        if (Divs_T[i] < 0 || Divs_T[i] > T) {
            flag=2;
            return;
        }
    }
    temp=Divs_T[i];
    /* calculate the present value of dividends (excluding the final one) */
    temp=0.0;
    for (i=0; i<n_divs-1; i++) {
        temp += dividends[i] * exp(-r*Divs_T[i]);
    }
    /* decrease the price by the present value of all dividends */
    div=dividends[n_divs-1];
    S=S*exp(-r*div);
    iterate=0;
    tol=0.000001;
    S_star=S;
    while (iterate) /* calculate the Black-Scholes value of a European call */
        d1=(log(S/X) + (r+sigma*sigma/2.0)*(T-t1))/(sigma*sqrt(T-t1));
        d2=d1-sigma*sqrt(T-t1));
        put=S*norm_n(d2)-X*exp(-r*(T-t1))*norm_n(d1);
        loc_q=0.0;
        S_star=S*(S*norm_n(d1)-X*exp(-r*(T-t1))*norm_n(d2)-1.0);
        error=fabs(S_star-S);
        if (error<tol) break;
        iterate++;
    }
    a1=(log(S/X) + (r+sigma*sigma/2.0)*T)/(sigma*sqrt(T));
    a2=a1-sigma*sqrt(T);
    b1=(log(S/X) + (r+sigma*sigma/2.0)*(T-t1))/(sigma*sqrt(t1));
    b2=b1-sigma*sqrt(t1);
    nt1=sqrt(t1);
    temp1=S*(num_n(b1)-num_n(a2)-nt1,nt1+iflag))*exp(-r*t1)*(X-div)*exp(-r*t1)*num_n(b2);
    opt_value=temp1+temp2;
    critical_value=S_star;
}
```

Code excerpt 5.1 Function to compute the Roll–Geske–Whaley approximation for the value of an American call option with discrete dividends.
