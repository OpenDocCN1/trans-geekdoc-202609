![](bbox=[0.13, 0.09, 0.86, 0.49])

Figure 84.23: Excel file binomial tree model.xlsm.

Binomial Tree Model.xlsm after the file is opened. Pushing the button shown in Figure 84.23 will result in the dialog box shown in Figure 84.24.

The dialog box shown in Figure 84.24 shows the parameters for the Binomial OPM. These parameters are changeable. The dialog box shows the default values.

Pushing the calculate button will produce the European call, European put, American call, and American put option values.

# 84.8 Black–Scholes Option Pricing Model

The most popular OPM is the Black–Scholes OPM. In this section, we will demonstrate the usage of the Black–Scholes OPM. In later sections, we will demonstrate the relationship between the Binomial OPM and the Black–Scholes pricing model. The Black–Scholes model prices the European call and put options. The Black–Scholes model for a the European call option is

$C = S N(d1) - X e^{-rT} N(d2), \quad (84.10)$