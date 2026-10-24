```
NumStages = size(Seq,1);
EvenStages = ~rem(NumStages,2);

if Flag1D % 1D Transfrom
%%% Convert N-D array to a 2-D array with dimension
Dim along the columns%%%
XSize = size(X); % Save original dimensions
N = XSize(Dim);
M = prod(XSize)/N;
Perm = [Dim: max(length(XSize),Dim),1: Dim-1];
X = double(reshape(permute(X,Perm),N,M));
if M == 1 & nargout == 0 & Level > 0
% Create a figure of the wavelet decomposition
set(gcf,'NextPlot','replace');
subplot(Level+2,1,1);
plot(X);
title('Wavelet Decomposition');
axis tight; axis off;

X = feval(mfilename,WaveletName,Level,X,Ext,1);

for i = 1: Level
N2 = N;
N = 0.5*N;
subplot(Level+2,1,i+1);
a = max(abs(X(N+1: N2)))*1.1;
plot(N+1: N2,X(N+1: N2),'b-');
ylabel(['d',sprintf('_ %c',num2str(i))]);
axis([N+1,N2,-a,a]);
end

subplot(Level+2,1,Level+2);
plot(X(1: N),'-');
xlabel('Coefficient Index');
ylabel('s_1');
axis tight;
set(gcf,'NextPlot','replacechildren');
varargout = {X};
return;
end

if rem(N,pow2(abs(Level))) , error('Signal length
must be divisible by 2^L.'); end

if N < pow2(abs(Level)), error('Signal length
too small for transform level.'); end
```