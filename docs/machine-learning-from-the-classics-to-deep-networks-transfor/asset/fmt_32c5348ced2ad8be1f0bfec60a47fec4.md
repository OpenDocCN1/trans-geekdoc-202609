
For gradient descent, `Φ[i] = I`, and for Newton-type recursions, `Φ[i]` is the inverse Hessian matrix of the loss function (Chapter [6](#Chp006_249-291_B9780443292385000123.xhtml)).

Note that these are not the only possible choices for matrix `Φ`. For example, in the Levenberg–Marquardt method, the square Jacobian is employed, that is,

```
Φ[i] = [∇J(θ^(i−1))∇^(T)J(θ^(i−1)) + λI]^(−1)
```

where `λ` is a regularization parameter. In [3], the *natural gradient* is proposed, which is based on the Fisher information matrix associated with the noisy distribution implied by the adopted prediction model, `f_θ(x)`. In both cases, the involved matrices asymptotically behave like the Hessian, yet they may provide improved performance during the initial convergence phase. For a further discussion, the interested reader may consult [49,56].

As already mentioned in Chapters [5](#Chp005_177-248_B9780443292385000111.xhtml) and [6](#Chp006_249-291_B9780443292385000123.xhtml) (Section [6.7](#Chp006_249-291_B9780443292385000123.xhtml)), the convergence rate to the respective optimal value of the simple gradient descent method (for the mean-square error case) is *linear*, that is,

```
ln(1/‖θ^(i) − θ_*(N)‖) ∝ i
```

and the corresponding rate for a Newton-type algorithm is (approximately) quadratic, that is,

```
ln ln(1/‖θ^(i) − θ_*(N)‖) ∝ i.
```

In contrast, the online version of Eq. [(8.98)](#Chp008_343-416_B9780443292385000147.xhtml#deq186), that is,

```
θ[n] = θ[n−1] − μ[n]Φ[n]L'(θ[n−1], y[n], x[n])
```
(8.98)
