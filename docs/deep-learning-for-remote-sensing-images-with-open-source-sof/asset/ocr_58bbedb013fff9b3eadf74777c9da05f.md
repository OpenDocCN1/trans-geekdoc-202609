Enter the following expression in **BandMathX** to process the first image of the Sentinel-2 time series:

```
# Normalize the Sentinel-2 image from 2019/07/05

# Go in Sentinel-2 images (10m)
cd ~/marmande
cd S2A_MSIL2A_20190705T105031_N0212_R051_T30TYQ_20190705T140734.SAFE
cd GRANULE/L2A_T30TYQ_A021069_20190705T105032/IMG_DATA/R10m

# Concatenate images, and normalise them between [0,1]
otbcli_BandMathX \
-il T30TYQ_20190705T105031_B04_10m.jp2 \
    T30TYQ_20190705T105031_B03_10m.jp2 \
    T30TYQ_20190705T105031_B02_10m.jp2 \
    T30TYQ_20190705T105031_B08_10m.jp2 \
-exp "{0.00012207*im1b1;0.00012207*im2b1;\
0.00012207*im3b1;0.00012207*im4b1}" \
-out ~/marmande/Sentinel2_2019-07-05_10m.tif

# Go back in the workspace
cd ~/marmande
```

Repeat the operation on the two next Sentinel-2 images. First, apply **BandMathX** to the _S2A_MSIL2A_20190725T105031_N0213_R051_T30TYQ_20190725T141902_ product, which corresponds to _S2<sub>t</sub>_:

```
# Normalize the Sentinel-2 image from 2019/07/25
cd ~/marmande
cd S2A_MSIL2A_20190725T105031_N0213_R051_T30TYQ_20190725T141902.SAFE
cd GRANULE/L2A_T30TYQ_A021355_20190725T105702/IMG_DATA/R10m
otbcli_BandMathX \
-il T30TYQ_20190725T105031_B04_10m.jp2 \
    T30TYQ_20190725T105031_B03_10m.jp2 \
    T30TYQ_20190725T105031_B02_10m.jp2 \
    T30TYQ_20190725T105031_B08_10m.jp2 \
-exp "{0.00012207*im1b1;0.00012207*im2b1;\
0.00012207*im3b1;0.00012207*im4b1}" \
-out ~/marmande/Sentinel2_2019-07-25_10m.tif
cd ~/marmande
```

Then, apply it to the _S2A_MSIL2A_20190824T105031_N0213_R051_T30TYQ_20190824T134703_ product, which corresponds to _S2<sub>t+1</sub>_:

```
# Normalize the Sentinel-2 image from 2019/08/24
cd ~/marmande
cd S2A_MSIL2A_20190824T105031_N0213_R051_T30TYQ_20190824T134703.SAFE
cd GRANULE/L2A_T30TYQ_A021784_20190824T105344/IMG_DATA/R10m
otbcli_BandMathX \
-il T30TYQ_20190824T105031_B04_10m.jp2 \
    T30TYQ_20190824T105031_B03_10m.jp2 \
    T30TYQ_20190824T105031_B02_10m.jp2 \
    T30TYQ_20190824T105031_B08_10m.jp2 \
-exp "{0.00012207*im1b1;0.00012207*im2b1;\
0.00012207*im3b1;0.00012207*im4b1}" \
-out ~/marmande/Sentinel2_2019-08-24_10m.tif
cd ~/marmande
```