
PSO searches for a low-cost hardware architecture design solution for DSP cores iteratively. In each iteration, it explores an equal or better solution in terms of design cost. However, this iterative searching process terminates on the basis of the following two conditions: (i) the number of iteration exceeds the maximum count (`I[max]`); (ii) the global best remains unchanged for the maximum consecutive iteration count (`δ`). In Sengupta *et al.* ([2017b](#Chapter3.html#c03_bib27)), the used value of `I[max]` and `δ` during the experimental setup is 100 and 10, respectively.

##### 3.6.3.2 Vendor allocation procedure

As mentioned earlier, scheduling and hardware allocation are performed for the DMR CDFG on the basis of resource configuration and vendor allocation mode. For example for the DMR of the FIR filter, the hardware resources required to schedule are the adder, multiplier and comparator (shown in [Figure 3.24](#Chapter3.html#c03_fig24)) . Now to implement distinctness during hardware allocation, the same 3PIP cores (adders, multipliers and comparators) are imported from two different vendors. Let us assume the two different vendors are V1 and V2; the multiplier and adder imported from V1 have area = 2468 au and 2034 au, latency = 10,000 ns and 265 ns, respectively; while the multiplier and adder imported from V2 have area = 2464 au and 2032 au, latency = 11,000 ns and 270 ns, respectively (*Note*: the values are used based on 90 nm technology scale; assuming 1 au = 1 transistor; ns = nanosecond).

Now consider the Trojan secured DMR CDFG of the FIR that is designed on the basis of the candidate solution `X[i] = 2(+), 2(*), 1(<), U = 2, M[v] = 00` (illustrated in [Figure 3.25(a)](#Chapter3.html#c03_fig25a)). This indicates that the DMR CDFG of the FIR filter is unrolled two times, scheduled based on two adders, two multipliers, and one comparator, and vendor hardware allocation is performed using mode ‘00’. The corresponding execution delay and area of the design is: `T[E]^(DMR) = 45,080 ns` and `A[T]^(DMR) = 13,064 au`. As shown in [Figure 3.25(a),](#Chapter3.html#c03_fig25a) based on the vendor allocation rule in mode 00 (all modes are explained in Section 3.4.1.2), operations of `U^(OG)` are allocated to the vendor in an alternative way in a control step (CS). For example, opn.1 and opn.3 of `U^(OG)` are allocated alternatively to hardware of V1 and V2 in control step 1. Further, opn.1′ and opn.3′ of `U^(DP)` are allocated to hardware of V2 and V1, respectively.

![image](OEBPS/images/PBCS0600-03-f25a.jpg)

Figure 3.25(a) Scheduling and binding of the FIR for Xi = 2(+), 2(\*), 2(<), U = 2, I = 4 based on vendor allocation mode `M[v] = 00`; `T[E]^(DMR) = 45,080 ns` and `A[T]^(DMR) = 13,064 au`

If the same DMR CDFG of the FIR filter is designed based on the candidate solution `X[i] = 2(+), 2(*), 1(<), U = 2, M[v] = 01` (illustrated in [Figure 3.25(b)](#Chapter3.html#c03_fig25b)), the corresponding execution delay and area of the design are `T[E]^(DMR) = 43,080 ns` and `A[T]^(DMR) = 17,996 au`. As shown in [Figure 3.25(b),](#Chapter3.html#c03_fig25b) based on the vendor allocation rule in mode 01, all operations of `U^(OG)` are allocated to the hardware of V1 and all operations of `U^(DP)` are allocated to the hardware of V2.

If the same DMR CDFG of the FIR filter is designed based on candidate solution `X[i] = 2(+), 2(*), 1(<), U = 2, M[v] = 10` (illustrated in [Figure 3.25(c)](#Chapter3.html#c03_fig25c)), the corresponding execution delay and area of the design is: `T[E]^(DMR) = ’45,080 ns` and `A[T]^(DMR) = ’13,064 au`. As shown in [Figure 3.25(c)](#Chapter3.html#c03_fig25c) based on vendor allocation rule in mode 10, all the critical path operations, that is, opn.1, opn.2, and opn.4 of `U^(OG)` (marked in a dotted circle) are allocated to the hardware of V1 and all non-critical path operations, that is, opn.3, opn.5, and opn.6 of `U^(OG)` are allocated to the hardware of V2. The hardware of the distinct vendor is allocated in `U^(DP)`.

![image](OEBPS/images/PBCS0600-03-f25b.jpg)

Figure 3.25(b) Scheduling and binding of the FIR for Xi = 2(+), 2(\*), 2(<), U = 2, I = 4 based on vendor allocation mode `A[v] = 00`; `T[E]^(DMR) = 45,080 ns` and `A[T]^(DMR) = 17,996 au`

![image](OEBPS/images/PBCS0600-03-f25c.jpg)

Figure 3.25(c) Scheduling and binding of the FIR for Xi = 2(+), 2(\*), 2(<), U = 2, I = 4 based on vendor allocation mode `A[v] = 00`; `T[E]^(DMR) = 45,080 ns` and `A[T]^(DMR) = 13,064 au` and opn.4 of `U^(OG)` are allocated to the hardware of V2

If the same DMR CDFG of the FIR filter is designed based on candidate solution `X[i] = 2(+), 2(*), 1(<), U = 2, M[v] = 11` (illustrated in [Figure 3.25(d)](#Chapter3.html#c03_fig25d)), the corresponding execution delay and area of the design are `T[E]^(DMR) = 45,070 ns` and `A[T]^(DMR) = 15,096 au`. As shown in [Figure 3.25(d)](#Chapter3.html#c03_fig25d) based on vendor allocation rule in mode 11, alternate vendor allocation is performed to the operations belonging to subsequent unrolled loop iterations, for example all operations of the first unrolled loop, that is, opn.1, opn.2, opn.5, and opn.6 of `U^(OG)` are allocated to the hardware of V1 and all operations of the second unrolled loop, that is, opn.3, and opn.4 of `U^(OG)` are allocated to the hardware of V2. Hardware of the distinct vendor is allocated in `U^(DP)`.

![image](OEBPS/images/PBCS0600-03-f25d.jpg)

Figure 3.25(d) Scheduling and binding of the FIR for Xi = 2(+), 2(\*), 2(<), U = 2, I = 4 based on vendor allocation mode `A[v] = 10`; `T[E]^(DMR) = 45,070 ns` and `A[T]^(DMR) = 15,096 au`. Hardware of distinct vendor is allocated in `U^(DP)`

### 3.7 Analysis of case studies/test cases

In this section, we analyze and compare four different Trojan security approaches for DSP cores that are available in the literature in terms of their security and design cost. This section is divided into four sub-sections: (i) DSP core applications and system setup, (ii) security analysis of Sengupta *et al.* ([2017b](#Chapter3.html#c03_bib27)), (iii) design cost analysis of Sengupta *et al.* ([2017a](#Chapter3.html#c03_bib26)), Rajendran *et al.* ([2013](#Chapter3.html#c03_bib17)) and Sengupta *et al.* ([2017c](#Chapter3.html#c03_bib28)) (iv) comparative study among them.

#### 3.7.1 DSP applications and system setup for the case studies

Results of approaches HLS-ST ([Rajendran *et al.*, 2013](#Chapter3.html#c03_bib17)), LC-HLS ([Sengupta *et al.*, 2017a](#Chapter3.html#c03_bib26)), TL-HLS ([Sengupta *et al.*, 2017b](#Chapter3.html#c03_bib27)) and NL-TS ([Sengupta *et al.*, 2017c](#Chapter3.html#c03_bib28)) reported in the literature were based on the implementation carried out in Java 8 and executed on Windows platform with Intel Core i53210M CPU, 4GB DDR3 primary memory, and processor frequency of 3.20 GHz. The design parameters were evaluated with respect to 90 nm CMOS-based technology node. The design cost of Trojan secured DSP core is calculated based on ([3.5)](#Chapter3.html#c03_eqn5) where `w[1]` and `w[2]\= 0.5`. The design area is calculated based on ([3.1)](#Chapter3.html#c03_eqn1), design latency for single-loop CDFG is calculated based on Eqn. 3.3 and nested-loop CDFG and non-loop CDFG is calculated based on Eqn. 3.4. During the PSO-DSE approach, each design solution is run 15 times to obtain low-cost design solution. Further, the optimal PSO control parameters are set as follows: `ω` = linearly decreasing between 0.9 and 0.1; `b1` and `b2` =2; `r1` and `r2` = 1; terminating criterion `I[max]` = 100 and `δ` = 10 ([Sengupta *et al.*, 2017b](#Chapter3.html#c03_bib27)). (*Note*: all the variables are defined in Section 3.6.3).

#### 3.7.2 Security analysis
