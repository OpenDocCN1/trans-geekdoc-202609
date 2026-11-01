
Since, we require the extent to which the filter can predict huge data over a period of time, it is important to define the expected value of the error function:

| ![](Images/9789815124842-C2-EQ6.jpg) || (6) |
| --- | --- |

where,

`LF`: Loss function

`E` [`f` (`e[k]`)] : Expected error

The results in the Mean Squared Error (`MSE`) function are defined as:

| ![](Images/9789815124842-C2-EQ7.jpg) || (7) |
| --- | --- |

The estimations of `x[k]` are done in a manner so as to minimise the loss function `LF`.

### KALMAN FILTER EQUATIONS

We first write down the state equations for any process under consideration:

| ![](Images/9789815124842-C2-EQ8.jpg) || (8) |
| --- | --- |

where,

`x[k:]` is the state Vector representing the process at time k and has dimensions (`nx1`).

`phi`: is the state transition matrix of the process from state k to the consecutive state `k+1`.

This state is assumed to be stationary w.r.t time and has the dimensions (`nxm`).

`w[k]`: is the white noise associated with the process, with a known value of covariance.

The observations on this variable can be modelled by the equation:

| ![](Images/9789815124842-C2-EQ9.jpg) || (9) |
| --- | --- |

`z[k]`: is the actual measurement of x at time k with dimensions (`mx1`).

`H`: is the connection between the state and the measurement vector without noise, stationary with respect to time and has dimensions (`mxn`).

`v[k]`: is the measurement error associated with the process and we consider it to be white noise with no cross-correlation with the process noise. And has dimensions (`mx1`).

The two noise models have covariances assumed stationary with respect to time and are given by:

| ![](Images/9789815124842-C2-EQ10.jpg) || (10) |
| --- | --- |

| ![](Images/9789815124842-C2-EQ11.jpg) || (11) |
| --- | --- |

The mean squared error (`MSE`) function is given by:

| ![](Images/9789815124842-C2-EQ12.jpg) || (12) |
| --- | --- |

This is equivalent to:

| ![](Images/9789815124842-C2-EQ13.jpg) || (13) |
| --- | --- |

`P[k]` : Error covariance matrix⁴ at time k.

Expansion of (2.13) gives:

| ![](Images/9789815124842-C2-EQ14.jpg) || (14) |
| --- | --- |

Let ![](Images/9789815124842-C2-EE1.jpg)be the priori estimate of ![](Images/9789815124842-C2-EE2.jpg), which can be known by knowing the system considered. We can write an updated equation for the new estimate, combining the old estimate with the measurement data. Therefore,

| ![](Images/9789815124842-C2-EQ15.jpg) || (15) |
| --- | --- |

`K[k]` : is the Kalman Gain.

`z[k]` – `H` `x^[k]`: is known as innovation or measurement residual.

For the current estimate, we have from equation (15):

| ![](Images/9789815124842-C2-EQ16.jpg) || (16) |
| --- | --- |

Substituting equation (9) in equation (15), we have:

| ![](Images/9789815124842-C2-EQ17.jpg) || (17) |
| --- | --- |

Substituting equation (2.29) in equation (2.14), we get:

| ![](Images/9789815124842-C2-EQ18.jpg) || (18) |
| --- | --- |

The error in the prior estimate is (`x^*[k]` – `x^*[k]‘*`), which is clearly not correlated with the measurement noise so the expectation may be written as:

| ![](Images/9789815124842-C2-EQ19.jpg) || (19) |
| --- | --- |

Substituting equation (2.11) and equation (2.14) in equation (2.19):

| ![](Images/9789815124842-C2-EQ20.jpg) || (20) |
| --- | --- |

here, `P[k]`^’ is the prior estimate of `P[k]`.

Equation (2.20) is the error covariance update equation. The mean squared error is contained in the diagonal of this covariance, as shown below:

| ![](Images/9789815124842-C2-EQ21.jpg) || (21) |
| --- | --- |

Trace of a matrix is defined as the sum of its diagonal elements. So, the trace of the above matrix `P[kk]` must be minimized for the Mean squared error to be minimum.

We first take the derivative of the trace of the matrix `P[kk]` with respect to `K[k]`. and then the output is put equal to zero to get the minima. Expanding (2.20) gives:

| ![](Images/9789815124842-C2-EQ22.jpg) || (22) |
| --- | --- |

Since the trace of the matrix is equal to the trace of its transpose, thus:

| ![](Images/9789815124842-C2-EQ23.jpg) || (23) |
| --- | --- |

where `T[M]` represents the trace of the matrix M.

As, `P[k]’` = (`P[k] ‘) ^T`, being a symmetric matrix, and

(`K[k]HP[k]’`) ^T = `P[k]’ ^T H^T K[k]^T` = `P*[k]’H^T K[k]^T`

Therefore,

| ![](Images/9789815124842-C2-EQ24.jpg) || (24) |
| --- | --- |

Differentiating with respect to `K[k]`

| ![](Images/9789815124842-C2-EQ25.jpg) || (25) |
| --- | --- |

Being a minimum value, setting it to zero and then rearranging the terms, we have:

| ![](Images/9789815124842-C2-EQ26.jpg) || (26) |
| --- | --- |

Solving for `K[k]`:

| ![](Images/9789815124842-C2-EQ27.jpg) || (27) |
| --- | --- |

This is the equation for Kalman Gain.

The measurement prediction covariance associated with it is given by:

| ![](Images/9789815124842-C2-EQ28.jpg) || (28) |
| --- | --- |

Substituting equation (27) in equation (22), we have:

| ![](Images/9789815124842-C2-EQ28A.jpg) |
| --- |

So, we have:

| ![](Images/9789815124842-C2-EQ29.jpg) || (29) |
| --- | --- |

Hence, we obtain the equation for Error Covariance Matrix with optimal gain.

Equation (15), equation (27) and equation (29) develop an estimate of the state variable `x[k]`.

The following equation gives the State projection:

| ![](Images/9789815124842-C2-EQ30.jpg) || (30) |
| --- | --- |

We need an equation which should project the error covariance matrix to the next time interval, `k+1` in order to complete the recursion. For this, we first write an expression for the prior estimate,

| ![](Images/9789815124842-C2-EQ31.jpg) || (31) |
| --- | --- |

Now we extend the equation (2.14) to time `k + 1`:

| ![](Images/9789815124842-C2-EQ32.jpg) || (32) |
| --- | --- |

Since the noise `w[k]` exists between k and k+1, `e[k]` and `w[k]` have zero cross-correlation, whereas the error `e[k]` corresponds to the error at time k.

Therefore,

| ![](Images/9789815124842-C2-EQ32A.jpg) |
| --- |

This completes the Recursive Filter.

Summarising the primary equations for the Kalman Filter process

The **State** equations:

| ![](Images/9789815124842-C2-EQ33.jpg) || (33) |
| --- | --- |

| ![](Images/9789815124842-C2-EQ34.jpg) || (34) |
| --- | --- |

| ![](Images/9789815124842-C2-EQ35.jpg) || (35) |
| --- | --- |

The Measurement Input equation:

| ![](Images/9789815124842-C2-EQ36.jpg) || (36) |
| --- | --- |

The Kalman Gain equation:

| ![](Images/9789815124842-C2-EQ37.jpg) || (37) |
| --- | --- |

The State Matrix Update equation:

| ![](Images/9789815124842-C2-EQ38.jpg) || (38) |
| --- | --- |

The Process Covariance Matrix Update equation:

| ![](Images/9789815124842-C2-EQ39.jpg) || (39) |
| --- | --- |

From the above equations, the matrices `H` and `C` are used for converting another matrix to a suitable dimension. Matrix, `I` represent the Identity Matrix.

### GENERAL APPLICATIONS OF KALMAN FILTER

There are numerous applications of Kalman Filters. Stating a few of them here:

1. Global Positioning System (G.P.S.) receivers.
2. Tracking a Plane using suitable radars.
3. Weather forecasting over an area.
4. Advanced Driver Assistance Systems (A.D.A.S.).
5. Virtual Reality, for predictive steps.
6. Image processing in a computer.

### KALMAN FILTER EQUATIONS IN ONE DIMENSION

To have a clear perspective of Kalman filter, we analysed it in one-dimension. The equations considered previously are generalised for N dimensional case. The special case where the dimension reduces to just one, the equations are tweaked a little.

Abbreviations used in the equations are:

`K`: Kalman Gain.

`EST[k]`: Current Estimated Value.

`EST[k][-1]`: Previous Estimated Value.

`E[EST]`: Error in the Estimated Value.

`MEA`: Measurement input value at time `k`.

`E[MEA]`: Error in the Measurement input value at time `k`.

Using these, the equations for one dimension case are given by:

The Kalman Gain equation:

| ![](Images/9789815124842-C2-EQ40.jpg) || (40) |
