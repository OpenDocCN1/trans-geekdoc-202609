+   3. `patches_train_s2_2019-07-25.tif`
+   4. `patches_train_s2_2019-08-24.tif`

Repeat the same operation for the validation dataset, as shown in the following command line.

```
```bash
export OTB_TF_NSOURCES=4
otbcli_PatchesExtraction \\
–vec patches_centroids_valid.gpkg \\
–source1.il sar_vh_hh_log_norm_EPSG32630.tif \\
–source1.patchsize 64 –source1.patchsizey 64 \\
–source1.out patches_valid_s1.tif \\
–source2.il Sentinel2_2019-07-05_10m.tif \\
–source2.patchsize 64 –source2.patchsizey 64 \\
–source2.out patches_valid_s2_2019-07-05.tif \\
–source3.il Sentinel2_2019-07-25_10m.tif \\
–source3.patchsize 64 –source3.patchsizey 64 \\
–source3.out patches_valid_s2_2019-07-25.tif \\
–source4.il Sentinel2_2019-08-24_10m.tif \\
–source4.patchsize 64 –source4.patchsizey 64 \\
–source4.out patches_valid_s2_2019-08-24.tif \\
–field "id"
```
```

The **PatchesExtraction** application has created 4 new files that constitute the validation dataset:

+   1. `patches_valid_s1.tif`
+   2. `patches_valid_s2_2019-07-05.tif`
+   3. `patches_valid_s2_2019-07-25.tif`
+   4. `patches_valid_s2_2019-08-24.tif`

# 16.3 More: automate steps with the OTB Python API

In this section, we provide insight on the use of the Python API of the Orfeo ToolBox. This section is, however, optional, and can be skipped since it only shows how to automate the steps previously performed to prepare the patches. The Python API enables you to connect in-memory OTB applications in preserving the so-called streaming mechanism (see 2.1.2). OTB applications can be instantiated as Python objects and their parameters can be set using the same key/value identifiers: once an OTB application object is instantiated, its parameter values can be set using dedicated methods. All parameters that can be set in an OTB application are settable in the Python instance (e.g. integer, float or double precision numbers, strings, images, images lists, vector data, etc.). Hence, it is quite straightforward to implement an entire pipeline that implies multiple OTB applications chained together: we instantiate