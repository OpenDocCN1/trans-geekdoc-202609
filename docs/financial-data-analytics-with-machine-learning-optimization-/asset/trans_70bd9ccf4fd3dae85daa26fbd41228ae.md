

1. [1](#c10.xhtml#R_c10-note-0001) 该估计量是通过最小化 `L²`‐损失函数 `L(β) = (y − X̃β)⊤(y − X̃β) = y⊤y − y⊤X̃β − β⊤X̃⊤y + β⊤X̃⊤X̃β` 得到的，其一阶条件 `∇βL = −2X̃⊤y + 2X̃⊤X̃β = 0` 给出 `X̃⊤(X̃X̃β̂) = X̃⊤y`。请注意，这是一种无正则化的回归，尤其是在 `X` 不够稀疏的情况下。否则，对于稀疏的 `X`，我们在目标函数中添加一个额外的正则化项 `∑{i : xi is sparse} λi|βi|`；进一步讨论可见 [第 11 章](#c11.xhtml)。

2. [2](#c10.xhtml#R_c10-note-0002) 更多细节可见 [`http://mba.tuck.dartmouth.edu/pages/faculty/ken.french/Data_Library/f-f_3developed.html`](http://mba.tuck.dartmouth.edu/pages/faculty/ken.french/Data_Library/f-f_3developed.html)。

3. [3](#c10.xhtml#R_c10-note-0003) 来自 `Bloomberg` 和 `Yahoo Finance`，例如。

