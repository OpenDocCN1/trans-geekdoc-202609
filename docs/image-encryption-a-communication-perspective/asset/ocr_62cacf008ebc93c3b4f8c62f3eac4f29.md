```
plaintextRC6(i,:) = re_plaintext;

end;

function y = RC6dec(plaintext,round,s)
% RC6 Decryption
a = plaintext(1:4); b = plaintext(5:8);
c = plaintext(9:12); d = plaintext(13:16);
c = RC6sub(c,s(2*round+4,:));
a = RC6sub(a,s(2*round+3,:)); for i = round:-1:1
    temp = d; d = c; c = b; b = a;
    a = temp;
    u = multi(d,(2*d+1)); u = shifting(u,5);
    t = multi(b,(2*b+1)); t = shifting(t,5);
    c = RC6sub(c,s(2*i+2,:)); c = shifting
    (c,-LSB5(t)); c = bitxor(c,u);
    a = RC6sub(a,s(2*i+1,:)); a = shifting
    (a,-LSB5(u)); a = bitxor(a,t);
end d = RC6sub(d,s(2,:));
b = RC6sub(b,s(1,:)); y(1:4) = a;
y(5:8) = b; y(9:12) = c; y(13:16) = d;

function [xa1,Fs,nbits] = RC6DecCBCAudio(x1, Fs,
nbits,key,r,CO)

%Decrypt Audio using rc6 in CBC mode
%CBC keyi = RC6keygen(key,r); L = length(x1);
y1 = double(x1); y1 = reshape(y1,L/16,16);
plaintextRC6 = zeros(L/16,16);
for i = 1:L/16
    RC6enctextss = y1(i,:);
    re_plaintext = RC6dec(RC6enctextss,r,keyi);
    if i ==1
        plaintext = bitxor(re_plaintext,CO);
    else
        plaintext = bitxor(re_plaintext,y1((i-1),:));
    end;
    plaintextRC6(i,:) = plaintext; end;
xa1 = uint8(plaintextRC6(:));

function xa1 = RC6DecCBCImage(x1,key,r,CO)
%Decrypt Image using RC6 in CBC mode

keyi = RC6keygen(key,r);
```