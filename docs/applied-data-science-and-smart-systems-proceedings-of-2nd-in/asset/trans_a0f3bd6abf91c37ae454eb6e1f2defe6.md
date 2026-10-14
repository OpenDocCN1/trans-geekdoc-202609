
-   [SLIVER 数据集包含具有不同形状、大小和病理状态的多种肝脏图像，使其适合用于训练稳健的算法。]

### IRCAD 数据集

[IRCAD 数据集用于评估增强算法的性能测试数据集。]

[该数据集包含肝脏结构的 CT 图像，可用于在不同数据集上验证算法的泛化能力。]

[体积重叠误差 (VOE)：测量分割体积与真实标注体积之间的重叠误差。]

[相对体积差 (RVD)：量化分割区域与真实标注区域之间的体积相对差异。]

[平均对称表面距离 (ASD)：测量分割区域表面与真实标注区域表面之间的平均距离（`[Figure 56.1](#ch56.xhtml#ch56_xhtml#fig56_1)`、`[Figure 56.2](#ch56.xhtml#ch56_xhtml#fig56_2)`、`[Figure 56.3](#ch56.xhtml#ch56_xhtml#fig56_3)` 和 `[Figure 56.4](#ch56.xhtml#ch56_xhtml#fig56_4)`）。]

![Figure 56.1 The comparison of existing and the proposed methods. (a) Represents the original images. (b) Represents the ground truth images. (c) Represents the existing method and (d) Represents the proposed method.](images/fig56_1_B.jpg)

[Figure 56.1 The comparison of existing and the proposed methods. (a) Represents the original images. (b) Represents the ground truth images. (c) Represents the existing method and (d) Represents the proposed method.](#ch56.xhtml#R_fig56_1)

![Figure 56.2 Shows the original image belongs to the SLIVER dataset](images/fig56_2_B.jpg)

[Figure 56.2 Shows the original image belongs to the SLIVER dataset](#ch56.xhtml#R_fig56_2)

![Figure 56.3 Shows the intensity histogram for the whole CT image](images/fig56_3_C.jpg)

[Figure 56.3 Shows the intensity histogram for the whole CT image](#ch56.xhtml#R_fig56_3)

![Figure 56.4 The intensity histogram for the whole CT image](images/fig56_4_B.jpg)

[Figure 56.4 The intensity histogram for the whole CT image](#ch56.xhtml#R_fig56_4)

[它充分展示了所提工作的分割效果优于当前方法。]

## Performance metrics

[提议算法的性能通过多种指标量化，包括 RVD、VOE、RMSD、ASD 和 MSD。]

### SLIVER 数据集结果

[提议算法的性能指标与现有 CV 模型在 SLIVER 数据集上的表现进行对比，如 [Table 56.1](#ch56.xhtml#tab56_1) 所示。]

[Table 56.1 Results for SLIVER](#ch56.xhtml#R_tab56_1)

| Data || Method || VOE || RVD || ASD || RMSD || MSD |
| --- | --- | --- | --- | --- | --- | --- |
| SLIVER || Existing || 7.6 || -0.1 || 0.8 || 1.5 || 20.8 |
| --- | --- | --- | --- | --- | --- | --- |
|  || Proposed || 7.3000 || -0.0800 || 0.6400 || 1.3200 || 19.2000 |

[VOE：提议算法的 VOE 为 7.3%，表明其分割体积与真实标注体积的重叠比现有模型的 VOE（7.6%）更好。]

[RVD：提议算法的 RVD 为 -0.08%，表明其分割体积与真实标注体积更接近，优于现有模型的 -0.1%。]

[ASD：提议算法的 ASD 值为 0.64 mm，显示出比现有模型的 0.8 mm 更佳的平均表面距离。]

[RMSD：提议算法的 RMSD 为 1.32 mm，表明其根均方距离较现有模型的 1.5 mm 更小。]

[MSD：提议算法的 MSD 为 19.2 mm，优于现有模型的 20.8 mm，体现了最大对称表面距离的改善。]

### IRCAD 数据集结果

[提议算法的性能指标同样与现有 CV 模型在 IRCAD 数据集上的表现进行对比，如 [Table 56.2](#ch56.xhtml#tab56_2) 所示。]

[Table 56.2 Results for IRCAD](#ch56.xhtml#R_tab56_2)

| Data || Method || VOE || RVD || ASD || RMSD || MSD |
| --- | --- | --- | --- | --- | --- | --- |
| IRCAD || Existing || 6.5 || 4.1 || 1.9 || 2.1 || 18.9 |
| --- | --- | --- | --- | --- | --- | --- |
|  || Proposed || 6.1000 || 3.8000 || 1.3000 || 1.2000 || 17.4000 |

[VOE：提议算法的 VOE 为 6.1%，优于现有模型的 6.5%。]

[RVD：提议算法的 RVD 为 3.8%，低于现有模型的 4.1%。]

[ASD：提议算法的 ASD 值为 1.3 mm，显示出相较现有模型的 1.9 mm 有所提升。]

[RMSD：提议算法的 RMSD 为 1.2 mm，低于现有模型的 2.1 mm。]

[MSD：提议算法的 MSD 为 17.4 mm，优于现有模型的 18.9 mm。]

## Discussion

[SLIVER 和 IRCAD 数据集的实验结果表明，提议算法在肝脏分割方面优于现有 CV 模型。]

[提议算法在所有性能指标上均持续超越现有模型，体现了其在肝脏 CT 图像分割方面的准确性和稳健性。]

[VOE 和 RVD 的下降表明分割体积与真实标注之间的重叠更好、相似度更高。]

[ASD、RMSD 和 MSD 的降低表明分割表面与真实标注的对齐更好，提升了分割精度。]

[分割肝脏区域的可视化对比进一步支持了算法的有效性，图片显示提议算法能够更精确地提取肝脏结构，并更贴合真实轮廓。]

[提议算法通过引入形状先验信息并增强 CV 模型，实现了肝脏分割性能的提升。]

[结果显示分割更准确、体积对应更紧密、表面距离更小，较现有模型表现更佳，这对医学影像分析的临床决策具有重要意义。]

## Conclusion

[提议的肝脏分割算法结合形状先验信息并增强 CV 模型，表现优于现有方法。]

[通过在 SLIVER 和 IRCAD 数据集上的全面评估，算法在体积重叠、表面距离和对称性等多项指标上始终取得更好结果，展示了其在 CT 图像中精准可靠地分割肝脏区域的潜力，有望提升医学影像分析和辅助临床决策。]

## Future work

[本研究可通过以下方式扩展：]

[1. 使用更大规模且更具多样性的数据集进行训练和测试。]

[2. 进一步研究和提升算法在不同图像质量和噪声水平下的鲁棒性与适应性。]

[3. 引入先进的机器学习技术（如深度学习）可能进一步提升算法性能。]

[4. 探索实时实现并将其集成到医学影像软件中，使其更易于实际临床应用。]

[5. 将该算法应用于其他医学影像中的器官和结构分割，可拓宽其在医学影像分析领域的影响范围。]

## References

*   [Zheng, S., Fang, B., Li, L., Gao, M., Zhang, H., Chen, H., and Wang, Y.](#ch56.xhtml#R_ref56_1) (2017). A novel variational method for liver segmentation based on statistical shape model prior and enforced local statistical feature. 2017 IEEE 14th Int. Symp. Biomed. Imag. (ISBI 2017), 261–264.

*   [Saito, K., Lu, H., Tan, J., Kim, H., Yamamoto, A., Kido, S., and Tanabe, M.](#ch56.xhtml#R_ref56_2) (2017). Automatic liver segmentation from multiphase CT images by using level set method. 2017 17th Int. Conf. Con. Autom. Sys. (ICCAS), 1590–1592.
