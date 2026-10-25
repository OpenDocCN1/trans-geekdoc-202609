| Method | Rank | Term | Overlap | P-value | Adjusted P-value |
| :--- | :--- | :--- | :--- | :--- | :--- |
| ssvm1 | 1 | SKIN (BULK TISSUE) | 52/2316 | 3.97 x 10^-23 | 4.28 x 10^-21 |
| ssvm2 | 1 | SKIN (BULK TISSUE) | 52/2316 | 3.97 x 10^-23 | 4.28 x 10^-21 |
| ssvm3 | 3 | SKIN (BULK TISSUE) | 34/2316 | 2.95 x 10^-9 | 1.06 x 10^-7 |
| limma | 50 | SKIN (BULK TISSUE) | 10/2316 | 7.34 x 10^-1 | 9.99 x 10^-1 |
| sam | 1 | SKIN (BULK TISSUE) | 25/2316 | 1.40 x 10^-4 | 1.52 x 10^-2 |
| t-test | 8 | SKIN (BULK TISSUE) | 5/2316 | 3.16 x 10^-3 | 3.35 x 10^-2 |
| lasso | 54 | SKIN (BULK TISSUE) | 1/2316 | 4.59 x 10^-1 | 4.59 x 10^-1 |

Table 10 Retrieved enriched terms within “ARCHS4 Tissues” via Enrichr according to uploaded genes via methods using Dataset3, showing genes expressed within tissue types. Rank column shows the order of terms when retrieved. Overlap displays a ratio-like format, corresponding to the number of uploaded genes overlapping to those in the terms. The best result is shown in bold.

![](bbox=[0.17, 0.225, 0.825, 0.7])

Fig. 10. Visualization of intersecting sets pertaining to each gene list provided by each method when Dataset3 was used.

ssvm2, outperforming ssvm3. However, results were significant for all our methods. SAM ranked the skin tissue as the 1st term, but the number of expressed genes was 25 less than those obtained via our methods. Fig. 10 provides a visualization of gene intersection among all methods. It should be noted that ssvm3 had 52 genes differing from all other methods and that ssvm1 and ssvm2 shared 37 genes. Together, all our methods shared 28 genes. SAM shared 13 genes with our methods. These results demonstrate that there was not a total overlapping among all methods, as each method produced a different list of genes affecting the enrichment analysis results. In Supplementary Data Sheet 3, we provide each list of genes produced via each method used in enrichment analysis. Moreover, we provide enrichment analysis results pertaining to Tables 9 and 10 in Supplementary Table 3_A and Table 3_B, respectively.

We selected ssvm3 for further biological analysis as it achieved good results. In Table 11, we retrieve drug-genes association. The three drugs (Retinoic acid, Vitinoin, and Alitretinoin) coincide with those in Tables 5 and 8, demonstrating improvements in treatment in clinical studies (Brehmer et al., 2011; Lee et al., 2019; Scully and Carrozzo, 2008; Sloberg et al., 1979). In Supplementary Table 3_C, we provide enrichment analysis results pertaining to drug terms within DSigDB. Regarding the two subgraphs in Fig. 11 obtained from the PPI network, the three genes (PI3, LCE2A, LCE2D) are related to the formation of the cornified envelope of the skin epidermis and oral epithelium (Fig. 12), while the LCP1 and ITGB2 are related to cytokine signaling in immune system, indicating their inflammatory role in OLP and the formation and maintenance of skin cornified envelope in LP (Anderton