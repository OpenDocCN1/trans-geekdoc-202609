```
qch6 = imag (ry);

%Demodulation ...........................................

ich7 = ich6./kmod;
qch7 = qch6./kmod;
outdemodata = qpskdemod (ich7,qch7,para,nd,m1);

function outdemodata = dwt_channel_clipping_companding
(serdata,para,nd,m1,gilen,dctlen,sr,ebno, br)

%serial to parallel conversion ...............................

paradata = reshape(serdata,para,nd*m1);
%QPSK modulation .............................................
[ich,qch] = qpskmod(paradata,para,nd,m1);
% [ich0,qch0] = compoversamp(ich01,qch01,length
    (ich01),Ipoint);
kmod = 1/sqrt(2);
ich1 = ich.*kmod;
qch1 = qch.*kmod;
%IDWT .........................................................
x = ich1 + qch1.*j;
y = wavelet('D6',-1,x,'zpd'); % Invert 5 stages
%; % 2D wavelet transform
% R = wavelet('2D CDF 9/7',-2,Y); % Recover X from Y%
Forward transform with 5 stages
CR = 4;
    clipping_threshold = (10^(CR/10))*sqrt(mean(ab
        s(y).^2));
    tx_signal_Ang = angle(y);
    for ii = 1: length(y)
    if y(ii) = = y(ii);
        y(ii) = y(ii);
    elseif abs(y(ii)).^2> clipping_threshold
        y(ii) = clipping_threshold.*exp(sqrt
            (-1)*tx_signal_Ang(ii));
    end
end
%companding ...............................................
u = 4;
```