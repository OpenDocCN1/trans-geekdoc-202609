single operation, \(O_{B1}\), there is no chance for site A and site C to garbage collect \(O_{A2}\) and \(O_{C2}\). In a worse situation, if a site has no operation submitted, then, no site in the system can garbage collect any operation.

# 4.3.5.2 Timestamp Matrix

For systems that use timestamp matrices, they can learn the stable operations without any additional message exchanges. At site \(i\), a cell in its timestamp matrix, \(TM_i[j][k] = t\), means that according to site \(i\)’s conservative estimate, site \(j\) has received all operations originated from site \(k\) up to \(t\). Hence, to find out what operations from site \(k\) that have become stable, all we need is to take the minimum of all rows at element \(k\), i.e., if \(min(TM_i[0][k], TM_i[1][k], ..., TM_i[N-1][k] = t\), all sites have received the first \(t\) operations submitted at site \(k\).

![](bbox=[0.12, 0.44, 0.88, 0.75])

Figure 4.16 Update commit using timestamp matrices in a system with three replicas.

Consider a system shown in Figure 4.16. Site A’s timestamp matrix is:

```
(
3 1 0
)
(
2 1 0
)
(
0 0 0
)
```