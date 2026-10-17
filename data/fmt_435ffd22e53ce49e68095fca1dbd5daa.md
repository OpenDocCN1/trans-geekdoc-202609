
| 1 || 101 || -9222.93, 5150.62, -2596.19, 7926.57, 796.74, -9259.86, 9335.39, 49.66, 995.76, -7415.86, 3726.71, -2141.33, 8777.05, 9190.49, 2325.45, 1087.92, 7541.71, -5877.16, -7493.36, 297.80, -9956.48, 8592.79, 429.41, -916.13, 7949.02, -7592.98, 8335.04, -1838.14, -5919.29, 1052.35, 7921.04, -9793.13, -8378.80, 5600.65, -9474.03, 4162.26, 5456.12, -8722.37, 1397.50, 7310.71, 7970.48, 1022.24, -4638.00, 3417.62, -3889.01, 8802.04, 6610.23, -7272.80, -4265.46, -861.19, 8771.91, 3169.98, 7778.50, 113.56, -1530.85, 8522.52, -2327.96, 5806.86, 2405.13, 7523.25, 3694.44, -8104.19, -4920.45, 5293.70, -8250.44, 2925.39, 1178.34, 1250.37, -7987.73, 8132.84, 8788.21, -9019.92, 6200.11, 8082.13, -4051.25, 4899.39, 1930.67, -8050.36, 8380.56, -6037.04, 9498.94, 3653.34, -5057.80, 9634.12, 6267.65, 2564.11, -4422.31, 6172.03, 6410.81, -9227.67, 9859.54, -8207.75, -7130.63, 8641.33, -9602.16, -2142.18, -3640.80, -9778.38, -699.24, 1744.13, 7179.45 || (768 bits) 155251809230070 893514897948846 250255525688601 71166966111350 947534894624925 52179522115341 344282218821823 32895145639727 898684564781135 911425012413524 710743706422593 331719098628765 602117654288074 972916187976263 849004251546271 9946096640 || 0.024466 || 0.0 || Yes |

Table 39.3 creates strong evidence that we can find the roots of polynomials with large constant values and of any degree or order. The root convergence happens till 201th degree polynomial successfully, means, encryption and decryption can be done more accurately. The key length will be more than 2048 bits which is far better than AES algorithm that uses three different key lengths (128, 192, and 256) with better memory utilizations. Figure 39.2 gives the memory requirement in bits details to satisfy the `f(`x`) = 0` test, where the degree of the polynomial varies from 3 to 201. It is clear from the Figure 39.2 that in spite of any degree of the polynomial (from 5 to 201 degree) the bit size required to store the root of the polynomial is always equal or less than the highest bit size of the coefficients given to that polynomial.

![Figure 39.2 Coefficient bits and accurate root bits relationship](img/fig39_2_C.jpg)

Figure 39.2 Coefficient bits and accurate root bits relationship

In the third experiment, all coefficient and constant values have been taken and processed with big number libraries ranging from 1 to 1024 bits. After generating a complete polynomial, Newton Raphson method is applied to compute a root. The accurate root evaluation takes place till 115 degrees, afterward the polynomial gets the erroneous root. A few tested polynomials are shown in Table 39.4.

Table 39.4 Polynomial root convergence with big numbers

| S No. || Degree of the polynomials || Coefficients of the polynomial || Constant value of the polynomial || Computed root using Newton Raphson method || Execution time in seconds || Evaluation of f(x) || Correct root convergence |

| --- | --- | --- | --- | --- | --- | --- | --- |

| 1 | 5 | 0916300184138066757562815 1274558987543914186376514 7998673615361504290674869 8717602105885168810562381 4454551067090137938783862 9769753620687025815234540- 4216093347228007006208.00, 17983595033397191.00, 6277 101735386680763835789422 573841115988241025190659 619855.00, 296427748447529 460284341721622241042320 311544861589992618201176 91321738785193983.00, -777 067556890291628367784762 650943790964629226073041 363510207617725815102178 4938315775.0 || (512 bits) 1340780792 9942597099 5740249982 0584612747 9365820592 3933777064 7354743439 6749414386 8031525178 8125008179 151117863 602690971 799117612 500691037 136586458- 1485296655 || -0.000212536 758617217807 406315922236 266137446075 543053711681 703085739374 459979809462 420197802394 383281194976 770016074010 785888985685 502209833233 181368797535 017642808031 461229341982 301949537699 319226852374 073717829963 899235345138 442458418981 556234229916 448501887787 429096708830 768954129214 649392777980- 775334237772 || 0.016592 || 0.0 || Yes |

| --- | --- | --- | --- | --- | --- | --- | --- |

In `Table 39.4`^[1], the entries of 5th degree and 15th degree have shown even though it is compatible with the 115-degree polynomial. It is additionally seen that the most elevated coefficient and constant length is 1024 bit, therefore to store a precise root, 1024-bit length is required for the root and the accuracy of the root is not depending upon the degree of a polynomial.

Moreover, it has been seen that the root computation is exceptionally fast using big number libraries. The time of root computation is given in `Table 39.2`^[2], `Table 39.3`^[3] and `Table 39.4`^[4]. As the degree of the polynomial expanded the time of computation is increased but still it is milliseconds (ms) range only. This implementation uses all big numbers still it suffers after 115th degree polynomial as compared to previous one that works well for 201st degree polynomials because it takes big values as co-efficient values.

Figure 39.3 depicts the temporal complexity graph for the codes of experiments 1, 2, and 3. The graph makes it obvious that primitive data types cannot converge after the polynomial’s 15th degree. Additionally, by employing big numbers, we are able to converge up to a degree of 151, and the convergence time is recorded in milliseconds, demonstrating the speed of root convergence.

![Figure 39.3 Graph of time complexities of root convergence experiments using primitive and big number data types](img/fig39_3_C.jpg)

Figure 39.3 Graph of time complexities of root convergence experiments using primitive and big number data types

## Conclusion

In this article, the implementation of the big number polynomial root finding algorithm using the Newton Raphson method has been done. Experiments have been carried out in which the polynomial is generated using large random constant and large coefficient values. Newton Raphson method is applied to find the first possible root. The simulation is done from the range 1 to 1024 bits for the constant value keeping the order of the polynomial from 2 to 201 degrees. The evaluated root is validated multiple times, and 100% accuracy is achieved. The calculated root value with its highest possible precision levels matches the same length of the given constant value. This work gives solid proof of the correct convergence to a root value of any given random higher order polynomial in a big number domain that opens a gateway to a new generation of cryptographic algorithms to work in the floating-point domain. The need for post quantum cryptography can be very well satisfied by this kind of dynamic algorithm.

## References

* How to store a very large number of more than 100 digits in C. Accessed 25 March 2023.
* Adomian, G. and Rach, R. (1985). On the solution of algebraic equations by the decomposition method. J. Math. Anal. Appl., 105(1), 141–166.
* Akram, S. and Ul Ann, Q. (2015). Newton Raphson method. Int. J. Sci. Engg. Res., 6(7), 1748–1752.
* Ben-Israel, A. (1966). A Newton-Raphson method for the solution of systems of equations. J. Math. Anal. Appl., 15(2), 243–252.
* Chun, C. (2006). A new iterative method for solving nonlinear equations. Appl. Math. Comput., 178(2), 415–422.
* Chun, C. and Neta, B. (2017). Comparative study of eighth-order methods for finding simple roots of nonlinear equations. Num. Algorith., 74, 1169–1201.
* Cordero, A. and Torregrosa, J. R. (2007). Variants of Newton’s method using fifth-order quadrature formulas. Appl. Math. Comput. 190(1), 686–698.
* Singh, J. and Singh, K. (2009). Statistically analyzing the impact of automated ETL testing on the data quality of a datawarehouse. Int. J. Comp. Elec. Engg., 1(4), 488.
* Darvishi, M. T. and Barati, A. (2007a). A fourth-order method from quadrature formulae to solve systems of nonlinear equations. Appl. Math. Comput., 188(1), 257–261.
