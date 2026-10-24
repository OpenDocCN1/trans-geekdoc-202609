```
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
for i = 1:3 plaintext1 = plaintext(:,:,i);
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
```