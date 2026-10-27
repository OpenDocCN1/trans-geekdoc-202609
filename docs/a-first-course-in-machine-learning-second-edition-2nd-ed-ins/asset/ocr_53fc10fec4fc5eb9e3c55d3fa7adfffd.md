```
8 mu0 = 0;
9 ss0 = 1;
10
11 % Component variance
12 ss = 1;
13
14 % Number of components
15 K = 2;
16
17
18 nSamps = 1000;
19
20 % Parameters for the prior Dirichlet
21 alp = repmat(1,K,1);
22 prk = gamrnd(alp,1);
23 prk = prk./sum(prk);
24
25 Z = zeros(N,K);
26
27 % Structures to hold the output
28 allZZ = zeros(N);
29 allMu = zeros(nSamps,K);
30 allPrk = zeros(nSamps,K);
31
32 % Outer loop to run multiple chains for computing Rhat
33 nChain = 5;
34 samps = zeros(nSamps,nChain);
35 for chain = 1:nChain
36     % Randomly initialise the means
37     mu = randn(K,1).*sqrt(ss0) + mu0;
38
39
40     for s = 1:nSamps
41         % Update the Z
42         for n = 1:N
43             like = -0.5*(x(n) - mu).^2;
44             like = like + log(prk);
45             prob = exp(like - max(like));
46             prob = prob./sum(prob);
47             pos = find(rand<=cumsum(prob),1);
48             Z(n,:) = 0;
49             Z(n,pos) = 1;
50         end
51
52         % Update the mu
53
54         for k = 1:K
55             ssk = 1/(1/ss0 + sum(Z(:,k)));
56             muk = ssk * (mu0/ss0 + sum(Z(:,k).*x));
57             mu(k) = randn*sqrt(ssk) + muk;
58         end
59
60         % Update the prior
61
62         prk = gamrnd(alp + sum(Z,1)',1);
63         prk = prk./sum(prk);
64
65         allPrk(s,:) = prk';
66         allMu(s,:) = mu';
```