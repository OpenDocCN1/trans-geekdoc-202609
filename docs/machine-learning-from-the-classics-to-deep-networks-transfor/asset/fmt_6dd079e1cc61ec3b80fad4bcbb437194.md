
**θ** = **θ**[r] + *j***θ**[i].

![Equation](images/B9780443292385000111/si118.png)

Then the cost function

*J*(**θ**) : ℂ^(*l*) ↦ [0, +∞)

![Equation](images/B9780443292385000111/si119.png)

is approximated as

*J*(**θ** + *Δ***θ**) = *J*(**θ**[r] + *Δ***θ**[r], **θ**[i] + *Δ***θ**[i]) = *J*(**θ**[r], **θ**[i]) + *Δ***θ**[r]^(*T*)∇[r]*J*(**θ**[r], **θ**[i]) + *Δ***θ**[i]^(*T*)∇[i]*J*(**θ**[r], **θ**[i]),

![Equation](images/B9780443292385000111/si120.png) (5.25)

where ∇[r] (∇[i]) denotes the gradient with respect to **θ**[r] (**θ**[i]).

![Equation](images/B9780443292385000111/si121.png) ![Equation](images/B9780443292385000111/si122.png)

Taking into account that

```
$\\Delta\\mathbf{\\theta}\_{r} = \\frac{\\Delta\\mathbf{\\theta} + \\Delta\\mathbf{\\theta}^{\\ast}}{2},\\quad\\Delta\\mathbf{\\theta}\_{i} = \\frac{\\Delta\\mathbf{\\theta} - \\Delta\\mathbf{\\theta}^{\\ast}}{2j},$
```

![Equation](images/B9780443292385000111/si123.png)

it is easy to show (Problem [5.3](#Chp005_177-248_B9780443292385000111.xhtml#o0020)) that
