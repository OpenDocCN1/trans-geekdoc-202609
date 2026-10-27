```
gam = 10.0;
N = length(x);
K = zeros(N);

% Create the kernel matrix
for n = 1:N
    for m = 1:N
        K(n,m) = exp(-gam*(x(n)-x(m))^2);
    end
end

K = K + 1e-6*eye(N);
% Generate a sample
f.samps = gauss samp(repmat(0,N,1),K,1)

% Add some noise
ss = 0.1;
true.f = f.samps(1,:) + randn(1,N)*sqrt(ss);

true.f = true.f';
x = x';

% Initial hyperparameters
inithyp = [0;0]

% Call optimisation code
hyp = fminunc(@(h) marg.like(h,true.f,x),inithyp)
```

EX 8.4. The function value at the nth data point if f_n. This function is then exponentiated to give the rate of a Poisson λ_n = exp(f_n). The integer count sampled from the Poisson is z_n. The gradient of the log posterior is given by:

$$rac{\delta}{\delta\mathbf{f}} = \mathbf{z} - \exp(\mathbf{f}) - \mathbf{C}^{-1}\mathbf{f}$$ 

$$\frac{\delta^2}{\delta\mathbf{f}\delta\mathbf{f}^T} = -\mathbf{C}^{-1} - \mathbf{E}$$

where E is a matrix with zeros everywhere except the diagonal where the nth diagonal value is exp(f_n). This is demonstrated with the following code:

```
% Generate some data
x = [0:0.01:1];
gam = 10.0;
N = length(x);
C = zeros(N);

% Create the kernel matrix
for n = 1:N
    for m = 1:N
        C(n,m) = exp(-gam*(x(n)-x(m))^2);
    end
end

C = C + 1e-6*eye(N);
```