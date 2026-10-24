```
```matlab
%x:-Original Image ^
%y:-Encrypted Image
%D:-Maximum Deviation Measuring Factor
%first,calculate the histogram between the original
    and encrypted image
x1 = imhist(x);
y1 = imhist(y);
%then calculate the difference between the two
diff = abs(y1-x1);
%then calculate D as follows
D1 = 0;
for i = 2:255
D1 = D1+diff(i);
end;
D2 = (diff(1)+diff(255))/2;
D = D1+D2;
function y = psnr(im1,im2)
%Peak Signal to Noise Ratio
MSEa = 0;
[m,n] = size(im1);
im1 = double(im1);
im2 = double(im2);
for i = 1:m
for j = 1:n
x = double(im1(i,j)-im2(i,j));
x1 = x^2/(m*n);
MSEa = MSEa+x1;
end;
end;
MSEa = double(MSEa);
y = 10*log10((255^2)/MSEa);
```
```