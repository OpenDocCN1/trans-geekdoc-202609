
```python
model = torch.nn.Linear(10, 5)

# Define the loss function

loss_fn = torch.nn.MSELoss()

# Define the optimizer - still using SGD

optimizer = torch.optim.SGD(model.parameters(),
	lr=0.01)

# Example data

input = torch.randn(100, 10)
target = torch.randn(100, 5)

# Define the batch size

batch_size = 10

# Training loop
```
```
for i in range(100):
    for j in range(0, input.shape[0], batch_size):
        # Compute the predicted output
        output = model(input[j:j+batch_size])
        # Compute the loss
        loss = loss_fn(output, target[j:j+batch_size])
        # Zero the gradients
        optimizer.zero_grad()
        # Compute the gradients
        loss.backward()
        # Update the parameters
        optimizer.step()
```

In the above demonstration, the loop over j steps in increments of batch_size, taking a slice of the input data and the target data for each mini-batch. In practice, you would also want to shuffle the input data at the start of each epoch to ensure the model doesn't learn anything from the order of the samples.

## Momentum

Momentum, a concept borrowed from physics, has been cleverly applied in the realm of optimization algorithms to accelerate the learning process. The idea behind momentum is simple: an object in motion tends to maintain its trajectory unless acted upon by an external force. This principle is applied to the optimization process in machine learning to guide the optimizer effectively, ensuring smoother and quicker convergence towards the global minimum of the loss function.

Within the context of optimization, momentum functions by carrying forward a fraction of the update vector from the previous time step to the current one. This mechanism assists the optimizer in moving along relevant directions more effectively, thereby mitigating unnecessary oscillations. The momentum term effectively serves as a memory of the previous gradients, helping to guide the optimization process by dampening rapid changes in gradient directions. Momentum can be a potent tool in optimization, especially in scenarios marked by high curvature, small but consistent gradients, or noisy gradients. High curvature can lead to rapid changes in gradient direction, causing the optimization process to oscillate wildly and potentially miss the optimum. A small but consistent gradient can lead to a slow convergence towards the optimum. Noise can introduce randomness, making it harder for the optimizer to find the optimum.

In each of these cases, momentum can help significantly. It increases the update for dimensions whose gradients point consistently in the same direction, accelerating convergence in these dimensions. At the same time, it reduces updates in dimensions where the gradients frequently change direction, helping to dampen oscillations. This dual action helps make the trajectory of the optimizer more direct and less prone to oscillations, leading to faster convergence and potentially better solutions.

### Using Momentum with SGD

Adding momentum to our SGD optimizer in PyTorch is as simple as adding an extra argument when we instantiate the optimizer.

We will see how this looks in practice:

```
# Define a simple linear model
model = torch.nn.Linear(10, 5)

# Define the loss function
loss_fn = torch.nn.MSELoss()

# Define the optimizer - SGD with momentum
optimizer = torch.optim.SGD(model.parameters(),
lr=0.01, momentum=0.9)

# Example data
input = torch.randn(100, 10)

target = torch.randn(100, 5)
```
```
# Define the batch size

batch_size = 10

# Training loop

for i in range(100):

    for j in range(0, input.shape[0], batch_size):

        # Compute the predicted output

        output = model(input[j:j+batch_size])

        # Compute the loss

        loss = loss_fn(output, target[j:j+batch_size])

        # Zero the gradients

        optimizer.zero_grad()

        # Compute the gradients
```
```
loss.backward()

# Update the parameters

optimizer.step()
```

In the above example, momentum=0.9 indicates that the gradient from the previous step counts for 90% of the momentum, which can be viewed as a type of memory that the gradient has of previous gradients. The current gradient is then added to this 90% accumulated gradient, and the result is used to update the parameters. This concept can help SGD navigate through ravines, areas where the surface curves more steeply in one dimension than in another, which are common around local optima. In these scenarios, SGD with Momentum will oscillate across the slopes of the ravine while only making hesitant progress along the bottom towards the local optimum.

## Adaptive Gradient Algorithm

Adaptive Gradient Algorithm, or Adagrad, is a notable optimization algorithm designed with the flexibility to adapt the learning rate for individual parameters. This

differential adaptation is particularly beneficial for dealing with sparse data, as it can ensure the optimization process is robust even when faced with infrequently occurring features.

Adagrad operates under the principle that not all parameters have the same sensitivity towards updates. In a high-dimensional space where data is sparse and feature occurrence is uneven, some parameters might be tied to frequent features, while others might be associated with infrequent ones. Adagrad ingeniously addresses this disparity by performing smaller updates for parameters associated with frequently occurring features and larger updates for those associated with infrequent features. This individualized treatment helps enhance the model's performance, particularly in contexts involving sparse datasets.

A unique trait of Adagrad lies in its method of adjusting the learning rate. It maintains a cumulative record of all past squared gradients, using this as a scaling factor for the learning rate. The more often a feature occurs, the greater the accumulated gradient, and hence, the smaller the effective learning rate. This ensures that the parameters associated with frequent features do not wildly fluctuate, providing a stable learning process.

However, this method of accumulation also presents a potential drawback. Since all past squared gradients are accumulated without any restriction, the total can become quite large over long training periods, resulting in an excessively small effective learning rate. This rapid decay of the learning rate can stall the learning process prematurely in long-running tasks, making Adagrad less suitable for some deep learning applications.

### Using Adagrad Algorithm

The following is an example of using the Adagrad optimizer in PyTorch:

```
# Define a simple linear model

model = torch.nn.Linear(10, 5)

# Define the loss function

loss_fn = torch.nn.MSELoss()

# Define the optimizer - Adagrad

optimizer = torch.optim.Adagrad(model.parameters(), lr=0.01)
```
# Example data
```
input = torch.randn(100, 10)
```
```
target = torch.randn(100, 5)
```
# Define the batch size
```
batch_size = 10
```
# Training loop
```
for i in range(100):
```
```
for j in range(0, input.shape[0], batch_size):
```
# Compute the predicted output
```
output = model(input[j:j+batch_size])
```
# Compute the loss
```
loss = loss_fn(output, target[j:j+batch_size])

# Zero the gradients

optimizer.zero_grad()

# Compute the gradients

loss.backward()

# Update the parameters

optimizer.step()
```

In the above sample program, the torch.optim.Adagrad is used to instantiate the Adagrad optimizer. Like SGD, the primary argument to the Adagrad optimizer is the set of parameters to be optimized, and it also accepts learning rate (lr) as an optional parameter.

## Adaptive Moment Estimation

Adaptive Moment Estimation (Adam) is a popular optimization algorithm used in training many types of deep learning models. Adam combines elements from

two other popular algorithms: AdaGrad, which handles sparse gradients, and RMSProp, which handles non-stationary (i.e., rapidly changing) objectives.

The name "Adam" is derived from "adaptive moment estimation", and the algorithm is designed to compute individual adaptive learning rates for different parameters. It calculates an exponential moving average of the gradient and the squared gradient, and the parameters beta1 and beta2 control the decay rates of these moving averages.

The main advantages of Adam include:

- Straightforward to implement.
- Computationally efficient with little memory requirements.
- Invariant to diagonal rescale of the gradients.
- Well suited for problems that are large in terms of data or parameters.
- Appropriate for non-stationary objectives.
- Works well with problems with very noisy or sparse gradients.
- Provides some regularization effects.

Now, we will look at an example of using the Adam optimizer in PyTorch:
