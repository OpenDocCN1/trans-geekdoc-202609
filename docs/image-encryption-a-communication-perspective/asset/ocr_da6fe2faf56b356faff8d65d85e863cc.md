```
% Z-power.

% [X,PHI1] = WAVELET(W,'phi1') returns an
% approximation of the
% scaling function associated with wavelet transform W.
% [X,PHI1] = WAVELET(W,'phi1',N) approximates the
% scaling function
% with resolution 2^-N. Similarly,
% [X,PSI1] = WAVELET(W,'psi1',...),
% [X,PHI2] = WAVELET(W,'phi2',...),
% and [X,PSI2] = WAVELET(W,'psi2',...) return
% approximations of the
% wavelet function, dual scaling function, and dual
% wavelet function.

% Wavelet transforms are implemented using the lifting
% scheme [4].
% For general background on wavelets, see for example
% [6] .

% Examples:

% % Display information about the S+P (4,4) wavelet
% wavelet('S+P (4,4)') ;

% % Plot a wavelet decomposition
% t = linspace(0,1,256);
% X = exp(-t) + sqrt(t - 0.3).*(t > 0.3) - 0.2*
% (t > 0.6);
% wavelet('RSpline 3.1',3,X); % Plot the decomposition
% of X

% % Sym4 with periodic boundaries
% Y = wavelet('Sym4',5,X,'per'); % Forward transform
% with 5 stages
% R = wavelet('Sym4',-5,Y,'per'); % Invert 5 stages

% % 2D transform on an image
% t = linspace(-1,1,128); [x,y] = meshgrid(t,t);
% X = ((x+1).*(x-1) - (y+1).*(y-1)) + real(sqrt(0.4 -
% x.^2 - y.^2));
% Y = wavelet('2D CDF 9/7',2,X); % 2D wavelet transform
% R = wavelet('2D CDF 9/7',-2,Y); % Recover X from Y
% imagesc(abs(Y).^0.2); colormap(gray); axis image;
%
```