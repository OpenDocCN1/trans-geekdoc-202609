# A Concise Introduction to Machine Learning

```
else
priorlambda = LAMBDA(1);-
# Run once on the Cholesky factorization to
# preserve positive definiteness.
update = sqrt (LAMBDA(1)/priorlambda) + (v' - M(:,l));
PSI(:,l) = choldupate(PSI(:,l),update,'-');
M(l,l) = LAMBDA(1)*M(:,l) + v(l,:)/priorlambda;
NU(l) = NU(l-1);
LAMBDA(l) = priorlambda;
SIGMA(:,l) = iwishrnd(PSI(:,l),*PSI(:,l),NU(l));
MU(:,l) = mvnrnd(M(:,l),SIGMA(:,l),LAMBDA(l));
# Calculate cluster probabilities.
p = priorlambda;
for k=1:K
p(k) = nk(k)/(N-1-alpha)*mvnpdf(v',MU(:,k),SIGMA(:,k));
pp(K+1) = (N-1-alpha)*mvnpdf(v',m,PSI)
p = sum(p)
# Sample new indicator variable.
l = randample(K,1,true,p);
idx = l;
if l
# Update the cluster sample is now assigned to.
postlambda = LAMBDA(l+1);
# Run once on the Cholesky factorization to
# preserve positive definiteness.
update = sqrt (LAMBDA(l)/postlambda) + (v' - M(:,l));
PSI(:,l) = choldupate(PSI(:,l),update,'-');
M(l,l) = LAMBDA(l)*M(:,l) + v(l,:)/postlambda;
NU(l) = NU(l-1);
LAMBDA(l) = postlambda;
SIGMA(:,l) = iwishrnd(PSI(:,l),*PSI(:,l),NU(l));
M(:,l) = mvnrnd(M(:,l),SIGMA(:,l),LAMBDA(l));
nk = nk+1;
else
# Create new cluster.
LAMBDA = cat(2,LAMBDA,lambda+1);
update = sqrt (LAMBDA(1)/(lambda+1)) + (v' - m);
PSI = cat(3,PSI,choldupate(PSI,update,'+'));
M = cat(2,M,lambda*m + v'/(lambda+1));
SIGMA = cat(3,SIGMA,iwishrnd(PSI(:,1),* ...
PSI(:,1),NU(1));
MU = cat(2,MU,mvnrnd(M(:,1),SIGMA(:,1),LAMBDA(1)));
nk = cat(2,nk,1);
X = K+1;
end
```

List 6.7: Dirichlet process method in MATLAB. For Python to go https://github.com/ACFaul/Clustering-Python.