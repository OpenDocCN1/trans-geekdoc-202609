```
zz = convenc(data1,trel);
s1 = length(zz);
para = 128;
nd = 6; %number of information OFDM symbol for one loop
ml = 2; %Modulation level: QPSK
sr = 250000; %symbol rate
br = sr.*ml; %Bit rat per carrier
Ipoint = 8;%Number of over samples
gilen = 32;
flat = 1;
fd = 600;

dctlen = para;
noc = para;
ofdm_length = para*nd*ml; %Total no for one loop

%Dividing the image into blocks ............................
nloops = ceil((length(zz))/ofdm_length);
new_data = nloops*ofdm_length ;
nzeros = new_data - length(zz);
input_data = [zz;zeros(nzeros,1)];
input_data2 = reshape(input_data,ofdm_length,nloops);

%Transmission ON FFT_OFDM ...............................
for ebno = [0,2,4,6,8,10];

demodata1 = zeros(ofdm_length,nloops);
for jj = 1: nloops % loop for columns
serdata1 = input_data2(:,jj)';
demodata = fft_channel_clipping_companding(serdata1,para,nd,ml,gilen,dctlen,sr,ebno,br);
demodata1(:,jj) = demodata(:, ); % the output of ofdm columns
end

%Received image .......................................
[Mr,Nr] = size(demodata1);
% demodata2 = demodata1(: );
yy = reshape (demodata1,Mr*Nr,1);%
part1 = yy(1: s1);
yy11 = part1;
```