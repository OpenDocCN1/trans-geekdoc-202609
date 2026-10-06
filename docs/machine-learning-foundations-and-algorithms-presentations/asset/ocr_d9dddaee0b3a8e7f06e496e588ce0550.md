# Chain rule

With vectors:

$u = u(x), \frac{\partial g(u)}{\partial x} = \frac{\partial u(x)}{\partial x} \frac{\partial g(u)}{\partial u}$

+   - Note: Swapped order
- Special case (scalar-> vector -> scalar):

$u = u(t), \frac{\partial g(u)}{\partial t} = \frac{\tilde{\partial u(t)}}{\partial t}_{1 \times d}} \frac{\partial g(u)}{\partial u}_{d \times 1}} = \sum_{i=1}^{d} \frac{\partial u_i(t)}{\partial t} \frac{\partial g(u)}{\partial u_i}$