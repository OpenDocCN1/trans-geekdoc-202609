The 12 landscape metrics were thus:

+   1 Total core area of forest – the total number of pixels of forest located in the core area of the patch, which is the area defined with a core–buffer distance of 1 pixel (30 m in this case)
+   2 Per cent cover of forest – the number of pixels of forest divided by the total number of pixels in the landscape
+   3 Per cent cover of urban area – the number of pixels of urban area divided by the total number of pixels in the landscape
+   4 Per cent cover of agricultural land – the number of pixels of agricultural land divided by the total number of pixels in the landscape
+   5 Number of forest patches – the number of patches of forest cover
+   6 Number of urban patches – the number of patches of urban land cover
+   7 Mean patch size of forest – the total area of forest cover divided by the number of forest patches
+   8 Mean patch size of urban area – the total area of urban land cover divided by the number of urban patches
+   9 Total forest edge – the total length of edge around all forest patches in the landscape
+   10 Edge density of forest– the total length of edge around all forest patches in the landscape divided by the total area of the landscape
+   11 Mean patch fractal dimension of forest – calculated as:

where N is the number of patches in the landscape, m is the number of land use/cover categories, ni is the number of patches of land use/cover type i, Pij is the perimeter of the jth patch of land use/cover type i and Aij is the area of the jth patch of land use/cover type i

+   12 Mean nearest neighbour between forest patches – the sum of the smallest distances between the edge of each forest patch and its closest forest patch, divided by the number of forest patches in the landscape

```
MPFD = \frac{\sum_{i=1}^m \sum_{j=1}^{n_i} \frac{2 \times ln(0.25 \times P_{ij})}{ln A_{ij}}}{N}
(10.16)
```

In this study, different landscape extents were defined in terms of buffers around each BBS route in order to evaluate the effect of changes in scale. This was done by first creating buffers of 50 m, 100 m, 500 m, 1,000 m, 2,500 m and 5,000 m around each BBS route on the digitised BBS route layer, then overlaying the buffer layer onto the land use/cover layer to create a new layer showing land use/cover classes (patches) within each buffer (extent). This layer was used to measure the aforementioned landscape metrics in each buffered landscape. The landscape metrics were calculated with Patch Analyst.

After the 12 landscape metrics were measured for each buffered landscape, correlation analyses were conducted at each buffer size (landscape extent) to determine how the landscape metrics were correlated with each other. The results showed that at the four smallest extents (50 m, 100 m, 500 m and 1,000 m buffers), mean patch size of forest, number of forest patches and per cent urban area were the least correlated, while mean patch fractal dimension of forest, total edge of forest and per cent urban area had the lowest correlations at the two