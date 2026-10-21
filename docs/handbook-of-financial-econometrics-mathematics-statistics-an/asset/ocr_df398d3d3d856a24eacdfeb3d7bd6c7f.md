```
set jess.pred;
if _FREQ_ = 0;
run;

data jess.count1_1;
set jess.out_sample;
if phat >=0.021 and bptstatus = 1;
run;

data jess.count1_2;
set jess.out_sample;
if bptstatus = 1;
run;

data jess.count2_1;
set jess.out_sample;
if phat < 0.021 and bptstatus = 0;
run;

data jess.count2_2;
set jess.out_sample;
if bptstatus = 0;
run;
```

# Appendix 126C Application of Merton Distance to Default Model

Following Bharath and Shumway (2008), we will discuss how V and σ_V can be numerically estimated. The Merton DD model estimates the market value of debt by applying the classic Merton (1974) bond pricing model. The Merton model makes two particularly important assumptions. The first is that the total value of a firm follows geometric Brownian motion,

$dV = \mu V dt + \sigma_V V dW,$
(126C.1)

where V is the total value of the firm, μ is the expected continuously compounded return on V, σ_V is the volatility of firm value and dW is a standard Wiener process. The second critical assumption of the Merton model is that the firm has issued just one discount bond maturing in T periods. Under these assumptions, the equity of the firm is a call option on the underlying value of the firm with a strike price equal to the face value of the firm’s debt and a time-to-maturity of T. Moreover, the value of equity as a function of the total value of the firm can be described by the Black-Scholes-Merton formula. By put-call parity, the value of the firm’s debt is equal to the value of a risk-free discount bond minus the value of a put option written on the