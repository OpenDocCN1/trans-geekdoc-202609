```
demodata = zeros(para,m1*nd);
demodata ((1: para), (1: m1 : m1*nd-1)) = 
idat a((1: para), (1: nd)) >= 0;
demodata ((1: para), (2: m1 : m1*nd)) = 
qdata((1: para), (1: nd)) >= 0;

%********************* End of file *********************

function varargout = wavelet(WaveletName,Level,X,Ext,Dim)
%WAVELET Discrete wavelet transform.
% Y = WAVELET(W,L,X) computes the L-stage discrete wavelet transform
% (DWT) of signal X using wavelet W. The length of X must be
% divisible by 2^L. For the inverse transform, WAVELET(W,-L,X)
% inverts L stages. Choices for W are
% 'Haar' Haar
% 'D1','D2','D3','D4','D5','D6' Daubechies'
% 'Sym1','Sym2','Sym3','Sym4','Sym5','Sym6' Symlets
% 'Coif1','Coif2' Coiflets
% 'BCoif1' Coiflet-like [2]
% 'Spline Nr.Nd' (or 'bior Nr.Nd') for Splines
% Nr = 0, Nd = 0,1,2,3,4,5,6,7, or 8
% Nr = 1, Nd = 0,1,3,5, or 7
% Nr = 2, Nd = 0,1,2,4,6, or 8
% Nr = 3, Nd = 0,1,3,5, or 7
% Nr = 4, Nd = 0,1,2,4,6, or 8
% Nr = 5, Nd = 0,1,3, or 5
% 'RSpline Nr.Nd' for the same Nr.Nd pairs Reverse splines
% 'S+P (2,2)','S+P (4,2)','S+P (6,2)', S+P wavelets [3]
% 'S+P (4,4)','S+P (2+2,2)'
% 'TT' "Two-Ten" [5]
% 'LC 5/3','LC 2/6','LC 9/7-M','LC 2/10', Low Complexity [1]
% 'LC 5/11-C','LC 5/11-A','LC 6/14',
% 'LC 13/7-T','LC 13/7-C'
% 'Le Gall 5/3','CDF 9/7' JPEG2000 [7]
% 'V9/3' Visual [8]
% 'Lazy' Lazy wavelet
% Case and spaces are ignored in wavelet names, for example, 'Sym4'
```