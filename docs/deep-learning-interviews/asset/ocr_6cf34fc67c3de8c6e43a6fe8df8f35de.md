**SOL-124✏CH.SOL- 5.25. The answers are as follows:**
The code snippet in 5.16 implements the function using Autograd .

```
```
1 from torch.autograd import Function
2 class EQ (Function):
3     @staticmethod
4     def forward (ctx, x1, x2):
5         # save everything to compute the gradient
6         ctx. save_for_backward(x1, x2)
7         return (x1 * x2). abs()
8         @staticmethod
9     def backward (ctx, grad_output):
10        x1, x2 = ctx. saved_tensors
11        return (grad_output * x1. sign() * x2. abs(),\
12        grad_output * x1. abs() * x2. sign())**2
```
```

![](bbox=[0.32, 0.45, 0.7, 0.48])

# 5.3.13 Dual numbers in AD

**SOL-125✏CH.SOL- 5.26.**
*The answers are as follows:*

1 *The procedure of AD is to use verbatim text of a computer program which calculates a numerical value and to transform it into the text of a computer program called the transformed program which calculates the desired derivative values. The transformed computer program carries out these derivative calculations by repeated use of the chain rule however applied to actual floating point values rather than to a symbolic representation .*
2 *Dual numbers extend all numbers by adding a second component x ↦ x + ẋ, where x + ẋ is the dual part .*
3 *The following arithmetic operations are possible on DN:*

(a) d² = 0