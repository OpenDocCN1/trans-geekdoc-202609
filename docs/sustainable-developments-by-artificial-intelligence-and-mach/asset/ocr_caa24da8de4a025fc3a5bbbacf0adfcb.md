(c) Line capacity constraint:

$|S_{ij}| \le |S_{max}|$ (6.14)

# 6.2.4 Inequality constraints of DG units

In the case of PV, the DG source only delivers active power, while in the case of WT, the DG source delivers active and reactive power (Chang & Chinh, 2020; Dehghani et al., 2020; Hassan & Zellagui, 2019; Imran & Kowsalya, 2014; Karimizadeh et al., 2020; Lasmari et al., 2020).

(a) DG capacity limits:

$P_{DG}^{min} \le P_{DG} \le P_{DG}^{max}$ (6.15)

$Q_{DG}^{min} \le Q_{DG} \le Q_{DG}^{max}$ (6.16)

(b) Power Factor of DG:

$PF_{DG}^{min} \le PF_{DG} \le PF_{DG}^{max}$ (6.17)

$PF_{DG} = \frac{P_{DG}}{\sqrt{P_{DG}^2 + Q_{DG}^2}}$ (6.18)

(c) Position of DG:

$2 \le DG_{position} \le N_{bus}$ (6.19)

(d) Number of DG:

$N_{DG} \le N_{DG.max}$ (6.20)

(e) Location of DG:

$n_{DG,i} / Location \le 1$ (6.21)

The limits of constraint values are shown in Table 6.1.

# 6.3 Cosine adapted whale optimization algorithm (CAWOA)

In 2016, Mirjalili developed the basic whale optimization algorithm (WOA) approach (Mirjalili & Andrew, 2016) as an innovative biological-inspired heuristic technique. The natural body motions of humpback whales are the basis of the WOA. Three steps are used to describe the bubble-net hunting process and