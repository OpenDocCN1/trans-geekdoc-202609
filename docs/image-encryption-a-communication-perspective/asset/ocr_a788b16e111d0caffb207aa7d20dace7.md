```
for j = 1:cols
    mat(i,j,loc) = mat(pr(i,j),pc(i,j),loc-1);
end
end
end
out = mat(:,:,num+1);

function ID = IDMF(x,y)
%this fuunction(irregular Deviation Measuring Factor) is based on how much the deviation cased by encryption is
%irregular.
%x:-Original Image
%y:-Encrypted Image
%D:-Maximum Deviation Measuring Factor
x = double(x);
y = double(y);
%first,calculate the difference between each pixel value before and after
%encryption
D = uint8(abs(x-y));
%calculate the H histogram of the difference
H = imhist(D)
%calculate the average of H
DC = 0;
for i = 1:256
    DC = DC+H(i);
end
DC = DC/256;
%subtract the DC from H at every point
for i = 1:256
    AC(i) = abs(H(i)-DC);
end
%calculate the sum of AC
ID = 0;
for i = 1:256
    ID = ID+AC(i);
End;
%the lower the value, the better the encryption

function D = MDMF(x,y)
%this fuunction calculates the Maximum Deviation
    Measuring Factor which
%calculates the deviation between the original and
    encrypted image.
```