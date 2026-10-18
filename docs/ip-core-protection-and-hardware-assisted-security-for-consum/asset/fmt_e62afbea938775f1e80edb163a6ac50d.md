
As mentioned earlier, this structurally obfuscated design is next fed as input with the module library and PSO control parameters to explore a low-cost design solution of DSP circuit through PSO. [Figure 7.15](#Chapter7.html#c07_fig15) represents the final low-cost, structurally obscured scheduled IP design using three adders and one multiplier (obtained through PSO-DSE). The DSP circuit representation of the same is depicted in [Figure 7.16](#Chapter7.html#c07_fig16). It uses eight 8:1 switches, 18 input registers, 2 output registers, and 13 delay elements. The changes (due to structural obfuscation) in the DSP circuit for this application at register-transfer/module level and gate level are reported in [Table 7.1](#Chapter7.html#c07_tbl1). (Note: Similarly, functionally equivalent obfuscated DSP IP core can be obtained for well-known applications such as FIR, IIR, HWT, JPEG CODEC, DCT, and IDCT. A case study of obfuscated JPEG CODEC is described in Chapter 9).

![image](OEBPS/images/PBCS0600-07-f15.jpg)

Figure 7.15 Scheduled low-cost obfuscated DSP IP design with three adders and one multiplier (Note: Resource configuration is explored through PSO-DSE)

![image](OEBPS/images/PBCS0600-07-f16.jpg)

Figure 7.16 Functionally equivalent DSP circuit (low-cost). (Note: Encircled portion indicates DSP circuits components transformed due to obfuscation, without change of functionality)

**Table 7.1** Module- and gate-level comparison of multistage obfuscated ([Sengupta et al., 2017a](#Chapter7.html#c07_bib36)) design with original design

![image](OEBPS/images/tab7.1.jpg)

### 7.6 Analysis of case studies

The multistage structural obfuscated mechanism section presented in Sengupta *et al.* ([2017a](#Chapter7.html#c07_bib36)) is separated into three sub-sections: (1) result of multistage structural obfuscation in terms of design latency, design area, embedding cost and security on case studies/test cases, (2) comparative study between single-stage structural obfuscation ([Lao and Parhi, 2015](#Chapter7.html#c07_bib14)), and (3) multistage structural obfuscation ([Sengupta *et al.*, 2017a](#Chapter7.html#c07_bib36)).

For the analysis, a 15nm NanGate technology library ([Open Cell Library, 2017](#Chapter7.html#c07_bib50)) is employed to assess both design area and design latency of a DSP circuit. While calculating the design cost using [(7.3)](#Chapter7.html#c07_eqn3) both *Ø*[1] and *Ø*[2] are assigned 0.5 to deliver equivalent priority to both silicon area and design latency. However, it may be possible to tune the weighing factors to provide different preference on silicon area and design latency. Further, following optimal settings from Sengupta *et al.* ([2017b](#Chapter7.html#c07_bib37)) are employed for PSO engine: *b*[1] and *b*[2] (acceleration coefficients) = 2; *ω* (inertia weight) = linearly diminishing between 0.9 and 0.1; *r*[1] and *r*[2] (random numbers) = 1; swarm size *p* = 3/5/7; *δ* = 10 or *I*[max] = 100 as terminating condition.

#### 7.6.1 Result of multistage structural obfuscation

The results of low-cost multistage structural obfuscation approach in terms of design latency, design area, and embedding cost with different particle size are shown in [Table 7.2](#Chapter7.html#c07_tbl2). It is shown from [Table 7.2](#Chapter7.html#c07_tbl2) that no reduction in the quality (cost) of design solution is found with the increment of particle size, for except “Auto Correlation” benchmark. In “Auto Correlation” benchmark, for particle size 5, the design cost is better than particle size 3, but it remains the same for both swarm size 5 and 7. Further, the low-cost design solution for all obfuscated DSP benchmarks generated through the PSO-DSE process also satisfies the user-provided design constraints. Design cost is a normalized metric that denotes the total area and total latency of a DSP circuit design. Design cost also known as implementation cost of a DSP design is a normalized function of area and latency.

**Table 7.2** Results for low-cost multistage obfuscated ([Sengupta et al., 2017a](#Chapter7.html#c07_bib36)) DSP core for different particle size

![image](OEBPS/images/tab7.2.jpg)

The strength of the multistage obfuscation can be calculated using a metric called “Power of Obfuscation” ([Sengupta and Roy, 2017](#Chapter7.html#c07_bib32)). The *power of obfuscation* is calculated based on the structural divergence between the original DSP circuit design and its transformed version. Power of Obfuscation (*P*^(obf)) indicates a normalized value between 0 and 1, and is expressed using the following expression:

![image](OEBPS/images/c07_eqn6.gif)

where *n*[*i*] is the unique number of modified nodes due to *i*th stage transformation method; *n*[T] is the total number of nodes of the original (before applying any transformation method) DSP circuit. A higher value of *P*^(obf) indicates stronger security of an obfuscated DSP design. A modified node is defined based on the following four cases ([Sengupta *et al.*, 2017a](#Chapter7.html#c07_bib36)):

*   If parents of a node in the structurally transformed CDFG are changed than its original

*   If child of a node in the structurally transformed CDFG is changed than its original

*   If the operation type of a node in the structurally transformed CDFG is changed than its original

*   If a node existing in the original CDFG does not present in the obfuscated design

#### 7.6.2 Comparative study and discussion

[Table 7.3](#Chapter7.html#c07_tbl3) reports a comparative study of an original (nonsecured) design with its structurally obfuscated version with respect to obfuscated design area, latency, and cost. For instance, the design latency, area, and cost of original autoregressive filter (ARF) benchmark are 2,573.5 ps, 241.80 μm², and −0.26, respectively, whereas, for structurally obfuscated ARF benchmark, the design area, design latency, and design cost are 241.80 μm², 1900.80 ps, and −0.37, respectively. It can be seen from [Table 7.3](#Chapter7.html#c07_tbl3) that an obfuscated design may achieve lesser execution time compared to the original design. This is because due to multistage transformations the obfuscated design may reduce the total number of operations available in the graph. Therefore, the structurally transformed graph may optimize the latency after scheduling.

**Table 7.3** Comparison of multistage obfuscated ([Sengupta et al., 2017a](#Chapter7.html#c07_bib36)) design with original design

![image](OEBPS/images/tab7.3.jpg)

[Table 7.4](#Chapter7.html#c07_tbl4) reports the comparative study between the multistage-based obfuscation technique ([Sengupta *et al.*, 2017a](#Chapter7.html#c07_bib36)) with the single-stage-based obfuscation technique ([Lao and Parhi, 2015](#Chapter7.html#c07_bib14)) with respect to design area, latency, and obfuscation design cost. For instance, for ARF benchmark (Mohanty *et al.*, 2008; Sengupta and Mohanty, 2016) the design area, design latency, and design cost of single-stage obfuscation approach are 788.80 μm², 1,511.50 ps, and −0.08, respectively, while the low-cost multistage obfuscation approach explores low-cost design solution through PSO-DSE for the same benchmark (design area, latency, and cost are reported earlier). Therefore, the low-cost multistage obfuscation approach achieves 47% reduction of design cost on average for standard benchmarks (DSP Benchmark Suite, 2017; Benchmark1, 2017; Benchmark2, 2017), compared to single-stage obfuscation approach ([Lao and Parhi, 2015](#Chapter7.html#c07_bib14)). As mentioned earlier, the reduction of design cost is achieved for multistage obfuscation technique because it performs PSO-DSE-based optimization on area-delay trade-off to explore the low-cost design solution. The graphical representation of design cost comparison between single-stage and multistage obfuscation is shown in [Figure 7.17](#Chapter7.html#c07_fig17).
