# 9.11 Pruning and thresholding policy

Figures 9.24(a) and 9.25(a) show the accuracy, and normalized FLOP and parameter counts for the PTPH policies, while Figures 9.24(b) and 9.25(b) capture the used for experimented thresholding and pruning policies in the hybrid approach. The figures are divided into five sections, one for each TP. Each segment assesses the impact of five different pruning policies on total parameter and FLOP count when with thresholding in PTP.

# 9.11.1 Fixed percentage PTPH

Figure 9.24(a) shows the normalized accuracy, FLOP and parameter counts for the $FTPHP_{FP}$ policy. For each TP, we study how $P_{ih}$ policy affects the FLOP and parameter counts by highlighting the increase and decrease in the average count by red and black colors.

An inverse trend is observed when both thresholding and pruning policies are aggressive (images with lower confidence are classified in early iterations, and

![](bbox=[0.083, 0.413, 0.913, 0.706])

Figure 9.24 The accuracy and average FLOP and parameter counts (normalized to ICNN with no pruning or threshold policy) for PTPH$FP_{FP}$. (a) Flop/Parameter count and accuracy. (b) Detection and selection thresholds for each iteration. For each thresholding policy (i.e., $D_{Ci}$ vector), multiple pruning policies (i.e., $S_{ih}$ vector) are investigated. The red and black bars show the increase and reduction, respectively, in the number of FLOP and parameter counts of a thresholding policy due to pruning