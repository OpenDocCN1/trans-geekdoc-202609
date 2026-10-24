

qv = imag((1./(ice1.^2+qce1.^2)).*(ice0+i.*qce0).* (ice1-i.*qce1));
%反向旋转矩阵 ...............................
ieqv1 = [iv iv iv iv iv iv iv];
qeqv1 = [qv qv qv qv qv qv qv];
%反向旋转 ...............................
icomen = real((ich7+i.*qch7).*(ieqv1+i.*qeqv1));
qcompen = imag((ich7+i.*qch7).*(ieqv1+i.*qeqv1));
ich7 = icomen;
qch7 = qcompen;
%信道估计符号去除 .......................
knd = 1;    %已知信道估计OFDM符号数量
ich9 = ich7(:,knd+1: nd+1);
qch9 = qch7(:,knd+1: nd+1);

%解调 .......................................
ich10 = ich9./kmod;
qch10 = qch9./kmod;
outdemodata = qpskdemod (ich10,qch10,para,nd,m1);

function outdemodata = fft_channel_offset_g(serdata,para,nd,m1,gilen,fftlen,sr,ebno, br,epsilon)

%串并转换 ...............................
paradata = reshape(serdata,para,nd*m1);

%QPSK调制 .......................................
[ich,qch] = qpskmod(paradata,para,nd,m1);

% [ich0,qch0] = compoversamp(ich01,qch01,length
(ich01),Ipoint);
kmod = 1/sqrt(2);
ich1 = ich.*kmod;
qch1 = qch.*kmod;

%IFFT .......................................
x = ich1 + qch1.*j;
y = ifft(x);
ich2 = real(y);
qch2 = imag(y);

%保护间隔插入 ...............................
[ich3,qch3] = giins1(ich2,qch2,fftlen,gilen,nd);
fftlen2 = fftlen + gilen;

%IDCT ...................................................
x = ich1 + qch1.*j;
y = idct(x);
ich2 = real (y);
qch2 = imag (y);

%保护间隔插入 ...................................
[ich3,qch3] = giins1(ich2,qch2,fftlen,gilen,nd);
fftlen2 = fftlen + gilen;

%衰减计算 ...................................
spow = sum(ich3.^2+qch3.^2)/nd./para;
attn = 0.5*spow*sr/br*10.^(-ebno/10);
attn = sqrt (attn);

%偏移 ...................................................
n = para/2;
offset = exp(j*2*pi*n*epsilon/para);
i_rx_signal = ich3.*offset;
q_rx_signal = qch3.*offset;
ich3a = i_rx_signal ;
qch3a = q_rx_signal ;

%接收机 ...................................................
%AWGN噪声添加 ...............................................
[ich4,qch4] = comb(ich3a,qch3a,attn);

%保护间隔去除 .....................................
[ich5,qch5] = girem1 (ich4,qch4,fftlen2,gilen,nd);

%DCT ........................................................
rx = ich5 + qch5.*j;
ry = dct(rx);
ich6 = real (ry);
qch6 = imag (ry);

%解调 ...............................................
ich7 = ich6./kmod;
qch7 = qch6./kmod;
outdemodata = qpskdemod (ich7,qch7,para,nd,m1);
function outdemodata = dwt_channel_offset_g(serdata,para,nd,m1,gilen,dctlen,sr,ebno,br,epsilon)

%串并转换 .................................

paradata = reshape(serdata,para,nd*m1);
%QPSK调制 ............................
[ich,qch] = qpskmod(paradata,para,nd,m1);
% [icho,qcho] = compoversamp(icho1,qcho1,length
(icho1),Ipoint);
kmod = 1/sqrt(2);
ich1 = ich.*kmod;
qch1 = qch.*kmod;
%IDWT ........................................
x = ich1 + qch1.*j;
y = wavelet('D6',-1,x,'zpd'); %5级逆变换

% 2D小波变换
% R = wavelet('2D CDF 9/7',-2,Y); % 从Y恢复X%
     5级前向变换
ich2 = real (y);
qch2 = imag (y);

%保护间隔插入 ...................
[ich3,qch3] = giins1(ich2,qch2,dctlen,gilen,nd);
dctlen2 = dctlen + gilen;

%衰减计算 ....................
spow = sum(ich3.^2+qch3.^2)/nd./para;
attn = 0.5*spow*sr/br*10.^(-ebno/10);
attn = sqrt (attn);

%偏移 ......................................
n = para/2;
offset = exp(j*2*pi*n*epsilon/para);
i_rx_signal = ich3.*offset;
q_rx_signal = qch3.*offset;
ich3a = i_rx_signal ;
qch3a = q_rx_signal ;

%接收机 ....................................
%AWGN噪声添加 ................................
    [ich4,qch4] = comb(ich3a,qch3a,attn);
%保护间隔去除 ......................
    [ich5,qch5] = girem1 (ich4,qch4,dctlen2,gilen,nd);
%DWT
rx = ich5 + qch5.*j;
ry = wavelet('D6',1,rx,'zpd'); %2D小波变换
% R = wavelet('2D CDF 9/7',-2,Y); % 从Y恢复X;
ich6 = real (ry);
qch6 = imag (ry);

%解调 .......................................................
ich7 = ich6./kmod;
qch7 = qch6./kmod;
outdemodata = qpskdemod (ich7,qch7,para,nd,m1);

function outdemodata = fft_channel_offset_zg(serdata,para,nd,m1,gilen,fftlen,sr,ebno,br,epsilon)

%串并转换 ...........................................
paradata = reshape(serdata,para,nd*m1);

%QPSK调制 .........................................................
[ich,qch] = qpskmod(paradata,para,nd,m1);

% [ich0,qch0] = compoversamp(ich01,qch01,length
(ich01),Ipoint);
kmod = 1/sqrt(2);
ich1 = ich.*kmod;
qch1 = qch.*kmod;

% IFFT ...............................................................
x = ich1 + qch1.*j;
y = ifft(x);
ich2 = real (y);
qch2 = imag (y);

%保护间隔插入 ...............................................
[ich3,qch3] = giins2(ich2,qch2,fftlen,gilen,nd);
fftlen2 = fftlen + gilen;

%衰减计算 ...............................................
spow = sum(ich3.^2+qch3.^2)/nd./para;
attn = 0.5*spow*sr/br*10.^(-ebno/10);
attn = sqrt (attn);

%偏移 ...............................................................
n = para/2;
offset = exp(j*2*pi*n*epsilon/para);
i_rx_signal = ich3.*offset;
q_rx_signal = qch3.*offset;
ich3a = i_rx_signal ;
qch3a = q_rx_signal ;

%接收机 ................................................
%AWGN噪声添加 ..........................................
[ich4,qch4] = comb(ich3a,qch3a,attn);

%保护间隔去除 .................................
[ich5,qch5] = girem1 (ich4,qch4,fftlen2,gilen,nd);

%FFT .....................................................
rx = ich5 + qch5.*j;
ry = fft(rx);
ich6 = real (ry);
qch6 = imag (ry);

%解调 ............................................
  ich7 = ich6./kmod;
  qch7 = qch6./kmod;
  outdemodata = qpskdemod (ich7,qch7,para,nd,m1);

function outdemodata = dct_channel_offset_zg(serdata,para,nd,m1,gilen,fftlen,sr,ebno,br,epsilon)

%串并转换 ..........................
paradata = reshape(serdata,para,nd*m1);

%QPSK调制 .........................................
[ich,qch] = qpskmod(paradata,para,nd,m1);

% [ich0,qch0] = compoversamp(ich01,qch01,length
                         (ich01),Ipoint);
kmod = 1/sqrt(2);
ich1 = ich.*kmod;
qch1 = qch.*kmod;

%IDCT ....................................................
x = ich1 + qch1.*j;
y = idct(x);
ich2 = real (y);
qch2 = imag (y);

%保护间隔插入 ...............................
[ich3,qch3] = giins2(ich2,qch2,fftlen,gilen,nd);
fftlen2 = fftlen + gilen;

%衰减计算 ................................
spow = sum(ich3.^2+qch3.^2)/nd./para;
attn = 0.5*spow*sr/br*10.^(-ebno/10);
attn = sqrt (attn);

%偏移 ............................................................
n = para/2;
offset = exp(j*2*pi*n*epsilon/para);
i_rx_signal = ich3.*offset;
q_rx_signal = qch3.*offset;
ich3a = i_rx_signal ;
qch3a = q_rx_signal ;

%接收机 ............................................................
%AWGN噪声添加 .......................................................
[ich4,qch4] = comb(ich3a,qch3a,attn);

%保护间隔去除 ...............................................
[ich5,qch5] = girem1 (ich4,qch4,fftlen2,gilen,nd);

%DCT ...............................................................
rx = ich5 + qch5.*j;
ry = dct(rx);
ich6 = real (ry);
qch6 = imag (ry);

%解调 .....................................................
ich7 = ich6./kmod;
qch7 = qch6./kmod;
outdemodata = qpskdemod (ich7,qch7,para,nd,m1);

function outdemodata = dwt_channel_offset_zg(serdata,para,nd,m1,gilen,dctlen,sr,ebno,br,epsilon)

%串并转换 ....................................
paradata = reshape(serdata,para,nd*m1);
%QPSK调制 ...................................................
[ich,qch] = qpskmod(paradata,para,nd,m1);
% [ich0,qch0] = compoversamp (ich01,qch01,length
(ich01),Ipoint);
kmod = 1/sqrt(2);
ich1 = ich.*kmod;
qch1 = qch.*kmod;
%IDWT .............................................................
x = ich1 + qch1.*j;

