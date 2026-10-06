# 174 Nanoelectronic Devices for Security

| Server ($K_i$, IDT) | Reader ($K_r$, RID) | Tag ($K_t$, TID, RID) |
|---|---|---|
| | Generates $N_g$ | 1-Query, $N_g$ | Generates $N_t$<br>Mark+00<br>Computes<br>IDX$_t = cro(RID@TID, $K_t)$ |
| Searches in IDT, and finds $<IDX_i, IDCI_i>$<br>Generates $N_g$<br>Computes<br>$M_1 = @K_i$<br>$M_2 = cro(RID@TID, $K_i@N_g)$ | 3-IDX$_i$, $N_p$, $N_r$ | 2-IDX$_i$, $N_t$ |
| | 4-IDX$_i$, $M_1$ | Obtain TID, $N_t$<br>Checks $cro(RID@TID, $K_t@N_g) = ?$M_2$<br>Computes<br>$M_3 = TID@N_g$<br>$M_4 = TID@N_g$ | 5-$M_3$, $M_4$ | Obtain $N_t$<br>Checks TID?=$M_3@N_g$<br>Computes<br>IDX$_{i+1} = cro(N_p@N_r$, $K_i)$<br>IDX$_{i+1} = cro(RID@TID, $K_{i+1})$ |
| | | 6-$K_t$-$K_{t+1}$ |
| Checks<br>$cro(RID@TID, cro(N_g@N_r$, $K_i))$<br>?=$IDX_{i+1}$<br>Computes<br>$K_{i+1} = cro(N_p@N_r$, $K_i)$<br>$K_{4+1}$-$K_{i+1}$ | 7-IDX$_{i+1}$ | |
| | 8-$M_s$ | 9-$M_s$ | Verifies $K_{i+1}$<br>Mark-01<br>Computes $M_s = @Mark@N_s$ |
| | Notification:<br>update the record | 10-$M_g$ | |
| | 11-$M_g$ | Successful update | |
| | 12 | 13 | Mark-10 |

**FIGURE 8.10** K. Fan scheme [52].

# 8.5.6 Shaohao Xie Scheme

RFID innovation is one of the center advances of the Internet of things; it has been generally used in medical services and brings a great deal of comfort for individuals in day-to-day life. This notwithstanding, the security and protection difficulties of RFID verification algorithms are increasing every day.

The main problem in current RFID algorithms typically utilize a back-end server to accumulate the data of labeled items, leading to data leakage if the user is hacked. To address this problem, the authors propose a security RFID verification convention for sanction insurance condition utilizing the method of indistinctness jumbling, which keeps the miscarriage of delicate information from the back-end worker. The list of symbols is shown in Table 8.5. Figure 8.11 shows the proposed scheme by Shaohao Xie et al. [53].

Table 8.6 shows the security flaws in the RFID authentication protocols scheme that are explained in this chapter. In conclusion, the Shaohao Xie et al. scheme [53] shows less vulnerabilities to many attacks in medical IoT.