```
```python
estimated_gradient)/(np.abs(backprop_gradient) +
np.abs(estimated_gradient))
# If the error is to large fail the gradient check
if relative_error &amp;gt; error_threshold:
    print &quot;Gradient Check ERROR: parameter=%s
    ix=%s&quot; % (pname, ix)
    print &quot;+h Loss: %f&quot; % gradplus
    print &quot;-h Loss: %f&quot; % gradminus
    print &quot;Estimated_gradient: %f&quot; %
    estimated_gradient
    print &quot;Backpropagation gradient: %f&quot; %
    backprop_gradient
    print &quot;Relative Error: %f&quot; % relative_error
    return
it.iternext()
print &quot;Gradient check for parameter %s passed&quot; %
(pname)
```
```

```
```python
RNNNumpy.gradient_check = gradient_check
grad_check_vocab_size = 100
np.random.seed(10)
model = RNNNumpy(grad_check_vocab_size, 10, bptt_truncate=1000)
model.gradient_check([0,1,2,3], [1,2,3,4])
```
```