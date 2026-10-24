```
for j = 1: N1
zn1(i,j) = num2str(yy1(i,j));
end;
end;
hn1 = bin2dec(zn1);
gn1 = col2im(hn1, [M,N], [M,N], 'distinct');
%The Error between Trans ...............................
    output_image = gn1/255;

output_image1 = medfilt2(output_image);

%The Error between Trans ...............................
    MSE1 = sum(sum((double(f)/255-output_image).^2))/ 
        prod(size(f));
PSNR = 10*log(1/MSE1)/log(10)

    MSE11 = sum(sum((double(f)/255-output_image1).^2))/ 
        prod(size(f));
PSNR1 = 10*log(1/MSE11)/log(10);

    end

%Transmission ON DCT_OFDM ...............................
    for ebno = [0,2,4,6,8,10];

demodata1 = zeros(ofdm_length,nloops);
for jj = 1: nloops % loop for columns
    serdata1 = input_data2(:,jj)';
    demodata = dct_channel(serdata1,para,nd,ml,gilen,f
        ftlen,sr,ebno,br);
    demodata1(:,jj) = demodata(:); % the output of
        ofdm columns
end

%Received image .......................................
    [Mr,Nr] = size(demodata1);
% demodata2 = demodata1(:);
    yy = reshape (demodata1,Mr*N r,1);%
    part1 = yy(1: s1);
yy11 = part1;
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%DECODING ............
yy11 = vitdec(yy11',t rel,1,'term','hard');% Decode.

yy1 = reshape(yy11,[R1,T1]);
```