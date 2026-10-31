modified while pixel values. This renders the image unrecognizable. For confusion stage, control parameters and initial conditions of the chaotic sequence serve up as the secret key. Permutation stage alone cannot provide security. It can be easily compromised by any attacks.

To augment safety, the encryption process second stage changes the worth of every pixel within the entire image. Sequentially modify the values of the pixels in the diffusion level, with the aid of random sequence created using the chaotic system. The confusion and diffusion process are iterated to enhance the security level. Iteration of confusion and diffusion process results in randomness and hence makes chaotic systems preferred choice for image encryption (Sakthidasan & Santhosh, 2011).

# 3.3 HENON MAP-BASED IMAGE ENCRYPTION

Henon chaotic map is a 2D discrete time dynamic system that has kindled interest in the researchers in the recent years. Introduced by Michel Henon, it is the straightforward type of Lorenz model. Henon map transforms a point (x_n, y_n) in the plane to another point (x_{n+1}, y_{n+1}) as defined below:

x_{i+1} = y_i + 1 - α x_i^2  (3.1)
y_{i+1} = β x_i  (3.2)

Henon map has two dependent parameters α, β are called the initial parameters. The canonical values are = 1.4 and = 0.3, which make the Henon map chaotic, and iterations appear to be a boomerang-shaped chaotic attractor. With these values, the plane’s beginning point can either map to the Henon attractor or diverge to infinity. The Henon map may appear chaotic or intermittent or converge to a periodic orbit for any values other than the canonical (https://en.wikipedia.org/wiki/H%C3%A9non_map).

Figure 3.3 shows a Henon map for a 2D plane formed from a well-defined number of rounds starting at the initial point (0.1, 0.1). Slightest changes in the initial point leads to drastic variations and hence in random behavior.

# 3.4 PERFORMANCE PARAMETERS FOR IMAGE ENCRYPTION

Performance analysis of encryption algorithm involves finding ways to attack the cryptosystem to extract partial or complete information from the encrypted image or to determine the secret key. These attacks are performed without the prior information about the decryption key. Parameters used for