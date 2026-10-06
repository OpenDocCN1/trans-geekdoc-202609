
## 204 CHAPTER | 7 Other Financial Derivatives

## Simply Compounded Spot Rate

When simple compounding is $\Delta(t,T) = L(t,T)(T-t)$, where $L(t,T)$ is the simply compounded spot rate between time $t$ and $T$.

$$
DF(t,T) = \{1 + L(t,T)(T-t)\} = 1
$$

and so the simply compounded rate

$$
$$L(t,T) = \frac{1}{T-t} \left\{ \frac{1}{DF(t,T)} - 1 \right\} \quad (7.2.4)
$$

## 7.2.1 Forward Rate Agreement

A forward rate agreement (FRA) is a contract between two counterparties (referred here as $A$ and $B$), in which one counterparty (say $A$) agrees to pay interest at the (variable) spot rate, while the other agrees to pay a fixed interest. The rate agreement starts at time $T_s$ and end at the maturity $T_m$, at which the counterparties settle the amount that is owed. If $P$ is the principal, then at time $T_m$, the contract has the following value to A:

$$
V(T_m) = P \{(T_m-T_s)K - L(T_s,T_m)(T_m-T_s)\} \quad (7.2.5)
$$

where $K$ is the agreed fixed rate, and $L(T_s,T_m)$ is the simply compounded rate between times $T_s$ and $T_m$. From equation (7.2.4), we have

$$
L(T_s,T_m) = \frac{1}{T_m-T_s} \left\{ \frac{1}{DF(T_s,T_m)} - 1 \right\}
$$

so

$$
V(T_m) = P \{(T_m-T_s)K - \frac{T_m-T_s}{DF(T_s,T_m)}\}\quad (7.2.6)
$$

The value of the FRA to A at time $t \le T_m$ is therefore $FRA(t,T_m) = DF(t,T_m)V(T_m)$ which means

$$
FRA(t,T_m) = DF(t,T_m)P \left{(T_m-T_s)K - \frac{T_m-T_s}{DF(T_s,T_m)}\right\} \quad (7.2.7)
$$

Using $DF(t,T) = DF(t,T_m)DF(T_m,T)$, we can rewrite equation (7.2.7) as

$$
FRA(t,T) = DF(t,T)P \left{(T_m-T_s)K - \frac{T_m-T_s}{DF(T_s,T_m)}\right\} \quad (7.2.8)
$$

The value of $K$ which sets $FRA(t)$ to zero is the time $t$ forward rate between times $T_s$ and $T_m$, and it is denoted by $F(t,T_s,T_m)$. From equation (7.2.8),

$$
F(t,T_s,T_m) = \frac{1}{T_m-T_s} \left\{ \frac{DF(t,T_s)}{DF(t,T_m)} - 1 \right\} \quad (7.2.9)
$$

Combining equation (7.2.8) and equation (7.2.10), we can express the value of the FRA as

$$
FRA(t) = DF(t,T_m)P \tau K - F(t,T_s,T_m)\} \quad (7.2.10)
$$

where $\tau = T_m - T_s$ is known as the tenor of the FRA, and $T_s$ is the reset time for forward rate $F(t,T_s,T_s+\tau)$.

## 7.2.2 Interest Swap

Interest swaps (IRS's) are very common financial instruments - it is unusual for 80% of the trades in a portfolio to be IRS. Here, we will provide a description of some of the characteristics of IRS's, more detail can be found in Hull (2003).

A vanilla IRS consists of a strip of FRA trades, each FRA starting when the previous FRA finishes. The maturity date of the IRS thus corresponds to the maturity date of the FRA.

Let the times of the FRAs be $t_{i,i} = 0, \dots, n-1$, and the maturity times of the FRAs be $t_{i,i} = 1, \dots, n$; note that the FRA start time corresponds to the forward rate reset times, and the maturity times correspond to the FRA payment times. We will now adopt the (common) convention of calling the FRA trades swaplets, so an IRS is made up of number of swaplets.

When the counterparty pays the fixed rate and receives the floating rate, (from A perspective) is termed a payer IRS. Alternatively, if A receives the fixed rate and pays the floating rate, then is termed a receiver IRS.

The value of an IRS at $t$, $t_{k-1} < t < t_{k}$, will now be considered. We will assume that discount factors used to count the forward rates and those to discount the coupon payments are associated with the same yield curve. Using (7.2.10), we have

$$
IRS(t) = C DF(t,t_{k}) + \sum_{i=k+1}^{n} DF(t,t_{i})\tau_{i} \{K - F(t,t_{i-1},t_{i-1}+\tau_{i})\} \quad (7.2.11)
$$

where $C$ is the next coupon payment after time $t$ (this occurs at $t_{k}$) and $\tau_{i}$ is the tenor of the $i^{th}$ swaplet which starts at time $t_{i-1}$ and ends at time $t_{i}$. Note that the next coupon payment for the swaplet starting at time $t_{k-1}$ and maturing at $t_{k}$ is already known at $t$ because the forward rate $F(t,t_{k-1},t_{k})$ was reset in the past $t_{k-1} < t$. We will now write (7.2.11)

$$
IRS(t) = C DF(t,t_{k}) + FXD(t) - FLT(t) \quad (7.2.12)
$$

where $FXD(t)$, the time value of the fixed leg,

$$
FXD(t) = P \sum_{i=k+1}^{n} DF(t,t_{i})\tau_{i} \quad (7.2.13)
$$

and $FLT(t)$, the time value of the floating leg,

$$
FLT(t) = P \sum_{i=k+1}^{n} DF(t,t_{i})\tau_{i} F(t,t_{i-1},t_{i-1}+\tau_{i}) \quad (7.2.14)
$$

## The Floating Leg

We will now evaluate equation (7.2.14). The floating leg payment at $t_{i}$ will be denoted by $C_{i}$ and has value

$$
C_{i} = P F(t,t_{i-1},t_{i-1}+\tau_{i}) \tau_{i}
$$

where

$$
F(t_i, t_{i-1}, t_{i-1}+\tau_{i}) = \left\{ \frac{DF(t_i, t_{i-1})}{DF(t_i, t_{i-1}+\tau_{i})} - 1 \right\} \frac{1}{\tau_{i}}
$$

From equation (7.2.14), thus have

$$
FLT(t) = \sum_{i=k+1}^{n} C_i DF(t,t_i) = P \sum_{i=k+1}^{n} DF(t_i, t_i) \tau_{i} \left\{ \frac{DF(t_i, t_{i-1})}{DF(t_i, t_{i-1}+\tau_{i})} - 1 \right\} \frac{1}{\tau_{i}}
$$
$$= P \{ DF(t, t_k) - DF(t, t_{k+1}) + DF(t, t_{k+1}) \dots - DF(t, t_i) + DF(t, t_i) \dots - DF(t, t_n)\}
$$

and so the value of the floating leg is

$$
FLT(t) = P \{ DF(t, t_k) - DF(t, t_n)\} \quad (7.2.15)
$$

## The Swap Rate

The time $t$ swap rate $SR_t$ is the value of the fixed rate $K$ which makes the $IRS(t)$ zero. Thus, from equations (7.2.12)-(7.2.14),

$$
P \{ DF(t, t_k) - DF(t, t_n)\} - C DF(t, t_k) = P SR_t \sum_{i=k+1}^{n} DF(t_i, t_i) \tau_{i} \quad (7.2.16)
$$

so

$$
SR_t = \frac{\{ DF(t, t_k) - DF(t, t_n)\} - \frac{C}{P} DF(t, t_k)}{\sum_{i=k+1}^{n} DF(t_i, t_i) \tau_{i}} \quad (7.2.17)
$$

## Amortisation

So far we have assumed that the principal is fixed and set to the value $P$. We will now deal with the situation the principal varies with time according to the following amortization schedule:

$$
AM_i = P_{i-1} - P_i, \quad i = 0, \dots, n-1, \quad (7.2.18)
$$

where $P_i$ is the value of the principal at time $t_i$ and the value of the floating leg is

$$
FLT(t) = \sum_{i=k+1}^{n} DF(t,t_i) \tau_i \left\{ \frac{DF(t_i, t_{i-1})}{DF(t_i, t_{i-1}+\tau_{i})} - 1 \right\} \frac{1}{\tau_{i}}
$$

When there is no amortization ($AM_i = 0$; $i=0\dots n-1$), then equation (7.2.20 reduces to (7.2.15).

## Basis Swap

This is very similar to an IRS, but now there are two floating legs. For example, leg 1 could be associated with 1-month LIBOR (London Inter-Bank Offer Rate) and have a schedule of monthly payments, while leg 2 could use 3-month LIBOR. In this case, the forward rates and discount factors for leg 1 would be computed using the 1-month LIBOR curve, and the forward rates and discount factors for leg 2 will be computed the 3-month LIBOR curve.

We will use the subscripts 1 and 2 to denote quantities associated with legs 1 and 2. The payment times associated with leg 1 are $t'_{1,i}=1\dots,n_1$. While those for leg 2 are $t'_{2,i}=1\dots,n_2$, (and for this example) $n_1=3n_2$.

If counterparty A makes the quarterly payments (that receives the payments made on leg 1), the time $t$ value of the basis is

$$
BS(t) = C_1DF(t,t_k) + FLT_1(t) - C_2DF(t,t_k) - FLT_2(t) \quad (7.2.21)
$$

where we have similar notation to that used in equation (7.2.12),

$$
FLT_1(t) = P_1DF(t,t_k) - DF(t,t_n)) \quad (7.2.22)
$$

and

$$
FLT_2(t) = P_2DF(t,t_k) - DF_2(t,t_n)) \quad (7.2.23)
$$

In equations (7.2.22) and (7.2.23), $P_1$ is the principal for leg 1 and $P_2$ is the principal for leg 2. The time of the next coupon payment for leg 1 is $t_{k_1}$, while for leg 2 is $t_{k_2}$; in addition, we have used the fact that $t_{n_1}=t_{n_2}=t_n$.
