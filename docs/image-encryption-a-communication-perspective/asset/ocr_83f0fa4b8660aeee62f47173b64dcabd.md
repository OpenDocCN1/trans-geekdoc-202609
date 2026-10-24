```
%serial to parallel conversion ...............................
paradata = reshape(serdata,para,nd*m1);
%QPSK modulation ...................................................
[ich,qch] = qpskmod(paradata,para,nd,m1);
% [ich0,qch0] = compoversamp(ich01,qch01,length
(ich01),Ipoint);
kmod = 1/sqrt(2);
ich1 = ich.*kmod;
qch1 = qch.*kmod;
%IDCT ............................................................
x = ich1 + qch1.*j;
y = idct(x);

CR = 4;
clipping_threshold = (10^(CR/10))*sqrt(mean(ab
s(y).^2));
tx_signal_Ang = angle(y);

for ii = 1: length(y)
if y(ii) = = y(ii);
y(ii) = y(ii);

elseif abs(y(ii)).^2> clipping_threshold
y(ii) = clipping_threshold.*exp(sqrt(-1)*tx_
signal_Ang(ii));

end
end
%companding .......................................................
u = 4;

tx_lfdma_max = max(abs(y(1: nd*para)));
tx_lfdma_Abs = abs(y(1: nd*para)); % tx data
amplitude

TxSamples_lfdma1 = tx_lfdma_max*((log10(1+u*
(tx_lfdma_Abs./tx_lfdma_
max)))/log10(u+1)).*sign(y
(1: nd*para));

tx_ifdma_max = max(abs(y(1: nd*para)));
tx_ifdma_Abs = abs(y(1: nd*para)); % tx data
amplitude
```