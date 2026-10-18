

$$\\begin{aligned} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}})} & {= {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}p\_{0}}(S\_{0}) \\cdot {\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{0},A\_{0})} \\\\ & {+ {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}p\_{0}}(S\_{0}) \\cdot {\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\pi}(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}Q^{\\pi}(S\_{0},A\_{0})} \\\\ \\end{aligned}$$  

现在将 `Q`^(*π*)(*S*[0], *A*[0]) 展开为：

$$\\begin{array}{r} {\\mathcal{R}\_{S\_{0}}^{A\_{0}} + {\\sum\\limits\_{S\_{1} \\in \\mathcal{N}}\\gamma} \\cdot \\mathcal{P}\_{S\_{0},S\_{1}}^{A\_{0}} \\cdot V^{\\pi}(S\_{1})\\text{~(Bellman~Policy~Equation)}} \\\\ \\end{array}$$  

$$\\begin{aligned} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}})} & {= {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}p\_{0}}(S\_{0}) \\cdot {\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{0},A\_{0})} \\\\ & {+ {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}p\_{0}}(S\_{0}) \\cdot {\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\pi}(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}(\\mathcal{R}\_{S\_{0}}^{A\_{0}} + {\\sum\\limits\_{S\_{1} \\in \\mathcal{N}}\\gamma} \\cdot \\mathcal{P}\_{S\_{0},S\_{1}}^{A\_{0}} \\cdot V^{\\pi}(S\_{1}))} \\\\ \\end{aligned}$$  

注意：∇[*θ*]ℛ[*S*[0]]^(*A*[0]) = 0，因此移除该项。

$$\\begin{aligned} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}})} & {= {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}p\_{0}}(S\_{0}) \\cdot {\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{0},A\_{0})} \\\\ & {+ {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}p\_{0}}(S\_{0}) \\cdot {\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\pi}(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}({\\sum\\limits\_{S\_{1} \\in \\mathcal{N}}\\gamma} \\cdot \\mathcal{P}\_{S\_{0},S\_{1}}^{A\_{0}} \\cdot V^{\\pi}(S\_{1}))} \\\\ \\end{aligned}$$  

现在将 ∇[**θ**] 移入 ∑[*S*[1] ∈ 𝒩] 内，使其仅作用于 *V*^(*π*)(*S*[1])。

$$\\begin{aligned} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}})} & {= {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}p\_{0}}(S\_{0}) \\cdot {\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{0},A\_{0})} \\\\ & {+ {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}p\_{0}}(S\_{0}) \\cdot {\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\pi}(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot {\\sum\\limits\_{S\_{1} \\in \\mathcal{N}}\\gamma} \\cdot \\mathcal{P}\_{S\_{0},S\_{1}}^{A\_{0}} \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}V^{\\pi}(S\_{1})} \\\\ \\end{aligned}$$  

现在将 ∑[*S*[0] ∈ 𝒩] 和 ∑[*A*[0] ∈ 𝒜] 移入 ∑[*S*[1] ∈ 𝒩] 内。

$$\\begin{aligned} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}})} & {= {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}p\_{0}}(S\_{0}) \\cdot {\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{0},A\_{0})} \\\\ & {+ {\\sum\\limits\_{S\_{1} \\in \\mathcal{N}}{\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}\\gamma}} \\cdot p\_{0}(S\_{0}) \\cdot ({\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\pi}(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot \\mathcal{P}\_{S\_{0},S\_{1}}^{A\_{0}}) \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}V^{\\pi}(S\_{1})} \\\\ \\end{aligned}$$  

$$\\begin{array}{r} \\left. \\text{请注意，}{\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\pi}(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot \\mathcal{P}\_{S\_{0},S\_{1}}^{A\_{0}} = p(S\_{0}\\rightarrow S\_{1},1,\\pi) \\right. \\\\ \\end{array}$$  

$$\\begin{aligned} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}})} & {= {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}p\_{0}}(S\_{0}) \\cdot {\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{0},A\_{0})} \\\\ & \\left. + {\\sum\\limits\_{S\_{1} \\in \\mathcal{N}}{\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}\\gamma}} \\cdot p\_{0}(S\_{0}) \\cdot p(S\_{0}\\rightarrow S\_{1},1,\\pi) \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}V^{\\pi}(S\_{1}) \\right. \\\\ \\end{aligned}$$  

$$\\begin{array}{r} {\\text{现在将}V^{\\pi}(S\_{1})\\text{展开为}{\\sum\\limits\_{A\_{1} \\in \\mathcal{A}}\\pi}(S\_{1},A\_{1};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{1},A\_{1})} \\\\ \\end{array}$$  

$$\\begin{aligned} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}})} & {= {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}p\_{0}}(S\_{0}) \\cdot {\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{0},A\_{0})} \\\\ & \\left. + {\\sum\\limits\_{S\_{1} \\in \\mathcal{N}}{\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}\\gamma}} \\cdot p\_{0}(S\_{0}) \\cdot p(S\_{0}\\rightarrow S\_{1},1,\\pi) \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}({\\sum\\limits\_{A\_{1} \\in \\mathcal{A}}\\pi}(S\_{1},A\_{1};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{1},A\_{1})) \\right. \\\\ \\end{aligned}$$  

我们现在回到了开始计算 ${\\sum\\limits\_{a}\\pi} \\cdot Q^{\\pi}$ 梯度时的状态。按照同样的分部求导过程计算 *π* ⋅ *Q*^(*π*) 的梯度，然后对 *Q*^(*π*) 进行贝尔曼展开（以计算其梯度），并迭代。

$$\\begin{array}{r} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}}) = {\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}p\_{0}}(S\_{0}) \\cdot {\\sum\\limits\_{A\_{0} \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(S\_{0},A\_{0};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{0},A\_{0}) +} \\\\ \\end{array}$$  

$$\\begin{array}{r} \\left. {\\sum\\limits\_{S\_{1} \\in \\mathcal{N}}{\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}\\gamma}} \\cdot p\_{0}(S\_{0}) \\cdot p(S\_{0}\\rightarrow S\_{1},1,\\pi) \\cdot ({\\sum\\limits\_{A\_{1} \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(S\_{1},A\_{1};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{1},A\_{1}) + \\ldots) \\right. \\\\ \\end{array}$$  

这个迭代过程得出：

$$\\begin{array}{r} \\left. \\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}}) = {\\sum\\limits\_{t = 0}^{\\infty}{\\sum\\limits\_{S\_{t} \\in \\mathcal{N}}{\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}\\gamma^{t}}}} \\cdot p\_{0}(S\_{0}) \\cdot p(S\_{0}\\rightarrow S\_{t},t,\\pi) \\cdot {\\sum\\limits\_{A\_{t} \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(S\_{t},A\_{t};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{t},A\_{t}) \\right. \\\\ \\end{array}$$  

$$\\begin{array}{r} {\\text{将}{\\sum\\limits\_{t = 0}^{\\infty}\\text{移入}}{\\sum\\limits\_{S\_{t} \\in \\mathcal{N}}{\\sum\\limits\_{S\_{0} \\in \\mathcal{N}}\\text{并注意}}}} \\\\ \\end{array}$$  

$$\\begin{array}{r} {{\\sum\\limits\_{A\_{t} \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(S\_{t},A\_{t};\\mathbf{\\mathbf{\\theta}}) \\cdot Q^{\\pi}(S\_{t},A\_{t})\\text{与}t\\text{无关}} \\\\ \\end{array}$$  

