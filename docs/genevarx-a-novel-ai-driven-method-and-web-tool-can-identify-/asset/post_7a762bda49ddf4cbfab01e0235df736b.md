
![](img/5167e39db543350967ce62ea50022e12_6_0.png)

### Fig. 3. Three highly interconnected clusters in a protein-protein interaction based on 100 genes from ssvm3 provided to Metascape enrichment analysis.

![](img/5167e39db543350967ce62ea50022e12_6_1.png)

### Fig. 4. Skin of a patient, with LP affecting the arm area. Critical expressed genes obtained from Fig. 3 are shown in the skin epidermis and dermis. Source: Figure created with BioRender.com.

![](img/5167e39db543350967ce62ea50022e12_6_2.png)

### Fig. 5. Fifteen transcription factors provided by Metascape according to the list of 100 input genes from ssvm3.

therapeutic targets for OLP (de Lanna et al., 2022). Keratin 19 (KRT19) has been found to be expressed in OLP (Farah et al., 2021; Schreurs et al., 2020). KRT16 has been reported to be associated with LP in the wound repair process (Vo et al., 2021) and IFI27 has been reported to be overexpressed in OLP (de Lanna et al., 2022). IRF1 and IFITM1 have been induced in LP, demonstrating their involvement in the skin injury process (Wenzel and Tüting, 2008). These 14 expressed genes can be considered as potential therapeutic targets for LP treatment. Moreover, they contribute to a greater understanding of LP pathogenesis. As shown in Fig. 5, we identified 15 transcription factors: RELA, NFKB1, SP1, STAT1, ETS1, STAT3, STAT2, JUN, HIF1A, IRF1, SRF, ETS2, CIITA, SMAD3, and SPI1. It has been reported in LP (Braegelmann et al., 2021). STAT1 has been reported to play a key role in the immune response in LP (Shao et al., 2019). OLP has been reported to be associated with increased expression of SMAD3 (Evert et al., 2021). These 14 identified genes and 15 transcription factors may prove useful as therapeutic targets and for understanding the molecular mechanism of LP.

### 3.2.2. Dataset2

Table 6 reports terms (i.e., diseases) associated with selected genes while Table 7 reports terms (i.e., tissue type) according to expressed genes after uploading genes obtained via each method. It can be seen in Table 6 that our methods (ssvm1, ssvm2, and ssvm3) outperformed

Table 6
Retrieved enriched terms within “DisGeNET” via Enrichr according to uploaded genes via methods using Dataset2, showing association between human genes and diseases. Rank column shows the order of terms when retrieved. Overlap displays a ratio-like format, corresponding to the number of uploaded genes overlapping to those in the terms. The best result is shown in bold.

| Method | Rank | Term | Overlap | P-value | Adjusted P-value |
| :--- | :--- | :--- | :--- | :--- | :--- |
| ssvm1 | 10 | SKIN DISEASES, GENETIC | 7/45 | 2.45 x 10^-9 | 7.93 x 10^-7 |
| | 421 | AUTOIMMUNE DISEASES | 13/1060 | 2.37 x 10^-3 | 1.82 x 10^-2 |
| | 13 | DERMATOLOGIC DISORDERS | 14/406 | 1.46 x 10^-8 | 3.57 x 10^-6 |
| ssvm2 | 10 | SKIN DISEASES, GENETIC | 7/45 | 2.45 x 10^-9 | 7.93 x 10^-7 |
| | 421 | AUTOIMMUNE DISEASES | 13/1060 | 2.37 x 10^-3 | 1.82 x 10^-2 |
| | 13 | DERMATOLOGIC DISORDERS | 14/406 | 1.46 x 10^-8 | 3.57 x 10^-6 |
| ssvm3 | 10 | SKIN DISEASES, GENETIC | 7/45 | 2.45 x 10^-9 | 7.93 x 10^-7 |
| | 421 | AUTOIMMUNE DISEASES | 13/1060 | 2.37 x 10^-3 | 1.82 x 10^-2 |
| | 13 | DERMATOLOGIC DISORDERS | 14/406 | 1.46 x 10^-8 | 3.57 x 10^-6 |
| limma | - | SKIN DISEASES, GENETIC | - | - | - |
| | 944 | AUTOIMMUNE DISEASES | 6/1060 | 4.38 x 10^-1 | 6.58 x 10^-1 |
| | 795 | DERMATOLOGIC DISORDERS | 3/406 | 3.31 x 10^-1 | 5.92 x 10^-1 |
| sam | - | SKIN DISEASES, GENETIC | - | - | - |
| | - | AUTOIMMUNE DISEASES | - | - | - |
| | - | DERMATOLOGIC DISORDERS | - | - | - |
| t-test | - | SKIN DISEASES, GENETIC | - | - | - |
| | 578 | AUTOIMMUNE DISEASES | 1/1060 | 6.81 x 10^-1 | 7.00 x 10^-1 |
| | - | DERMATOLOGIC DISORDERS | - | - | - |
| lasso | - | SKIN DISEASES, GENETIC | - | - | - |
| | 516 | AUTOIMMUNE DISEASES | 1/1060 | 6.03 x 10^-1 | 6.40 x 10^-1 |
| | 445 | DERMATOLOGIC DISORDERS | 1/406 | 2.94 x 10^-1 | 3.61 x 10^-1 |

Table 7
Retrieved enriched terms within “ARCHS4 Tissues” via Enrichr according to uploaded genes via methods using Dataset2, showing genes expressed within tissue types. Rank column shows the order of terms when retrieved. Overlap displays a ratio-like format, corresponding to the number of uploaded genes overlapping to those in the terms. The best result is shown in bold.

| Method | Rank | Term | Overlap | P-value | Adjusted P-value |
| :--- | :--- | :--- | :--- | :--- | :--- |
| ssvm1 | 1 | SKIN (BULK TISSUE) | 47/2316 | 1.05 x 10^-18 | 1.13 x 10^-16 |
| ssvm2 | 1 | SKIN (BULK TISSUE) | 47/2316 | 1.05 x 10^-18 | 1.13 x 10^-16 |
| ssvm3 | 1 | SKIN (BULK TISSUE) | 47/2316 | 1.05 x 10^-18 | 1.13 x 10^-16 |
| limma | 65 | SKIN (BULK TISSUE) | 10/2316 | 7.34 x 10^-1 | 9.99 x 10^-1 |
| sam | 42 | SKIN (BULK TISSUE) | 2/2316 | 3.69 x 10^-1 | 6.76 x 10^-1 |
| t-test | 31 | SKIN (BULK TISSUE) | 4/2316 | 2.19 x 10^-1 | 6.35 x 10^-1 |
| lasso | 51 | SKIN (BULK TISSUE) | 2/2316 | 6.01 x 10^-1 | 8.76 x 10^-1 |

baseline methods. Specifically, skin diseases-genetic ranked 10th with 7 commonly expressed genes (DSP, FLG2, COL7A1, SPINK5, PKP1, ADAR, ITGA6) out of 45. Autoimmune diseases ranked 421st with 13 commonly expressed genes (FLG, SPARC, DST, STAT1, ADAR, ENO1, HMGCR, TTN, PTPRC, SOAT1, LMNA, FGFR3, TP63) out of 1060 genes. The dermatologic disorders term was ranked 13th with 14 commonly expressed genes (FLG, DSP, DST, SPINK5, DHCR24, ADAR, SFPQ, DES, COL7A1, LMNA, FGFR3, TP63, SPRR1B, IVL) out of 406. Baseline methods demonstrated inferior results as retrieved terms ranked worse terms. Moreover, no baseline method was able to identify all terms (e.g., skin diseases-genetic, autoimmune diseases, dermatologic disorders). For example, SAM had no related terms. Hence, results were designated as “-”. The same held true when a baseline method did not retrieve the term. In Table 7, it is evident that our methods (i.e., ssvm1, ssvm2, and ssvm3) retrieve the related term (i.e., SKIN (BULK TISSUE)), ranking 1st with 47 expressed genes out of 2316. Baseline methods had worse ranking results. These results in Tables 6 and 7 demonstrate the superiority of our methods for disease identification as well as identification of tissues related to the studied problem. Fig. 6 provided useful information pertaining to intersecting genes of each provided method. Our methods shared 98 genes in common while they differed in only 2 genes. Limma had 98 different genes from all other methods. The t-test and lasso methods differed by 9 and 16 genes, respectively. Our methods and limma shared 1 gene in common. The same was true for our methods relative to the t-test. These visualized results demonstrate that our methods differ from existing methods and therefore results were different in Tables 6 and 7. In Supplementary Data Sheet 2, we provide a list of genes produced by each method used in enrichment analysis. Moreover, we provide enrichment analysis results pertaining to Tables 6 and 7 in Supplementary Table 2,A and Table 2,B, respectively. As our methods performed better than baseline methods and shared 98 genes, we selected ssvm3 to gain further biological insights within the molecular mechanism of LP. We retrieved drugs associated with genes produced via ssvm3 from Enrichr, followed by uploading the produced 100 genes into Metascape. Table 8 shows the drug terms and associated genes obtained from Enrichr. Retinoic acid has been reported to be effective as a topical treatment in OLP (Laurence Le Cleach and Chosidow, 2012; Qiao et al., 2022). Oral treatment of tretinoin (a generic name of Vitinoin) has been reported to be effective in treating LP (Lee et al., 2019). In Supplementary Table 2,C, we provide enrichment analysis results pertaining to drug terms within DSigDB. In Fig. 7, two subgraphs obtained from PPI networks are shown, including the following 25 genes: COL6A3, COL3A1, COL5A2, COL7A1, ITGA6, FN1, AGRN, HSPG2, VCAN, TTN, SOAT1, HSP90AB1, ATP6V1B1, HMGCR, HMGCS1, DSP, HRNR, FLG2, FLG, PKP1, RPL35A, RPS27A, RPS14, RPSA, and RPL37A. Some of these genes have been reported to be related to skin diseases. For example, genes related to the extracellular matrix shown in Fig. 8 (including COL6A3, COL3A1, COL5A2, COL7A1, ITGA6, FN1, AGRN, HSPG2, VCAN, DSP) directly contribute to skin cutaneous diseases such as LP (Dussoyer et al., 2022; Huang et al., 2022; Salazar et al., 2022). Mutations in genes related to ribosomes (RPL35A, RPS27A, RPS14, RPSA, and RPL37A) are the key to several disorders (Jiao et al., 2023; Lafitta-Navarro and Concetti Sorrell, 2023; Lee et al., 2022; Moitinho-Silva et al., 2022; Taupelt et al., 2022). These results may play a critical role in identifying putative therapeutic targets and thereby identifying effective drugs. In Fig. 9, four transcription factors were reported (i.e., RELA, STAT3, TP53, STAT1). TP53 has been reported to be overexpressed
