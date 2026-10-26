# GANs vs InfoGAN

![](bbox=[0.16, 0.22, 0.38, 0.5])

code data/gen

![](bbox=[0.18, 0.55, 0.35, 0.85])

max_φ L_φ = 𝔼_{p_θ(x|y)p(y)} [log q_φ(y|x)]
max_θ L_θ = 𝔼_{p_θ(x|y)p(y)} [log q_φ^r(y|x)]

![](bbox=[0.62, 0.22, 0.84, 0.5])

code data/gen

![](bbox=[0.64, 0.55, 0.82, 0.85])

max_φ L_φ = 𝔼_{p_θ(x|y)p(y)} [log q_η(z|x,y) q_φ(y|x)]
max_{θ,η} L_{θ,η} = 𝔼_{p_θ(x|y)p(y)} [log q_η(z|x,y) q_φ^r(y|x)]