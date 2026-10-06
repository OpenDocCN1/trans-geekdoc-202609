# 3 SHARPNESS-BASED DISTRIBUTION ROBUST OPTIMIZATION

![](bbox=[0.23, 0.14, 0.77, 0.4])

FIGURE 3.6. Efficiency comparison between SharpDRO and SAM.

the worst-case performance of SAM, owing to our efficient worst-case data selection, which is vital for robust generalization against severe corruptions.

# 3.6 Conclusion

In this Chapter, we propose a SharpDRO approach to enhance the generalization performance of DRO methods. Specifically, we focus on minimizing the sharpness of worst-case data to learn flat loss surfaces. As a result, SharpDRO is more robust to severe corruption compared to other methods. Moreover, we apply SharpDRO to distribution-average and distribution-agnostic settings and propose an OOD detection process to select the worst-case data when the distribution index is not known. Extensive quantitative and qualitative experiments have been conducted to show that SharpDRO can deal with the most challenging corrupted distributions and achieve improved generalization results compared to well-known baseline methods.