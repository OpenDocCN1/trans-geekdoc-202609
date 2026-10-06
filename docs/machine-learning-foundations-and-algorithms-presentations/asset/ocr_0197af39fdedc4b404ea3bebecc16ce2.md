# # Difficulty in Training GANs

# ## Issues with the Discriminator

![](bbox=[0.183, 0.303, 0.755, 0.792])

As the Discriminator gets more and more confident, the region that gives us informative gradients keeps shrinking.

... Till we eventually achieve a step-function which tells us nothing about how G should be changed for the desired effect on the model.