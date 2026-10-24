```
RC5enctextRC5(i,:) = RC5enctext;

end;
xa = uint8(RC5enctextRC5(:));

function xa = RC5EncCFBImage(x,key,r,CO)
%Encrypt Image using RC5 in CFB mode
[m,n] = size(x);
y = double(x); keyi = RC5keygen(key,r);
plaintext1 = reshape(y',8,m*n/8)';

RC5enctextRC5 = zeros(m*n/8,8);
for i = 1:m*n/8 plaintext = plaintext1(i,:); if i ==1
cr1 = RC5enc(CO,r,keyi);

RC5enctext = bitxor(plaintext,cr1);
else cr1 = RC5enc(RC5enctext,r,keyi);

RC5enctext = bitxor(plaintext,cr1);
end;

RC5enctextRC5(i,:) = RC5enctext;

end; ya = reshape(RC5enctextRC5',n,m)';
xa = uint8(ya);

function xa = RC5EncCFBImageC(x,key,r,CO)
%Encrypt Colored Image using RC5 in CFB mode
x1 = x(:,:,1); x2 = x(:,:,2); x3 = x(:,:,3);
y1 = double(x1); y2 = double(x2);
y3 = double(x3); [m,n] = size(x1);

keyi = RC5keygen(key,r);
plaintext(:,:,1) = reshape(y1',8,m*n/8)';
plaintext(:,:,2) = reshape(y2',8,m*n/8)';
plaintext(:,:,3) = reshape(y3',8,m*n/8)';

RC5enctext = x;
% CFB
for i = 1:3 plaintext1 = plaintext(:,:,i);
RC5enctextRC5 = RC5CFB(plaintext1,m,n,CO,r,keyi);
RC5enctextRC5 = reshape(RC5enctextRC5',n,m)';
RC5enctext(:,:,i) = RC5enctextRC5;
end; xa = uint8(RC5enctext);
```