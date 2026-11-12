
## PROGRAM 3.2 IMPLEMENTATION OF THE BILINEAR TRANSFORMATION IN MATLAB

```matlab
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%Program that implements the bilinear transformation
%from a set of transformation points
%considering the unit square
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%Definition of transformation points
%The unit square method is considered to be used.
x1=100;
y1=80;
x2=500;
y2=70;
x3=100;
y3=350;
x4=10;
y4=10;
%Determination of parameters a and b.
a1=x2-x1;
a2=x4-x1;
a3=x1-x2+x3-x4;
a4=x1;
b1=y2-y1;
b2=y4-y1;
b3=y1-y2+y3-y4;
b4=y1;
%Get the size of the image
Im = imread("fotos/paisaje.jpg") ;
Im = rgb2gray(Im) ;
[m n]=size(Im) ;
%Each of the points of the result image is set to black,
%this is because there will be values of the result image
% that do not have a corresponding value in the original
% image.
I1=zeros(size(Im)) ;
%All pixels of the transformed image are traversed
for re=1:m
   for co=1:n
   %The coordinates of the original image
   %correspond to points on the unit square so
   %they are divided between m and n
      rel=re/m;
      col=co/n;
   %Get the values of the transformed image
      x=round(a1*col+a2*rel+a3*rel*col+a4) ;
      y=round(b1*col+b2*rel+b3*rel*col+b4) ;
   %It is protected for pixel values that due to
%the transformation do not have a corresponding
    if ((x>=1) || (x<=n) || (y>=1) || (y<=m))
    I1(y,x)=Im(re,co) ;
    end
end
end
%Convert the image to a data type
I1=uint8(I1) ;
%The image is displayed
imshow(I1)
```

add interesting effects and distortions to images. The following three examples make extensive use of the reverse formulation of the transformation:

Depending on the type of transformation in question, the inverse formulation is not always easy, although for practical purposes on many occasions (using the source-origin transformation technique) inversion is not necessary.

## 3.1.6.1 The Twirl Transformation

The Twirl transformation produces an \(\alpha\) rotation of the image about the rotation point \(\boldsymbol{x}_c = (x_c, y_c)\), this rotation decreases as the distance of the image pixel from the rotation point increases. The geometric transformation produced on the image only has an effect within a certain radius \(r_{max}\) of distortion, so outside of it, the image remains unchanged [6]. The inverse formulation of this transformation is defined as follows:

where:

dx = x' - x_c

dy = y' - y_c

![](img/fa2d7e8bd88af7122f764c748b0a3723_130_0.png)

FIGURE 3.10
Different nonlinear transformations. (a) and (b) Twirl transformation, (c) and (d) Ripple transformation, and (e) and (f) spherical distortion.

\[
r = \sqrt{d_x^2 + d_y^2}
\]
\[
\beta = atan2(d_y, d_x) + \alpha \cdot \left( \frac{r_{max}-r}{r_{max}} \right) \tag{3.38}
\]

Figure 3.10a and d show two examples of the Twirl transformation, considering the center of the image as the point of rotation \(\mathbf{x}_c\), \(r_{max}\) as half the main diagonal of the image, and the angle of rotation \(\alpha = 28^\circ\).

## 3.1.6.2 The Twirl Transformation in MATLAB

This section presents how to implement the Twirl transformation in MATLAB. The implementation methodology uses the inverse formulation of the transformation; that is, it starts by finding the correspondence of the transformed values with those of the original. This is convenient since the transformation itself, according to Equations 3.36 and 3.37, is expressed in terms of the inverse formulation. The code for this implementation is shown in Program 3.3, considering as the point of rotation \(\mathbf{x}_c\) the center of the image, \(r_{max}\) as half the main diagonal of the image, and the angle of rotation \(\alpha = 28^\circ\).

## PROGRAM 3.3 IMPLEMENTATION OF THE TWIRL TRANSFORMATION IN MATLAB

```matlab
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%Program that implements the Twirl transformation
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Im=imread("fotos/paisaje.jpg")
Im = rgb2gray(Im) ;
imshow(Im)
figure
%Get the size of the image
[m n]=size(Im) ;
%The center of rotation is defined
as the center of the image
xc=n/2;
yc=m/2;
%The angle of rotation is defined approx. 28 degrees
%1 rad
alfa=1;
%rmax is defined
rmax=sqrt (xc*xc+yc*yc) ;
%Convert the image to double to avoid numerical problems
Imd=double (Im) ;
%The resulting image is filled with zeros in such a way
% where there are no geometric correspondences,
% the value of the pixels will be zero.
II=zeros (size (Im) ) ;
%All pixels of the transformed image are traversed
for re=1:m
for co=1:n
%The values defined in 3.34 are obtained
dx=co-xc;
dy=re-yc;
r=sqrt (dx*dx+dy*dy) ;
%The transformations of
%Equations 3.33-3.34 are calculated
if (r<=rmax)
Beta=atan2 (dy,dx)+alfa*...
((rmax-r)/rmax) ;
xf=round (xc+r*cos (Beta) ) ;
yf=round (yc+r*sin (Beta) ) ;
else
xf=co;
yf=re;
end
%It is protected for pixel values that due to
%the transformation do not have a corresponding
   if ( (xf>1) && (xf<n) && (yf>1) && (yf<m) )
      II(re,co)=Imd(yf,xf) ;
   end
end
end
II=uint8(II) ;
imshow(II)
```

## 3.1.6.3 The Ripple Transformation

The Ripple transform produces a local waveform distortion in the $x$ or $y$ direction. The parameters of this transformation are the periods of the wavelength $\tau_x$ and $\tau_y$ that are defined in each of the directions and the displacement amplitudes in each direction, defined by the parameters $a_x$ and $a_y$ [6]. The inverse formulation of this transformation is defined as follows:

\(T_x^{-1} : x = x' + a_x \cdot \text{sin} \left( \frac{2\pi y'}{\tau_x} \right)\)
\(T_y^{-1} : y = y' + a_y \cdot \text{sin} \left( \frac{2\pi x'}{\tau_y} \right)\)
(3.39)

Figure 3.10b and e shows two examples of the Ripple transformation, considering $\tau_x = 120$ and $\tau_y = 250$, as well as $a_x = 10$ and $a_y = 12$.

## 3.1.6.4 The Ripple Transformation in MATLAB

This section presents how to implement the Ripple transformation in MATLAB. The implementation methodology uses the inverse formulation of the transformation; that is, it starts by finding the correspondence of the transformed values with those of the originals. This is convenient since the transformation itself, according to Equation 3.39, is expressed in terms of the inverse formulation. The code for this implementation is shown in Program 3.4, considering $\tau_x = 120$ and $\tau_y = 250$, also $a_x = 10$ and $a_y = 10$.

## 3.1.6.5 Spherical Distortion

Spherical distortion produces an effect similar to that of a sphere-shaped lens. The parameters for performing this transformation are the center of the lens $\mathbf{x}_c = (x_c, y_c)$, the maximum distortion radius $r_{\text{max}}$ and the lens index $\lambda\rho$ [6]. The inverse formulation of this transformation is defined as follows:

## PROGRAM 3.4 IMPLEMENTATION OF THE RIPPLE TRANSFORMATION IN MATLAB

```matlab
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%Program that implements the Ripple transformation
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
Im=imread("fotos\paisaje.jpg")
Im = rgb2gray(Im);
imshow(Im)
figure
%Get the size of the image
[m n]=size(Im) ;
%The periods of the wavelength are defined
tx=120;
ty=250;
%Displacements of each of the directions
ax=10;
ay=12;
%Convert the image to double to avoid
%numerical problems
Imd=double(Im) ;
%The resulting image is filled with zeros in such a way
% that where there are no geometric correspondences,
% the value of the pixels will be zero.
I1=zeros(size(Im)) ;
%All pixels of the transformed image are traversed
for re=1:m
    for co=1:n
    %The transformations of Eq. 3.36 are calculated
    Angulo1=sin(( 2*pi*re)/tx);
    Angulo2=sin(( 2*pi*co)/ty);
    xf=round(co+ax*Angulo1) ;
    yf=round(re+ay*Angulo2) ;
    %It is protected for pixel values that due to the
    %transformation do not have a corresponding
    if ( (xf>=1)&&(xf<=n)&&(yf>=1)&&(yf<=m) )
    I1(re,co)=Imd(yf,xf) ;
    end
    end
end
I1=uint8( I1) ;
imshow(I1) ;
```
