```
if i == 2*r+4
    i = 1;
end
end

function RC6enctextRC6 = OFB(plaintext1,m,n,CO,r,keyi)
%Encrypt data using RC6 in OFB mode
RC6enctextRC6 = zeros(m*n/16,16);
for i = 1:m*n/16
    plaintext = plaintext1(i,:);

    if i == 1
        cr = RC6enc(CO,r,keyi);
    else
        cr = RC6enc(cr,r,keyi);
    end;

    RC6enctext = bitxor(plaintext,cr); RC6enctextRC6(i,:)
    = RC6enctext;

end;

function plaintextRC6 = RC6OFBDec(RC6enctext1,m,n,CO,r,
keyi)
%Decrypt data using RC6 in OFB mode
plaintextRC6 = zeros(m*n/16,16);
for i = 1:m*n/16
    RC6enctextss = RC6enctext1(i,:);
    if i ==1
        cr = RC6enc (CO,r,keyi);
        re_plaintext = bitxor(RC6enctextss,cr);
    else
        cr = RC6enc(cr,r,keyi);
        re_plaintext = bitxor(RC6enctextss,cr);
    end;

    plaintextRC6(i,:) = re_plaintext;

end;

function y = RC6sub(x,w)
%z = a-almod 2^32
```