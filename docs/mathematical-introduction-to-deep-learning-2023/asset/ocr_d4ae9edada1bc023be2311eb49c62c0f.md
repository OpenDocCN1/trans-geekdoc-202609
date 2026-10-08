# 7.5. SGD optimization with Nesterov momentum

```
```
14 J = 64
15
16 N = 150000
17
18 loss = nn.MSELoss()
19 lr = 0.003
20 alpha = 0.999
21
22 m = [p.clone().detach().zero_() for p in net.parameters()]
23
24 for n in range(N):
25     indices = torch.randint(0, M, (J,))
26
27     x = X[indices]
28     y = Y[indices]
29
30     net.zero_grad()
31
32     # Remember the original parameters
33     params = [p.clone().detach() for p in net.parameters()]
34
35     for p, m_p in zip(params, m):
36         p.sub_(lr * alpha * m_p)
37
38     # Compute the loss
39     loss_val = loss(net(x), y)
40     # Compute the gradients with respect to the parameters
41     loss_val.backward()
42
43     with torch.no_grad():
44         for p, m_p, q in zip(net.parameters(), m, params):
45             m_p.mul_(alpha)
46             m_p.add_((1 - alpha) * p.grad)
47             q.sub_(lr * m_p)
48             p.copy_(q)
49
50     if n % 1000 == 0:
51         with torch.no_grad():
52             x = torch.rand((1000, 1)) * 4 * np.pi - 2 * np.pi
53             y = torch.sin(x)
54             loss_val = loss(net(x), y)
55             print(f"Iteration: {n+1}, Loss: {loss_val}")
```
```

Source code 7.6 (code/optimization_methods/nesterov_sgd.py): PYTHON code implementing the Nesterov accelerated SGD optimization method in PyTorch