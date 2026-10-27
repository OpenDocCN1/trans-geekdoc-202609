```
```matlab
#Separate the color components
r=i(:,:,1); #red component
[m n p]=size(r); #dimension of red component
g=i(:,:,2); #green component
[x y z]=size(g); #dimension of green component
b=i(:,:,3); #blue component
[j k l]=size(b); #dimension of blue component
#Extract bit planes (red component)
for a1=1:m
for a2=1:n
    #extraction of bit planes
    if bitget(uint8(r(a1,a2)),5)==1 || bitget(uint8(r(a1,a2)),6)==1 ||
    bitget(uint8(r(a1,a2)),7)==1 || bitget(uint8(r(a1,a2)),8)==1)
    rt(a1,a2,:)=r(a1,a2);
    end
end
end
```
```

# 4.7 Coding Exercise

The previous code example is for designing feature vectors with bit plane slicing from the Red color component. Refer to the example to complete the following assignments:

+   - Extract bit planes from Green and Blue color components.
+   - Extract feature vectors from each of the color components using mean threshold selection.

Hereafter, calculation of average values for diverse metrics is carried out to observe Precision, Recall, MR and F1-Score for classification with four different classifiers—namely, KNN, RIDOR, ANN and SVM—from four different public datasets (Table 4.2).

# 4.8 Feature Extraction from Even and Odd Image Varieties Using Mean Threshold Selection

This section discusses another example of mean threshold selection for enhancing the robustness of extracted feature vectors with augmented data. The flipped versions of the images are used for data augmentation, which is