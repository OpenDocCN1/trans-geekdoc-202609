$$e^x \approx E_x(x) \approx 2^{1.44x} \tag{8.26}$$

*Based on this formulation, one can calculate the sigmoid function as:*

$$\text{Sigmoid }(x) \approx \frac{1}{1+2^{-1.44x}} \approx \frac{1}{1+2^{-1.5x}} \tag{8.27}$$

*1 Code snippet 8.21 provides a pure C++ based (e.g. not using Autograd, implementation of the forward pass for the Sigmoid function. Implement the backward pass that directly computes the analytical gradients in C++ using Libtorch [ 19 ] style tensors .*

```
```
1 #include <torch/script.h>
2 #include <vector>
3 
4 torch:: Tensor sigmoid001(const torch:: Tensor &x) {
5 	torch:: Tensor sig = 1.0 / (1.0 + torch:: exp(- x));
6 	return sig;
7 }
```
```

FIGURE 8.21: Forward pass for the Sigmoid function using Libtorch

*2 Code snippet 8.22 provides a skeleton for printing the values of the sigmoid and its derivative for a range of values contained in the vector v. Complete the code (lines 7-8) so that the values are printed .*

```
```
1 #include <torch/script.h>
2 #include <vector>
3 int main() {
4 	std:: vector<float> v{0.0, 0.1, 0.2, 0.3,
5 			0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 0.99};
6 	for (auto it = v.begin(); it != v.end(); ++ it) {
7 		torch:: Tensor t0 = torch:: tensor(* it);
8 		...
9 	}
10 }
```
```