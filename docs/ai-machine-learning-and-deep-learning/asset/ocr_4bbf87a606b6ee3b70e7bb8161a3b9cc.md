aims to add as little noise as possible to standard input data and make the output data as misclassified as possible. We can show this idea in equation (6.3.1) [17]. We take the neural network as a function, and the standard input x. However, adding noise to the standard input x and δ x is smaller than a small number ε. With a few different inputs, the function returns different outputs (see Figure 6.4).

![](bbox=[0.11, 0.24, 0.84, 0.42])

FIGURE 6.4 Image with class C, with some noise δx added into the images and put into a trained DNN. The trained DNN then returns the incorrect class D with the highest probability of 0.8. For an excellent adversarial image, we check to see whether the noise is as minor as expected. If Yes, a malicious image is created. If No, we update the noise and create another image as an input to the trained DNN.

Instead of using error-generic and error-specific, Shafique et al.(6.3.1) used the names “untargeted attack scenario” for random incorrect output and “targeted attack” for a specific output [17].

# 6.3.2.1 Evasion Attack

An attacker does not have access to the DNN training process and training data in an evasion attack. This attack aims at a learning model that has been trained. In Figure 6.4, we can see the process of finding the adversarial examples automatically. In [20], Goodfellow et al. provided a fast gradient sign method (FGSM). This algorithm finds out the input gradient direction of the loss function cost and adds noise to the input, creating a piece of new information as an adversarial example.