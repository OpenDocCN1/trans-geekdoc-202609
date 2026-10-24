```
function cipherdes1' = cipher(plaindes1,r,keyi)
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%this file for the encryption of the plaintext to a
ciphertext using des
% clc
% clear all bin = zeros(8);
for i = 1:8
    bin(i,:) = dec2binvecA(plaindes1(i),8);
end;
plaindes = rot90(bin);
plaindes = plaindes(:);
ip = InitialPermutation(plaindes);
left = ip(1:32);
right = ip(33:64);
for round = 1:r
    expansion = .expl(right);
    xor_one = bitxor(expansion',keyi(round,:));
    substitution = DESsub(xor_one);
    permutation = p(substitution);
    xor_two = bitxor(left,permutation);
    if round ~= r left = right;
        right = xor_two;
    else
        left = xor_two;
    end;
end;
y(1:32) = left; y(33:64) = right;

cipherdesBIN1 = finalpermutation(y);

cipherdesBIN1 = reshape(cipherdesBIN1,8,8)';
cipherdes1 = zeros(1,8);
for i = 1:8
    cipherdes1(i) = binvec2decA(cipherdesBIN1
    (i,end:-1:1));
end;
```

```
function y = Convert256toHex(x)
%convert 256 base numbers to Hex.
a = length(x);
j = 1;
y = zeros(1,2*a);
for i = 1:a
```