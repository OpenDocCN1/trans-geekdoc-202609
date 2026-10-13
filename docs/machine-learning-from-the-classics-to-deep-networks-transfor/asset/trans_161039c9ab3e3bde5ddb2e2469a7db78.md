

$$
\overline{\mathbf{q}}_{\mathbf{\theta}_{3}}(\mathbf{z}) = \frac{\mathbf{q}_{\mathbf{\theta}_{3}}(\mathbf{z})}{||\mathbf{q}_{\mathbf{\theta}_{3}}(\mathbf{z})||_{2}},\ \text{and}\ \overline{\mathbf{z}}^{\prime} = \frac{\mathbf{z}^{\prime}}{||\mathbf{z}^{\prime}||_{2}},
$$

![Equation](images/B9780443292385000251/si484.png)

最优参数集由此得出为

$$
(\mathbf{\theta}_{1 \ast},\mathbf{\theta}_{2 \ast},\mathbf{\theta}_{3 \ast}): = \arg\min\limits_{\mathbf{\theta}_{1},\mathbf{\theta}_{2},\mathbf{\theta}_{3}}\sum\limits_{n = 1}^{N_{t}}||\overline{\mathbf{z}}_{n}^{\prime} - \overline{\mathbf{q}}_{\mathbf{\theta}_{3}}(\mathbf{z}_{n})||_{2}^{2},
$$

![Equation](images/B9780443292385000251/si485.png)

其中 $N_{t}$ 用于表示训练数据样本的数量。请注意，优化仅针对定义学生分支的参数进行。在第 $t$ 次迭代步骤中，教师分支的参数通过所谓的*指数移动平均*（EMA）（动量）原理进行更新，即

$$
\boldsymbol{\xi}_{i}^{(t)} = \alpha\boldsymbol{\xi}_{i}^{(t-1)} + (1 - \alpha)\boldsymbol{\theta}_{i}^{(t)},\quad i = 1, 2,
$$

![Equation](images/B9780443292385000251/si486.png)

