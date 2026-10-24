
DESenctextDES(i,:) = DESenctext;

end;

function plaintextDES = DESECBDec(DESenctext1,m,n,r,
    keyi)
%Decrypt data using DES in ECB mode

plaintextDES = zeros(m*n/8,8);
for i = 1:m*n/8
    DESenctextss = DESenctext1(i,:);
    re_plaintext = decry(DESenctextss,r,keyi);
    plaintextDES(i,:) = re_plaintext;
end;

function [xa,Fs,nbits] = DesEncCBC Audio(x,Fs,nbits,
    key,r,CO)
%Encrypt Audio using DES in CBC mode

L = length(x);
y = double(x);
keyi = DESkeygen(key,r);
plaintext1 = reshape(y,L/8,8);
ciphertextDES = zeros(L/8,8);
    %CBC
for i = 1:L/8
    plaintext = plaintext1(i,:);
    if i == 1
        plaintexts = bitxor(plaintext,CO);
    else
        plaintexts = bitxor(plaintext,ciphertext);
    end;
    ciphertext = cipher(plaintexts,r,keyi);
    ciphertextDES(i,:) = ciphertext;
end;
xa = uint8(ciphertextDES(:));

function xa = DesEncCBCImage(x,key,r,CO)
%Encrypt Image using DES in CBC mode
[m,n] = size(x);
y = double(x);
keyi = DESkeygen(key,r);
plaintext1 = reshape(y',8,m*n/8)';
ciphertextDES = zeros(m*n/8,8);
%CBC
for i = 1:m*n/8
    plaintext = plaintext1(i,:);
    if i == 1
        plaintexts = bitxor(plaintext,CO);
    else
        plaintexts = bitxor(plaintext,ciphertext);
    end;
    ciphertext = cipher(plaintexts,r,keyi);
    ciphertextDES(i,:) = ciphertext;
end;
ya = reshape(ciphertextDES',n,m)';
xa = uint8(ya);

function xa = DesEncCBCImageC(x,key,r,CO)
%Encrypt Colored Image using DES in CBC mode
x1 = x(:,:,1);
x2 = x(:,:,2);
x3 = x(:,:,3);
[m,n] = size(x1);
y1 = double(x1);
y2 = double(x2);
y3 = double(x3);
keyi = DESKeygen(key,r);
plaintext(:,:,1) = reshape(y1',8,m*n/8)';
plaintext(:,:,2) = reshape(y2',8,m*n/8)';
plaintext(:,:,3) = reshape(y3',8,m*n/8)';
DESentext = x;
%CBC
for i = 1:3
    plaintext1 = plaintext(:,:,i);
    DESentextDES = DESCBC(plaintext1,m,n,CO,r,keyi);
    DESentextDES = reshape(DESentextDES',n,m)';
    DESentext(:,:,i) = DESentextDES;
end;
xa = uint8(DESentext);

function [xa,Fs,nbits] = DesEncCFBAudio(x,Fs,nbits,key,
    r,CO)
%Encrypt Audio using DES in CFB mode
L = length(x);
y = double(x);
keyi = DESKeygen(key,r);
plaintext1 = reshape(y,L/8,8);
ciphertextDES = zeros(L/8,8);
% CFB
for i = 1:L/8
    plaintext = plaintext1(i,:);
    if i ==1
        cr1 = cipher(CO,r,keyi);
        ciphertext = bitxor(plaintext,cr1);
    else
        cr1 = cipher(ciphertext,r,keyi);
        ciphertext = bitxor(plaintext,cr1);
    end;
    ciphertextDES(i,:) = ciphertext;
end;
xa = uint8(ciphertextDES(:));

function xa = DesEncCFBImage(x,key,r,CO)
%Encrypt Image using DES in CFB mode
[m,n] = size(x);
y = double(x);
keyi = DESkeygen(key,r);
plaintext1 = reshape(y',8,m*n/8)';
ciphertextDES = zeros(m*n/8,8);
% CFB
for i = 1:m*n/8
    plaintext = plaintext1(i,:);
    if i ==1
        cr1 = cipher(CO,r,keyi);
        ciphertext = bitxor(plaintext,cr1);
    else
        cr1 = cipher(ciphertext,r,keyi);
        ciphertext = bitxor(plaintext,cr1);
    end;
    ciphertextDES(i,:) = ciphertext;
end;
ya = reshape(ciphertextDES',n,m)';
xa = uint8(ya);

function xa = DesEncCFBImageC(x,key,r,CO)
%Encrypt Colored Image using DES in CFB mode

x1 = x(:,:,1); x2 = x(:,:,2); x3 = x(:,:,3);
[m,n] = size(x1); y1 = double(x1);
y2 = double(x2); y3 = double(x3);
keyi = DESkeygen(key,r);
plaintext(:,:,1) = reshape(y1',8,m*n/8)';
plaintext(:,:,2) = reshape(y2',8,m*n/8)';
plaintext(:,:,3) = reshape(y3',8,m*n/8)';
DESencrypt = x;
% CFB
for i = 1:3
    plaintext1 = plaintext(:,:,i);
    DESencryptDES = DESCFB(plaintext1,m,n,CO,r,keyi);
    DESencryptDES = reshape(DESencryptDES',n,m)';
    DESencrypt(:,:,i) = DESencryptDES;
end;
xa = uint8(DESencrypt);

function [xa,Fs,nbits] = DesEncECBAudio(x,Fs,nbits,key,r)
%Encrypt Audio using DES in ECB mode
L = length(x);
y = double(x); keyi = DESkeygen(key,r);
plaintext1 = reshape(y,L/8,8);
ciphertextDES = zeros(L/8,8);
% ECB
for i = 1:L/8
    plaintext = plaintext1(i,:);
    ciphertext = cipher(plaintext,r,keyi);
    ciphertextDES(i,:) = ciphertext;
end;
xa = uint8(ciphertextDES(:));

function xa = DesEncECBImage(x,key,r)
%Encrypt Image using DES in ECB mode
[m,n] = size(x);
y = double(x); keyi = DESkeygen(key,r);
plaintext1 = reshape(y',8,m*n/8)';
ciphertextDES = zeros(m*n/8,8);
% ECB
for i = 1:m*n/8
    plaintext = plaintext1(i,:);
    ciphertext = cipher(plaintext,r,keyi);
    ciphertextDES(i,:) = ciphertext;
end;
ya = reshape(ciphertextDES',n,m)'; xa = uint8(ya);

function xa = DesEncECBImageC(x,key,r)
%Encrypt Colored Image using DES in ECB mode
x1 = x(:,:,1); x2 = x(:,:,2); x3 = x(:,:,3);
[m,n] = size(x1); y1 = double(x1);
y2 = double(x2);
y3 = double(x3); keyi = DESkeygen(key,r);
plaintext(:,:,1) = reshape(y1',8,m*n/8)';
plaintext(:,:,2) = reshape(y2',8,m*n/8)';
plaintext(:,:,3) = reshape(y3',8,m*n/8)';
DESencText = x;

for i = 1:3
    plaintext1 = plaintext(:,:,i);
    DESencTextDES = DESECB(plaintext1,m,n,r,keyi);
    DESencTextDES = reshape(DESencTextDES',n,m)';
    DESencText(:,:,i) = DESencTextDES;
end;
xa = uint8(DESencText);

function [xa,Fs,nbits] = DesEncOFBAudio(x,Fs,nbits,...
        key,r,CO)
%Encrypt Audio using DES in OFB mode
L = length(x);
y = double(x); keyi = DESkeygen(key,r);
plaintext1 = reshape(y,L/8,8);
ciphertextDES = zeros(L/8,8);
% OFB
for i = 1:L/8
    plaintext = plaintext1(i,:);
    if i == 1
        cr = cipher(CO,r,keyi);
    else
        cr = cipher(cr,r,keyi);
    end;
    ciphertext = bitxor(plaintext,cr);
    ciphertextDES(i,:) = ciphertext;
end;
xa = uint8(ciphertextDES(:));

function xa = DesEncOFBImage(x,key,r,CO)
%Encrypt Image using DES in OFB mode

[m,n] = size(x);
y = double(x); keyi = DESkeygen(key,r);
plaintext1 = reshape(y',8,m*n/8)';
ciphertextDES = zeros(m*n/8,8);
% OFB
for i = 1:m*n/8
    plaintext = plaintext1(i,:);
    if i == 1
        cr = cipher(CO,r,keyi);
    else
        cr = cipher(cr,r,keyi);
    end;
    ciphertext = bitxor(plaintext,cr);
    ciphertextDES(i,:) = ciphertext;
end;
ya = reshape(ciphertextDES',n,m)'; xa = uint8(ya);

function xa = DesEncOFBImageC(x,key,r,CO)
%Encrypt Colored Image using DES in OFB mode

x1 = x(:,:,1);
x2 = x(:,:,2);
x3 = x(:,:,3);
[m,n] = size(x1);
y1 = double(x1);
y2 = double(x2);
y3 = double(x3);
keyi = DESkeygen(key,r);
plaintext(:,:,1) = reshape(y1',8,m*n/8)';
plaintext(:,:,2) = reshape(y2',8,m*n/8)';
plaintext(:,:,3) = reshape(y3',8,m*n/8)';
DESenctext = x;
% OFB
for i = 1:3
    plaintext1 = plaintext(:,:,i);
    DESenctextDES = DESOFB(plaintext1,m,n,CO,r,keyi);
    DESenctextDES = reshape(DESenctextDES',n,m)';
    DESenctext(:,:,i) = DESenctextDES;
end;
xa = uint8(DESenctext);

function key1 = DESkeygen(Mainkey,r)
%DES Key Generation
% Inserting master key
% clc
% clear all

% Mainkey = ['A';'A';'B';'B';'0';'9';'1';'8';'2';'7';'
            '3';'6';'C';'C';'D';'D'];
key2 = Convert256toHex(Mainkey);
key = zeros(r,4); for i = 1:r
key(i,:) = dec2binvecA(key2(i),4); end
key = rot90(key);
key = key(:);

a = [57 49 41 33 25 17 9 1 58 50 42 34 26 18 10 2 59
    51 43 35 27 19 11 3 60 52 44 36 63 55 47 39 31
    23 15 7 62 54 46 38 30 22 14 6 61 53 45 37 29 21
    13 5 28 20 12 4];
b = [14 17 11 24 1 5 3 28 15 6 21 10 23 19 12 4 26 8
    16 7 27 20 13 2 41 52 31 37 47 55 30 40 51 45 33
    48 44 49 39 56 34 53 46 42 50 36 29 32];
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
output1 = key(a);
key1 = zeros(r,48);
left = output1(28:-1:1);
right = output1(56:-1:29);
for i = 1:r
left = shiftleft(left,i);
right = shiftleft(right,i);
output(28:-1:1) = left;
output(56:-1:29) = right;
key1(i,:) = output(b);
end

function ciphertextDES = DESOFB(plaintext1,m,n,CO,r,keyi)
%Encrypt data using DES in OFB mode

ciphertextDES = zeros(m*n/8,8);
for i = 1:m*n/8
plaintext = plaintext1(i,:);

if i == 1
cr = cipher(CO,r,keyi);

else
cr = cipher(cr,r,keyi);

end;
ciphertext = bitxor(plaintext,cr);
ciphertextDES(i,:) = ciphertext;

end;

function plaintextDES = DESOFBDec(ciphertext1,m,n,CO,r,keyi)
%Decrypt data using DES in OFB mode

plaintextDES = zeros(m*n/8,8);
for i = 1:m*n/8
ciphertextss = ciphertext1(i,:);
if i ==1
cr = cipher(CO,r,keyi);
re_plaintext = bitxor(ciphertextss,cr);
else
cr = cipher(cr,r,keyi);
re_plaintext = bitxor(ciphertextss,cr);
end;

plaintextDES(i,:) = re_plaintext;

end;
