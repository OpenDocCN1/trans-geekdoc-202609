# PROGRAM 6.1 IMAGE COMPRESSION USING SVD DECOMPOSITION

```
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%
%% Program to calculate the SVD decomposition
%% for image compression proposes.
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%
%%
%% Erik Cuevas, Alma Rodríguez
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%
%%Acquire the image
Im=imread('I1.jpeg');
%%Convert the image to grayscale
I1=rgb2gray(Im);
%%Convert image to floating point
X=double(I1);
%%Get SVD components
[U,S,V]=svd(X);
%%The truncation point is defined
r=15;
%%The approximate data matrix is obtained with only r=15
elements
Xapprox15 = U(:,1:r)*S(1:r,1:r)*V(:,1:r) ';
%%Converts the data array to integer
IR15=mat2gray(Xapprox);
%%The image is shown
imshow(IR15)
r=50;
%%The approximate data matrix is obtained with only r=50
elements
Xapprox50 = U(:,1:r)*S(1:r,1:r)*V(:,1:r) ';
%%Converts the data array to integer
IR50=mat2gray(Xapprox50);
figure;
%%The image is shown
imshow(IR50)
r=100;
%%The approximate data matrix is obtained with only r=15
elements
Xapprox100 = U(:,1:r)*S(1:r,1:r)*V(:,1:r) ';
%%Converts the data array to integer
IR100=mat2gray(Xapprox100);
figure;
%%The image is shown
imshow(IR100)
```