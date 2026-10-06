# Min-Max Stationary Point

+   There exists a stationary point:
- If the generated data exactly matches the real data, the discriminator outputs 0.5 for all inputs
- If discriminator outputs 0.5, the gradients for the generator is flat, so generator does not learn
- Unfortunately, this is also true of a random discriminator

+   Stationary points need not be stable (depends on the exact GANs formulation and other factors)
- Generator may overshoot some values or oscillate around the optimum
- A discriminator with unlimited capacity can still assign an arbitrarily large distance to 2 similar distributions