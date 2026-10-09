for the true log odds ratio and true odds ratio.

# 2.2.5 The Logit Function and Entropy

**PRB-24 CH.PRB- 2.21.**
The entropy (see *Chapter 4*) of a *single binary outcome* with probability *p* to receive *1* is defined as:

H(p) = -p log p - (1 - p) log(1 - p). (2.7)

*At what* p *does* H(p) *attain its maximum value?*

*What is the relationship between the entropy* H(p) *and the logit* function, *given* p ?

# 2.2.6 Python/PyTorch/CPP

**PRB-25 CH.PRB- 2.22.**
The following C++ code (Fig. 2.7) is part of a *(very basic)* *logistic regression implementation module*. For a *theoretical discussion* *underlying this question*, refer to problem 2.17.

```
1 #include ... 
2 std: vector< double > theta {-6,0,0.5, 1.0};
3 double sigmoid (double x) {
4 double tmp=1.0/(1.0+ exp(- x));
5 std:: cout << "prob="<< tmp<< std:: endl;
6 return tmp;
7 }
8 double hypothesis (std:: vector< double > x){
9 double z;
0 z=std:: inner_product(std:: begin(x), std:: end(x),
1 std:: begin(theta), 0.0 );
```