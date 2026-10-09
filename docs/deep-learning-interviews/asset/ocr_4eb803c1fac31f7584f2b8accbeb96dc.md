+   2 There possible methods are:
- i Constant
- ii Xavier/Glorot uniform
- iii Xavieir/Glorot normal

+   3 Good initialization would optimally generate activations that produce initial gradients that are larger than zero. One idea is that the training process would converge faster if unit variance is achieved ([16]). Moreover, weights should be selected carefully so that:
- i They are large enough thus preventing gradients from decaying to zero.
- ii They are not too large causing activation functions to over saturate.

+   4 There are several ways to reduce the problem of plateaus:
- i Add some type of regularization.
- ii In cases wherein the plateau happens right at the beginning, amend the way weights are initialized.
- iii Amending the optimization algorithm altogether; for instance using SGD instead of Adam and vice versa.

5 Since the initial LR is already very low, his suggestion may worsen the situation since the optimiser would not be able to jump off and escape the plateau.

6 In contrast to accuracy, Log loss has no upper bounds and therefore at times may be more difficult to understand and to explain.