# CHAPTER 7. ENCODING BEHAVIORAL DATA

207

timeseries

image representation

X: 5,3,0,-5,4,1,1,2,0
Y: 2,2,0,0,1,0,1,2,0
Z: 3,2,3,2,3,3,1,2,3

| | 1 | 2 | 3 |
|---|---|---|---|n| 5 | -5 | 1 | 1 |
| 3 | 4 | 2 | 2 |
| 0 | 1 | 0 | 0 |
| 2 | 1 | 2 | 2 |
| 3 | 4 | 2 | 3 |
| 0 | 0 | 3 | 3 |

| | 1 | 2 | 3 |
|---|---|---|---|n| 5 | -5 | 1 | 1 |
| 3 | 4 | 2 | 2 |
| 0 | 1 | 0 | 0 |

Figure 7.6: Encoding 3 accelerometer timeseries as an image.

![](bbox=[0.159, 0.253, 0.355, 0.413])

![](bbox=[0.399, 0.253, 0.595, 0.413])

![](bbox=[0.644, 0.253, 0.84, 0.413])

a) jogging b) walking c) sitting

Figure 7.7: Three activities captured with an accelerometer represented as images.

acceleration timeseries can be converted to images. A window size of 100 is defined. Since the sampling rate was 20 Hz it means each window corresponds to 100/20 = 5 seconds. For each window, we have 3 timeseries (x,y,z). We reshape each of them into 10 x 10 matrices by arranging the elements into columns. Then, the three matrices can be stacked to form a 3D image similar to an RGB image. Figure 7.6 shows the process of reshaping 3 timeseries of size 9 into 3 x 3 matrices to generate an RGB-like image.

The script then moves to the next window with no overlap and repeats the process. Actually, the script saves each activity as one line of text. The first 100 elements correspond to the x axis, the next 100 to y, and the remaining to z. Thus each line has 300 values. Finally, the user id and the activity label are added at the end. This format makes it easy to read the file and reconstruct the images later. The resulting file is called images.txt and is already included in the smartphone_activities dataset folder.

The script plot_activity_images.R shows how to read the images.txt file and reconstruct the images so we can plot them. Figure 7.7 shows three different activities plotted as colored images of 10 x 10 pixels. Before generating the plots, the images were normalized between 0 and 1.

We can see that the patterns for 'jogging' look more 'chaotic' compared to the others while the 'sitting' activity looks like a plain solid square. Then, we can use those images to train