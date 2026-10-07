% and estimated pathloss (l) given a specified SNR (in dB) and amplitude
% of an interference signal

```
Ns = 1000;           % size of data
K = 64;               % size of known sequence (in bits)
sps = 8;               % number of samples per symbol
fd = 1;                % symbol rate
fs = sps*fd;            % sample rate
rc_alpha = 0.35;     % raised cosine filter rolloff
```

% Create training sequence
train = randint(1,K)
train_mod = pskmod(train, 2)
t = rcosflft(train_mod, fd, fs, 'fir/sqrt', rc_alpha)

% Create source signal including the training sequence
xs = [randint(1, N), train, randint(1, N)]
xs_mod = pskmod(xs, 2)
s = rcosflft(xs_mod, fd, fs, 'fir/sqrt', rc_alpha)

% Create interference signal
xi = randint(length(xs), 1)
xi_mod = pskmod(xi, 4)
i = iamp*rcosflft(xi_mod, fd, fs, 'fir/sqrt', 0.25)

% Received signal is sum of source, interference, and noise
r = awgn(s + i, SNR, 'measured')
r = 0.1*r; % crude pathloss

```
% Autocorrelate training sequence to get max correlation value
autocor = xcorr(t,t)
autocor = ceil(length(autocor)/2) : length(autocor);
[mauto, indauto] = max(autocor);
```

```
% Correlate against known training sequence and find peak
sigcor = xcorr(r, t)
sigcor = sigcor(ceil(length(sigcor)/2) : length(sigcor))
sigcor = abs(sigcor)
[m,ind] = max(sigcor);
```

% Use crosscorrelation and autocorrelation of training sequence