
```matlab
%Image with no Encryption + OFDM + offset + zero padding + over estimated channel........
%Transmitter ...........................................................
%Data Generation ...........................................................
%Transmitter ...........................................................
%Data Generation ...........................................................
f = imread('Cameraman.tif');
[M,N] = size(f);
g1 = im2col(f, [M,N], [M,N], 'distinct');
h1 = dec2bin(double(g1));
[M1,N1] = size(h1);
z1 = zeros (M1,N1);
for i = 1: M1
for j = 1: N1
z1(i,j) = str2num(h1(i,j));
end;
end;
[R1,T1] = size(z1);
zz1 = reshape(z1,R1*T1, 1);
% The transmitted data ...............................................
zz = [zz1];

%ENCODING ...............................................................
    trel = poly2trellis(7,[171 133]);% Trellis
    data1 = zz;
    zz = convenc(data1,trel);
s1 = length(zz);
para = 128;
nd = 6; %number of information OFDM symbol for one loop
m1 = 2; %Modulation level: QPSK
sr = 250000; %symbol rate
br = sr.*m1; %Bit rate per carrier
Ipoint = 8;%Number of over samples
gilen = 32;
flat = 1;
fd = 600;

    fftlen = para;
    noc = para;
    ofdm_length = para*nd*m1; %Total no for one loop

%Dividing the image into blocks .........................................

nloops = ceil((length(zz))/ofdm_length);

new_data = nloops*ofdm_length ;
nzeros = new_data - length(zz);
input_data = [zz;zeros(nzeros,1)];
input_data2 = reshape(input_data,ofdm_length,nloops);

%Transmission ON FFT_OFDM ............................................
    for ebno = [0,2,4,6,8,10];

demodata1 = zeros(ofdm_length,nloops);
for jj = 1: nloops % loop for columns
    serdata = input_data2(:,jj)';
    demodata = fft_channel_estimation_no_mapping_zg(serdata,para,nd,m1,gilen,fftlen,sr,ebno,br,fd,flat);
    demodata1(:,jj) = demodata(:); % the output of ofdm columns

end

%Received image ............................................
[Mr,Nr] = size(demodata1);
% demodata2 = demodata1(:);
yy = reshape (demodata1,Mr*Nr,1);% 
part1 = yy(1: s1);
yy11 = part1;
%DECODING ............................................
    yy11 = vitdec(yy11',trel,1,'term','hard');% Decode.

yy1 = reshape(yy11, [R1,T1]);
for i = 1: M1
for j = 1: N1
zn1(i,j) = num2str(yy1(i,j));
end;
end;
hnl = bin2dec(zn1);
gn1 = col2im(hnl, [M,N], [M,N], 'distinct');
%The Error between Trans ...................................
output_image = gn1/255;

output_image1 = medfilt2(output_image);

%The Error between Trans ....................................
MSE1 = sum(sum((double(f)/255-output_image).^2))/prod(size(f));
PSNR = 10*log(1/MSE1)/log(10)

MSE11 = sum(sum((double(f)/255-output_image1).^2))/prod(size(f));
PSNR1= 10*log(1/MSE11)/log(10);

end

%Transmission ON DCT_OFDM ........................

for ebno = [0,2,4,6,8,10];

demodata1 = zeros(ofdm_length,nloops);
for jj = 1: nloops % loop for columns
    serdata = input_data2(:,jj)';
    demodata = dct_channel_estimation_no_mapping_zg(serdata,para,nd,m1,gilen,fftlen,sr,ebno,br,fd,flat);
    demodata1(:,jj) = demodata(:,1); % the output of ofdm columns

end

%Received image ..................................
 [Mr,Nr] = size(demodata1);
% demodata2 = demodata1(:);
YY = reshape (demodata1,Mr*Nr,1);%
part1 = YY(1: s1);
yy1 = part1;
%DECODING .........................................
YY11 = vitdec(yy1',trel,1,'term','hard');% Decode.

yy1 = reshape(YY11,[M1,N1]);
for i = 1: M1
for j = 1: N1
zn1(i,j) = num2str(yy1(i,j));
end;
end;
hn1 = bin2dec(zn1);
qn1 = col2im(hn1, [M,N], [M,N], 'distinct');
%The Error between Trans ..........................
output_image = gn1/255;

output_image1 = medfilt2(output_image);

%The Error between Trans ...............................
    MSE1 = sum(sum((double(f)/255-output_image).^2))/prod(size(f));
    PSNR = 10*log(1/MSE1)/log(10)

    MSE11 = sum(sum((double(f)/255-output_image1).^2))/prod(size(f));
    PSNR1 = 10*log(1/MSE11)/log(10);

    end

    %Transmission ON DWT_OFDM ...........................

    for ebno = [0,2,4,6,8,10];

    demodata1 = zeros(ofdm_length,nloops);
    for jj = 1: nloops % loop for columns
        serdata = input_data2(:,jj);
        demodata = dwt_channel_estimation_no_mapping_zg(serdata,para,nd,m1,gilen,fftlen,sr,ebno,br,fd,flat);
        demodata1(:,jj) = demodata(:); % the output of ofdm columns

    end

    %Received image ......................................
    [Mr,Nr] = size(demodata1);
    % demodata2 = demodata1(:);
    yy = reshape (demodata1,Mr*Nr,1);%
    part1 = yy(1: s1);
    yy11 = part1;
    %DECODING ...........................................
    yy11 = vitdec(yy11,trel,1,'term','hard');% Decode.

    yy1 = reshape(yy11 ,[R1,T1]);
    for i = 1: M1
    for j = 1: N1
    zn1(i,j) = num2str(yy1(i,j));
    end;
    end
    end;
    hnl = bin2dec(zn1);
    gnl = col2im(hnl, [M,N], [M,N], 'distinct');
    %The Error between Trans ...........................
        output_image = gn1/255;

    output_image1 = medfilt2(output_image);

    %The Error between Trans ...........................
       MSE1 = sum(sum((double(f)/255-output_image).^2))/prod(size(f));
    PSNR = 10*log(1/MSE1)/log(10)

       MSE11 = sum(sum((double(f)/255-output_image1).^2))/prod(size(f));
    PSNR1 = 10*log(1/MSE11)/log(10);

    end

%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
function Outdemodata = fft_channel(serdata,para,nd,m1,gilen,fftlen,sr,ebno,br)

%serial to parallel conversion ...........................
paradata = reshape(serdata,para,nd*m1);
%QPSK modulation ..........................................
[ich,qch] = qpskmod(paradata,para,nd,m1);
% [ich0,qch0] = compoversamp(ich01,qch01,length(ich01),Ipoint);
kmod = 1/sqrt(2);
ich1 = ich.*kmod;
qch1 = qch.*kmod;
%IFFT .....................................................
x = ich1 + qch1.*j;
y = ifft(x);
ich2 = real (y);
qch2 = imag (y);

%Guard Interval insertion ...............................

[ich3,qch3] = gins(ich2,qch2,fftlen,gilen,nd);
fftlen2 = fftlen + gilen;

%Attenuation Calculation ................................
spow = sum(ich3 .^2+qch3 .^2)/nd./para;
attn = 0.5*spow*sr/br*10.^(-ebno/10);
attn = sqrt (attn);

%Receiver ................................................
%AWGN addition ...........................................

    [ich4,qch4] = comb(ich3,qch3,attn);

%Guard interval removal ..................................
    [ich5,qch5] = girem (ich4,qch4,fftlen2,gilen,nd);
%FFT ......................................................
rx = ich5 - qch5.*j;
ry = fft(rx);
ich6 = real (ry);
qch6 = imag (ry);

%Demodulation ............................................
    ich7 = ich6./kmod;
    qch7 = qch6./kmod;
outdemodata = qpskdemod (ich7,qch7,para,nd,m1);

function outdemodata = dct_channel(serdata,para,nd,m1,gilen,dctlen,sr,ebno,br)

%serial to parallel conversion ..........................

paradata = reshape(serdata,para,nd*m1);
%QPSK modulation .........................................
[ich,qch] = qpskmod(paradata,para,nd,m1);
% [ich0,qch0] = compoversamp(ich01,qch01,length(ich01),Ipoint);
kmod = 1/sqrt (2);
ich1 = ich.*kmod;
qch1 = qch.*kmod;
%DCT .....................................................
x = ich1 + qch1.*j;
y = idct(x);
ich2 = real (y);
qch2 = imag (y);

%Guard interval insertion ................................

[ich3,qch3] = giins(ich2,qch2,dctlen,gilen,nd);
dctlen2 = dctlen + gilen;

%Attenuation Calculation ...............................................

spow = sum(ich3.^2+qch3.^2)/nd./para;
attn = 0.5*spow*sr/br*10.^ (-ebno/10);
attn = sqrt (attn);

%Receiver .............................................................

%AWGN addition .......................................................

[ich4,qch4] = comb(ich3,qch3,attn);

%Guard interval removal ...............................................
[ich5,qch5] = girem (ich4,qch4,dctlen2,gilen,nd);
%DWT ...............................................................
rx = ich5 + qch5.*j;
ry = wavelet('D6',1,rx,'zpd'); % 2D wavelet transform
% R = wavelet('2D CDF 9/7',-2,Y); % Recover X from Y;
ich6 = real (ry);
qch6 = imag (ry);

%Demodulation .........................................................
ich7 = ich6./kmod;
qch7 = qch6./kmod;
outdemodata = qpskdemod (ich7,qch7,para,nd,m1);

function outdemodata = fft_channel_clipping_companding(serdata,para,nd,m1,gilen,fftlen,sr,ebno,br)

paradata = reshape(serdata,para,nd*m1);
%QPSK modulation .......................................................
[ich,qch] = qpskmod(paradata,para,nd,m1);
% [ich0,qch0] = compoversamp(ich01,qch01,length(ich01),Ipoint);

kmod = 1/sqrt(2);
ich1 = ich.*kmod;
```
