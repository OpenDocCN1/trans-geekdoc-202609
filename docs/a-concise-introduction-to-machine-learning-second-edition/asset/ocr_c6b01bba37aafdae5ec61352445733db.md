![](bbox=[0.23, 0.178, 0.769, 0.35])

(a) $K = 4, 8.3\%$ compression ratio.

(b) $K = 16, 16.7\%$ compression ratio.

Figure 6.2: $K$ mean compression.

we need to store the pixel values of each cluster centre which requires $24K$ bits, to be encoded in $\log_2 K$ bits, and this needs to be stored for each pixel. For $K=4$, two bits are necessary. The compression ratio is then $8.3\%$. The cluster numbers are $00, 01, 10, 11$. When $K=16$, four bits are required. Figure 6.2 illustrates this. Using four clusters results in an image consisting of lighter and darker shades of brown which means the cluster centres stay too far off the axes of grey where the red, green and blue components are. 16 clusters seem an adequate representation at a compression ratio of $16.7\%$. The colours are more realistic.

Listing 6.1 reads an image of tissue stained with hematoxylin and eosin to make different types distinguishable (Image courtesy of Alin Martin, Johns University). Using three clusters, one of these identifies the nuclei.

We used $K$ means on two examples of image processing. This is a large area of ongoing research with algorithms tailored to specific applications. Gonzales & Woods (2018) give a comprehensive overview.

# 6.2 Mixture Models

```
$0 \le \pi_k \le 1 \quad \sum_{k=1}^{K} \pi_k = 1.$
```