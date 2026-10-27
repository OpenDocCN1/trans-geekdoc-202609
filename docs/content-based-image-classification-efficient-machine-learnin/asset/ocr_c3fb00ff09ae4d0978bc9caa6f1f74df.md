```
```matlab
r=i(:,:,1); #red component
[m n p]=size(i1); #dimension of red component
g=i(:,:,2); #green component
[x y z]=size(i3); #dimension of green component
b=i(:,:,3); #blue component
[j k l]=size(i6); #dimension of blue component
#Flipping the color components
flp_r = fliplr(r);
flp_g = fliplr(g);
flp_b = fliplr(b);
#Creating Even and Odd varieties of each component
r_evn = (r + flp_r)/2;
g_evn = (g + flp_g)/2;
b_evn = (b + flp_b)/2;
r_odd = (r - flp_r)/2;
g_odd = (g - flp_g)/2;
b_odd = (b - flp_b)/2;
```
```

# 4.10 Coding Exercise

*The previous code example is for generating odd and even varieties of test images. Refer to the example to complete the following assignments:*

+   - Extract features from odd and even varieties of images using mean threshold selection.
+   - Test classification results for each variety.

Hereafter, calculation of average values for diverse metrics is carried out to observe Precision, Recall, MR and F1-Score for classification with four different classifiers—namely, KNN, RIDOR, ANN, and SVM—from four different public datasets using features extracted with mean threshold selection from Original + Even Image variety (Table 4.3).

# 4.11 Feature Extraction with Static and Dynamic Ternary Image Maps Using Mean Threshold Selection

This section deals with extraction of feature vectors with ternary image maps following the logic of mean threshold selection [4]. The techniques are known as Static Thepade’s Ternary BTC (STTBTC) and Dynamic Thepade’s