# 98 CHAPTER 5 Single Asset American Options

dividends[] - the dividends[] contains the first dividend, dividend[i] the second sec.
Div_T[] - the times at which the dividends are paid. Div_T[i] is the time at which the first dividend is paid.
DivT is the time at which the underlying asset is paid,

+   50
X
sigma
R
put
the strike price
the volatility
the time to maturity
the interest rate
if put is not zero then a call option, otherwise a put option

Output parameters:
value - the value of the option, iflag an error indicator
double zero;
double beta,temp,temp1,temp2,temp3;
double tn_val,val_to,loc,q_err;
long i14;

```
loc_q = 0;
for (i=0; i < n_divs; i++) {
    if (Div_T[i] < zero) printf("Error in Div array element is greater than %f\n", Div_T[i]);
    else printf("Error in Div array element is zero\n");
}
divends[i] = Div;
```

```
// calculate the value of the dividends /\nfac = 0;
for (i=0; i < n_divs; i++) {
    fac += dividends[i] * exp(-Div_T[i]);
}
```

```
temp = 50;
// calculate the value of the option on expiry /\nblack_scholes_deal(W,TULL,NULL,X,sigma,r,loc,q,put,&value);
// calculate the value of the option on the last dividend date /\ntemp = Div_T[n_divs-1];
temp += dividends[n_divs-1] * exp(-r*temp);
black_scholes_deal(W,TULL,NULL,X,sigma,r,loc,q,put,&value);
value = Max(value,val);
```

Code excerpt 5.2. (continued).

Code excerpt 5.3 shows how the values are as Whaley (1981) and compares the result with Black, Geske, and Whaley approximation with that of Black; results are presented in Table 5.1.

double q,r,temp,loc,r;
long i1,i2,n_divs;
double delta,vega,ad_value,ad_value_put;
long is_american,ifail,put;
double bin_hs[5],greeks[5],bin_bs_value;
double double_value,critical_value,E1,E2, crit1,crit2;
double black_value;
double Div_T[i],dividends[i];
long n_div,put;

```
E = 100.0;
sigma = 0.92;
temp = 2.0;
t = 1.6;
put = 0;
// checking the parameters as in Whaley (1981) /
nDiv_T[0] = 5.0;
dividends[0] = 5.0;
n_div = 5;
printf("Price %f RGW Black %f\n", price, black);
for (i=0; i < n_div; i++) {
    put = 0;
    if (black == 0.0) {
        RGW_approx(option_value,critical_value,n_divs,Div_T,T_50,E,sigma,r,&ifail);
        printf("%.4f, critical_value\n", critical_value);
        if (put == 0) printf("%.4f, %f\n", value, value);
    }
    black_approx(&black_value,n.divss,Div_T,T_59,E,sigma,r,put,&value);
}
```

Code excerpt 5.3 Simple test to compare the calculation of results using RGW_approx with function opt_black_approx, and the parameters used are the same as in Whaley (1981).

*