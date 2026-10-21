Also, in each interval of time, the maturity characteristics of each bond outstanding in the firm’s bond portfolio can be determined as follows. Let the maturity of a bond j in the interval i be m_{j,i}. Bond j is issued in the interval (j - N0) = k. Since M_k is the maturity of the bond issued in the interval k, we can write

m_{j,i}=M_k-(i-k)  for all j > N0,
= m_{j,0} - i  for all j < N0,

where m_{j,0} is the maturity of the bond j outstanding at t = t0.

The funds available through all the outstanding bonds in the interval i are
V \sum_{j=1}^{N'} X_{j,i}  (49.2)

where V is the face value of one bond.

The total funds available from long-term sources of bonds and equity at any time interval i are defined as B_i. Then,
B_i = \sum_{k=0}^{i} Y_{1,k} + \sum_{k=0}^{i} Y_{3,k} + V \sum_{j=1}^{N'} X_{j,i}  (49.3)

Let us define the cumulative requirements, D_i, in interval i as follows:
D_i = \sum_{k=1}^{i} R_k  (49.4)

where R = [R1,R2,R3,...,RN]' is the vector of funding requirements over the N period planning horizon.

# 49.3.1 The costs of funds

(1) Floatation Costs. If g_i and g_c are the variable and the fixed floatation costs, respectively, the total equity floatation cost G_i is
G_i = (g_c + g_i Y_{1,i})\sigma_i,  where \sigma_i = 1 if Y_{1,i} > 0,  (49.5)
= 0 otherwise.

The bond floatation cost in general is lower than the equity floatation cost. Let α and β be the fixed and the variable floatation costs for bonds, respectively. Then the total bond floatation cost F_i in any given time interval is
F_i = [α + β(X_{N0+i,i})]δ_i,  where δ_i = 1 if X_{N0+i,i} > 0  (49.6)
= 0 otherwise.