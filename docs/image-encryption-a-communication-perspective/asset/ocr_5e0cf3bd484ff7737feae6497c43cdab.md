```
```matlab
flat = 1;
fd = 600;
epsilon = 0.1;
        fftlen = para;
        noc = para;
        ofdm_length = para*nd*m1; %Total no for one loop

%Dividing the image into blocks .......................
nloops = ceil((length(zz))/ofdm_length);
new_data = nloops*ofdm_length;
nzeros = new_data - length(zz);
input_data = [zz;zeros(nzeros,1)];
input_data2 = reshape(input_data,ofdm_length,nloops);

%Transmission ON FFT OFDM ............................

        for ebno = [0,2,4,6,8,10];

demodatal = zeros(ofdm_length,nloops);
for jj = 1:nloops % loop for columns
    serdata = input_data2(:,jj)';
    demodata = fft_channel_offset_zg(serdata,para,
                nd,m1,gilen,fftlen,sr,ebno,
                br,epsilon);
    demodata1(:,jj) = demodata(:); % the
                                      output of ofdm
                                      columns

end

%Received image ............................
[Mr,Nr] = size(demodata1);
% demodata2 = demodata1(:);
yy = reshape (demodata1,Mr*Nr,1);%
part1 = yy(1: s1);
yy11 = part1;
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%DECODING ...........
yy11 = vitdec(yy11',trel,1,'term','hard');% Decode.

yy1 = reshape(yy11,[R1,T1]);
for i = 1: M1
for j = 1: N1
zn1(i,j) = num2str(yy1(i,j));
end;
end;
```
```