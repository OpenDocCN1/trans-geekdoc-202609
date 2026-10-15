In the above demonstration, the loop over j steps in increments of batch_size, taking a slice of the input data and the target data for each mini-batch. In practice, you would also want to shuffle the input data at the start of each epoch to ensure the model doesn't learn anything from the order of the samples.

# Momentum

Momentum, a concept borrowed from physics, has been cleverly applied in the realm of optimization algorithms to accelerate the learning process. The idea behind momentum is simple: an object in motion tends to maintain its trajectory unless acted upon by an external force. This principle is applied to the optimization process in machine learning to guide the optimizer effectively, ensuring smoother and quicker convergence towards the global minimum of the loss function.

Within the context of optimization, momentum functions by carrying forward a fraction of the update vector from the previous time step to the current one. This mechanism assists the optimizer in moving along relevant directions more effectively, thereby mitigating unnecessary oscillations. The momentum term effectively serves as a memory of the previous