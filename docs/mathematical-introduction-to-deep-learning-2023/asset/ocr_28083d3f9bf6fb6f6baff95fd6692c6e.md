```
23
24 # Define a neural network with two hidden layers with 50 neurons
25 # each using ReLU activations
26 N = torch.nn.Sequential(
27 torch.nn.Linear(d+1, 50), torch.nn.ReLU(),
28 torch.nn.Linear(50, 50), torch.nn.ReLU(),
29 torch.nn.Linear(50, 1)
30 ).to(dev)
31
32 # Configure the training parameters and optimization algorithm
33 steps = 3000
34 batch_size = 256
35 optimizer = torch.optim.Adam(N.parameters())
36
37 # Train the network
38 for step in range(steps):
39 # Generate uniformly distributed samples from [a,b]^d
40 x = (torch.rand(batch_size, d) * (b-a) + a).to(dev)
41 t = T * torch.rand(batch_size, 1).to(dev)
42
43 optimizer.zero_grad()
44 # Compute the loss
45 L = loss(N, rho, phi, t, x)
46 # Compute the gradients
47 L.backward()
48 # Apply changes to weights and biases of N
49 optimizer.step()
50
51 # Plot the result at M+1 timesteps
52 M = 5
53 mesh = 128
54
55 def toNumpy(t):
56 return t.detach().cpu().numpy().reshape((mesh, mesh))
57
58 fig, axs = plt.subplots(2,3,subplot_kw=dict(projection='3d'))
59 fig.set_size_inches(16, 10)
60 fig.set_dpi(300)
61
62 for i in range(M+1):
63 x = torch.linspace(a, b, mesh)
64 y = torch.linspace(a, b, mesh)
65 x, y = torch.meshgrid(x, y, indexing='xy')
66 x = x.reshape((mesh*mesh,1)).to(dev)
67 y = y.reshape((mesh*mesh,1)).to(dev)
68 z = N(torch.cat((i*T/M*torch.ones(128*128,1).to(dev), x, y), 1))
69
70 axs[i//3, i%3].set_title(f"t = {i * T / M}")
```