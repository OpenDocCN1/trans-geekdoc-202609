```
RC6enctextRC6 = reshape(RC6enctextRC6',n,m)';
RC6enctext(:, :, i) = RC6enctextRC6;
end;
xa = uint8(RC6enctext);

function [xa, Fs, nbits] = RC6EncCFBAudio(x, Fs, nbits,key,r,CO)
%Encrypt Audio using RC6 in CFB mode

L = length(x);
y = double(x);
keyi = RC6keygen(key,r);
plaintext1 = reshape(y,L/16,16);
RC6enctextRC6 = zeros(L/16,16);
% CFB
for i = 1:L/16
    plaintext = plaintext1(i,:);
    if i ==1
        cr1 = RC6enc(CO,r,keyi);
        RC6enctext = bitxor(plaintext,cr1);
    else
        cr1 = RC6enc(RC6enctext,r,keyi);
        RC6enctext = bitxor(plaintext,cr1);
    end;
    RC6enctextRC6(i,:) = RC6enctext;
end;
xa = uint8(RC6enctextRC6(:));

function xa = RC6EncCFBImage(x,key,r,CO)
%Encrypt Image using RC6 in CFB mode
[m,n] = size(x);
y = double(x);
keyi = RC6keygen(key,r);
plaintext1 = reshape(y',16,m*n/16)';
RC6enctextRC6 = zeros(m*n/16,16);
% CFB
for i = 1:m*n/16
    plaintext = plaintext1(i,:);
    if i ==1
```