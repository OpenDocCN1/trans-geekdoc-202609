# PROGRAM 3.5 IMPLEMENTATION OF SPHERICAL DISTORTION IN MATLAB

```
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%Program that implements spherical distortion
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Im=imread("fotos/paisaje.jpg")
Im = rgb2gray(Im);
imshow(Im)
figure
%Get the size of the image
[m n]=size(Im);
%The center of the spherical lens is defined as
%the center of the image
xc=n/2;
yc=m/2;
%Define the lens index
ro=1.8;
%rmax is defined
rmax=sqrt(xc*xc+yc*yc);
%Convert the image to double to avoid numerical problems
Imd=double(Im);
%The resulting image is filled with zeros
%In such a way that where there are
%no geometric correspondences,
% the value of the pixels will be zero.
Il=zeros(size(Im));
%All pixels of the transformed image are traversed
for re=1:m
 for co=1:n
%The values defined in 3.37 are obtained
 dx=co-xc;
 dy=re-yc;
 r=sqrt(dx*dx+dy*dy);
 if (r<rmax)
%The transformations of Eq. 3.37 are calculated
 z=sqrt(rmax*rmax-r*r);
 R1=dx/(sqrt(dx*dx+dz*z));
 R2=dy/(sqrt(dy*dy+z*z));
 Bx=(1-(1/ro))*asin(R1);
 By=(1-(1/ro))*asin(R2);
 xf=round(co-z*tan(Bx));
 yf=round(re-z*tan(By));
 else
 xf=co;
 yf=re;
 end
```