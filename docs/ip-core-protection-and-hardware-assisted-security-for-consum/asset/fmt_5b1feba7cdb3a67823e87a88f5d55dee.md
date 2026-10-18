
# DFG of MESA Benchmark Demonstration

DFG of MESA benchmark is taken for demonstration purpose. Additionally, two adders and three multipliers are provided as resource configuration. The scheduled DFG of MESA benchmark using aforesaid resource configuration is shown in [Figure 5.5](#Chapter5.html#c05_fig5). No signature constraint is embedded in that design. Corresponding tabular representation of the same scheduling is shown in [Table 5.1](#Chapter5.html#c05_tbl1).

Now let us assume that a 7-digit buyer signature is provided as: `‘AAABACC’`. The signature provided by the buyer is then deciphered. The signature and its respective deciphered constraints are depicted in [Table 5.2](#Chapter5.html#c05_tbl2). Deciphered constraints are attained using the fingerprint encoding rules described in Section 5.3.E.

Now, the DFG of MESA benchmark needs is subjected to scheduling based on the resource configuration with fingerprinting constraints. In `cs 1`, four multiplication operations, viz., `opn 1`, `opn 2`, `opn 3`, and `opn 4`, are ready to be scheduled but only three multiplier units are present. This creates schedule operation conflict situation. This conflict can be resolved by inserting decoded fingerprint constraints in the scheduling phase. For instance, first digit `‘A’` forces even multiplication operation, i.e. `opn 2` into odd `CS`, i.e. `cs 1` while resolving scheduling conflict. Likewise, the next digit `‘A’` forces multiplication `opn 4` in odd `cs 1`, while resolving the scheduling conflict. In case of the third digit `‘A’`, no even operation is available to schedule; therefore, next multiplication is scheduled in `cs 1` by merely picking the first operation from the sorted list. Hence, `opn 1` is chosen and scheduled in `cs 1`. Similarly, for fourth digit `‘B’` odd operation, i.e. `opn 5` is scheduled in even `cs 2`, while resolving scheduling conflict. Further even operation, i.e. `opn 6` is scheduled in odd `cs 3` for fingerprint encoding of digit `‘A’`. This fingerprint constraint implanting mechanism in scheduling will operate up until all operation conflicts resolutions are done. The final schedule after embedding buyer fingerprint is shown in [Table 5.3](#Chapter5.html#c05_tbl3).

It can be observed from [Table 5.1](#Chapter5.html#c05_tbl1) (no constraints embedded) and [Table 5.3](#Chapter5.html#c05_tbl3) (with fingerprint constraints) that both the scheduled design has same number of `CS` and same resource configuration. Consequently, the buyer fingerprint is implanted in the design with completely nil area and nil latency overhead, without changing the functionality.

![image](OEBPS/images/PBCS0600-05-f05.jpg)

Figure 5.5 Scheduled DFG of MESA benchmark using two adders and three multipliers without embedding any constraints

**Table 5.1** Tabular representation of scheduled MESA benchmark using two adders and three multipliers without embedding any constraints

![image](OEBPS/images/tab5.1.jpg)

**Table 5.2** Fingerprint and watermark and its corresponding decoded constraints

![image](OEBPS/images/tab5.2.jpg)

**Table 5.3** Tabular representation of scheduled MESA benchmark using two adders and three multipliers post implanting fingerprint constraints

![image](OEBPS/images/tab5.3.jpg)

## Storage Variables and CIG Generation

Subsequently, the storage variables (`S1–S17`) are allocated in the fingerprint embedded scheduling and its equivalent CIG is generated (shown in [Figure 5.6](#Chapter5.html#c05_fig6)). In the CIG of [Figures 5.6](#Chapter5.html#c05_fig6) and [5.7](#Chapter5.html#c05_fig7), red node is indicated by `R`, yellow node by `Y`, blue node by `B`, and green node by `G`. Similar convention is applicable for [Tables 5.4](#Chapter5.html#c05_tbl4) and [5.5](#Chapter5.html#c05_tbl5). The timing table of register allocation of the same CIG is shown in [Table 5.4](#Chapter5.html#c05_tbl4).

Corresponding to two `‘C’` digits, two additional edges need to be inserted in the generated CIG as fingerprint constraints. Although two extra edges have to be inserted, but fortuitously an edge between `S1`, `S3` is previously present in the CIG. Therefore, only one new edge between `S1`, `S5` needs to be added. This indicates storage variable `S1` and `S5` must be executed through distinct register. According to [Table 5.4](#Chapter5.html#c05_tbl4), both `S1` and `S5` are executed through same register (`Green`), which indicates that modification in register allocation process is required. The revised timing table of register allocation is evident in [Table 5.5](#Chapter5.html#c05_tbl5), where `S1` is executed through register `green` and `S5` is executed through register `red`.

![image](OEBPS/images/PBCS0600-05-f06.jpg)

Figure 5.6 Colored interval graph before embedding any constraints as additional edge

![image](OEBPS/images/PBCS0600-05-f07.jpg)

Figure 5.7 Modified colored interval graph after embedding fingerprint and watermark constraints as extra edges

**Table 5.4** Timing table for register allocation pre-implanting `‘C’` digits

![image](OEBPS/images/tab5.4.jpg)

**Table 5.5** Timing table for register allocation post implanting `‘C’` digits

![image](OEBPS/images/tab5.5.jpg)

## 5.4.2 Demonstration of watermarking constraints embedding process

After implanting buyer fingerprinting constraints in the design, the fingerprint embedded design is now fed into the block for watermark insertion. For demo purpose, a 7-digit seller signature is chosen as: `‘i i i I I T !’`. The signature and its equivalent deciphered constraints as extra edge between nodes in CIG are shown in [Table 5.2](#Chapter5.html#c05_tbl2). It can be observed using the CIG shown in [Figure 5.6](#Chapter5.html#c05_fig6), only two extra edges ((`S2`, `S7`) and (`S1`, `S4`)) as constraints requires implanting in the CIG, because rest of the five edges are previously existing. Because of an extra edge injected between `S1` and `S4`, both are forced to execute in distinctive registers. `S2` and `S7` are by default implemented using distinctive registers as apparent in [Table 5.5](#Chapter5.html#c05_tbl5). The final revised CIG is shown in [Figure 5.7](#Chapter5.html#c05_fig7), and [Table 5.6](#Chapter5.html#c05_tbl6) depicts its corresponding timing table for register allocation. In [Figure 5.7](#Chapter5.html#c05_fig7), dotted edge between `S1` and `S5` indicates fingerprint constraints and dotted edge between `S2` and `S7` indicates watermark constraints. It is evident that nil area and latency overhead are obtained after implanting watermark. Therefore, in case of MESA application, implanting both fingerprint and watermark attains completely nil area and latency design.

**Table 5.6** Timing table for register allocation post implanting fingerprint and watermark constraints

![image](OEBPS/images/tab5.6.jpg)

# 5.5 Analysis of case studies for DSP cores

Symmetrical IP core protection mechanism in Roy and Sengupta ([2017](#Chapter5.html#c05_bib32)) generates a low overhead strongly secured DSP IP core design. To validate the robustness and low overhead, following metrics are used by Roy and Sengupta ([2017](#Chapter5.html#c05_bib32)):

*   Implanting cost for both signatures in a design indicating design quality.
*   Area overhead with respect to resources and extra register needed while implanting fingerprint and watermark.
*   Time consumed to generate signature.
*   Strength of signature in terms of probability of coincidence.
*   Influence of large size fingerprint and watermark on design area, design delay, and implanting cost.
*   Scalability to deal with bigger size applications.

Therefore, the analysis/case study section is divided as follows: (i) result of symmetrical IP core protection approach ([Roy *et al.*, 2008](#Chapter5.html#c05_bib10)) in context of design latency, design area, embedding cost, and strength of signature, and (ii) comparative study between Roy *et al.* ([2008](#Chapter5.html#c05_bib10)) and unsymmetrical IP core protection approach ([Koushanfar *et al.*, 2005](#Chapter5.html#c05_bib18)). (Note: as no approach for symmetrical IP core protection exists for DSP core.)
