```
# get the inputs; data is a list of [inputs, labels]
inputs, labels = data[0].to('cuda'), data[1].to('cuda')
# zero the parameter gradients
optimizer.zero_grad()
# forward + backward + optimize
outputs = model(inputs)
loss = criterion(outputs, labels)
loss.backward()
optimizer.step()
```

This script will automatically use all GPUs available on the machine. The data is split in the batch dimension, so the batch size should be larger than the number of GPUs used.