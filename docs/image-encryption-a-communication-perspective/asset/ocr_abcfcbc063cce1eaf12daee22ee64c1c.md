```
```matlab
for i = 1:L/8
    RC5entextss = RC5entext1(i,:);
    if i == 1
        cr = RC5enc (CO,r,keyi);
        re_plaintext = bitxor(RC5entextss,cr);
    else
        cr = RC5enc(cr,r,keyi);
        re_plaintext = bitxor(RC5entextss,cr);
    end;

    plaintextRC5(i,:) = re_plaintext;

end;
xa1 = uint8(plaintextRC5(:));

function xa1 = RC5DecOFBImage(x1,key,r,CO)
%Decrypt Image using RC5 in OFB mode.
keyi = RC5keygen(key,r);

[m,n] = size(x1); y1 = double(x1);
plaintextRC5 = zeros(m*n/8,8);
RC5entext1 = reshape(y1',8,m*n/8)';
for i = 1:m*n/8
    RC5entextss = RC5entext1(i,:);
    if i == 1
        cr = RC5enc (CO,r,keyi);
        re_plaintext = bitxor(RC5entextss,cr);
    else
        cr = RC5enc(cr,r,keyi);
        re_plaintext = bitxor(RC5entextss,cr);
    end;

    plaintextRC5(i,:) = re_plaintext;

end;
ya1 = reshape(plaintextRC5',n,m)';

xa1 = uint8(ya1);

function xa1 = RC5DecOFBImage (x,key,r,CO)
%Decrypt Colored Image using RC5 in OFB mode.
keyi = RC5keygen(key,r);
%OFB

x1 = x(:,:,1);
x2 = x(:,:,2);
x3 = x(:,:,3);
```
```