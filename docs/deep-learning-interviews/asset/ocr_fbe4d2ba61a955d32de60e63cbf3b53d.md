```
```
1  std:: cout << "inner_product=" << z<< std:: endl;
2  return sigmoid(z);
3  }
4  int classify (std:: vector< double > x){
5    int hypo= hypothesis(x) > 0.5f;
6    std:: cout << "hypo=" << hypo<< std:: endl;
7    return hypo;
8  }
9  int main() {
10    std:: vector< double > x1 {1,40,3.5};
11    classify(x1);
12  }
```
```

FIGURE 2.7: Logistic regression in CPP

+   1 Explain the purpose of line 20 , i.e., $inner\_product$ .
2 Explain the purpose of line 25 , i.e., $hypo(x)>0.5f$ .
3 What does $\theta (theta)$ stand for in line 9?
4 Compile and run the code, you can use:
[https://repl.it/languages/cpp11](https://repl.it/languages/cpp11) to evaluate the code .
What is the output?