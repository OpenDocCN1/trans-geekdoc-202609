```
# Patches extraction
otbcli_PatchesExtraction \
-source1.il Sentinel-2_B4328_10m.tif \
-source1.patchsizex 16 \
-source1.patchsizey 16 \
-source1.out Sentinel-2_B4328_10m_patches_A.tif \
-vec terrain_truth_epsg32654_A_pos.shp \
-field "class" \
-outlabels Sentinel-2_B4328_10m_labels_A.tif uint8
```

where:

+   - **source1** is the parameter group for the first image source (it cannot be set with value, and only contains parameters),
+   - **source1.il** is the input image list of the first source,
+   - **source1.patchsizex** is the patch width of the first source,
+   - **source1.patchsizey** is the patch height of the first source,
+   - **source1.out** is the output patches image of the first source,
+   - **vec** is the input vector data of the points (samples locations),
+   - **field** is the attribute that we will use as the label value (i.e. the class),
+   - **outlabels** is the output image for the labels.

After this step, you should have generated the following output images, that we will name “the training dataset”:

+   - *Sentinel-2_B4328_10m_patches_A.tif*
+   - *Sentinel-2_B4328_10m_labels_A.tif*

**Visualizing the patches**
A simple trick enables you to check the extracted patches from QGIS: Simply open the patches as a raster, then chose the same coordinate reference system as the current project (indicated on the bottom right of the window).

Repeat the previously described steps for the vector layer *terrain_truth_epsg32654_B_pos.shp* and generate the patches and labels for validation.

```
# Patches extraction
otbcli_PatchesExtraction \
-source1.il Sentinel-2_B4328_10m.tif \
-source1.patchsizex 16 \
-source1.patchsizey 16 \
-source1.out Sentinel-2_B4328_10m_patches_B.tif \
-vec terrain_truth_epsg32654_B_pos.shp \
-field "class" \
-outlabels Sentinel-2_B4328_10m_labels_B.tif uint8
```