# 182 Hardware architectures for deep learning

with input that can entirely fit in IFM buffers, removing the need for mem_lst_cycles. While $1 \times 1$ convolution is bounded by data traffic due IFMs and OFM partial sums (mem_lst_cycles, stage 4), dense inner product computation in FCL is limited by weight data traffic (wt_ld_cycles, stage 2).

# 8.9.1.2 Exploration strategy

To choose optimum values of design variables, we perform design space exploration to estimate resource usage and runtime latency. We allow $Tn$ to vary as powers of two, $Tm$ takes intermediate values as well to improve DSP usage. Performance scales linearly with DSPs up to some power of two due to the nature of feature map dimensions used in CNNs, after which the gain is nominal. Designs that do not satisfy DSP and BRAM requirements of the FPGA board are rejected. We then check logic usage of designs in descending order of the highest performance and select the first one that satisfies the logic resource thresholds. This reduces the total exploration time.

# 8.9.1.3 Design variable optimization

The runtime and resource optimization strategies for VGG and GoogLeNet are shown in Figure 8.11. 8.11(a) and (d) show how the runtime latency varies with the sweep of $Tn$ and $Tm$ for values that satisfy resource constraints of the FPGA. Optimal pairs of these tiling factors are obtained with the least latency. Furthermore, $Tr$ also has an impact on performance along BRAM usage. For a network with large layer dimensions like VGG, i.e., with large $max\_$, $Tr$ can only be increased to a relatively lower extent as the buffer depth quickly saturated BRAM resources. This is seen in Figure 8.11(b) as $Tr$ has a maximum sweep of up to 18. On the other hand, GoogLeNet layer dimensions are relatively smaller and $Tr$ tile can be made as large as 68 but buffer initialization overheads start dominating for on-chip buffers and best performance occurs at 13, i.e., visible in Figure 8.11(e). To provide higher on-chip bandwidth, buffer depths, the burst length needs to be sacrificed, leading to poor off-chip memory performance. To keep the CE from stalling, we give higher preference to the on-chip bandwidth by instantiating as wide as on-chip buffers as needed and then optimize the performance by using the $Tr$ values. Figure 8.11(c) and (f) show how used BRAMs change in incremental steps. for VGG and GoogLeNet, respectively. If the value of $Tr$ at a step in Figure 8.11(f) falls inside the monotonic region in BRAM requirement can be reduced by reducing $Tr$ by 1 with marginal no reduction in performance. This can result in simplified routing leading to higher operating frequency.

# 8.9.2 Onboard runs

# 8.9.2.1 Network-specific runs

We run the optimizer for four different CNNs to minimize total cycles taken in all layers of a particular CNN. The resulting architecture configurations $<Tn, Tm, Tr, Tp>$