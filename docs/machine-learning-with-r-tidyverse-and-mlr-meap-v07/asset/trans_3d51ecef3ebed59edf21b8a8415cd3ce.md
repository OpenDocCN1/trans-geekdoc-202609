...[/content].

We must not output any original English text, only translation. Ensure we keep all lines, including code blocks, equations, figure captions, etc. Also need to translate bold and italic content, preserving symbols. For example **EQUATION 19.3** becomes **EQUATION 19.3**? The rule: bold needs translation of content and retain symbols. So **EQUATION 19.3** is bold, we need to translate "EQUATION" to Chinese? Probably "公式". But keep the number. So **EQUATION 19.3** => **公式 19.3**. However the example: "**Richard Feynman**" translated to "诺贝尔物理奖获得者**理查德·费曼**". They kept the bold around the name, but translated the surrounding text. For **EQUATION 19.3**, it's a label, maybe translate "EQUATION" to "公式". So **EQUATION 19.3** => **公式 19.3**. Also need to keep the asterisks.

Italic: *itatic* => *italic*? In example they translated "*hard to forget*" to "*难以遗忘*". So keep italic markers and translate content.

Inline code: `20 min` stays same.

Links: [Feynman's learning method](https://wiki.example.org/feynmans_learning_method) => [费曼学习法](https://wiki.example.org/feynmans_learning_method). So translate the link text, keep URL.

List items: need to translate each line.

We must ensure we keep the same line breaks as original. Also need to keep code fences unchanged.

Let's go through the text line by line.

Original text:

[content]

Notice that the evidence has been expanded to more concretely show how the probability of drawing case $x_i$ from either Gaussian is the sum of the probabilities of drawing it from each Gaussian independently. Equation 19.2 allows us to calculate the posterior probability of case $x_i$ belonging to Gaussian $k$. Equation 19.3 shows the same calculation, but for the posterior probability of case $x_i$ belonging to Gaussian $j$.

**EQUATION 19.3**

$$p(j \mid x_i)=\frac{p(x_i\mid j)\times p(j)}{p(x_i\mid k)p(k)+p(x_i\mid j)p(j)}$$

So far, so good. But how do we calculate the likelihood and the priors? The likelihood is the probability density function of the Gaussian distribution, which tells us the relative probability of drawing a case with a particular value, from a Gaussian distribution with a particular combination of mean and variance. The probability density function for Gaussian distribution $k$ is shown in equation 19.4, but it isn’t necessary for you to memorize it.

**EQUATION 19.4**

$$p(x_i\mid k)=\frac{1}{\sqrt{2\pi\sigma_k^2}}e^{-\frac{(x_i-\mu_k)^2}{2\sigma_k^2}}$$

where $\mu_k$ and $\sigma_k^2$ are the mean and variance, respectively, for Gaussian $k$.

At the start of the algorithm, the prior probabilities are generated randomly, just like the means and variances of the Gaussians. These priors get updated at each iteration to be the sum of the posterior probabilities for each Gaussian, divided by the number of cases. You can think of this as the mean posterior probability for a particular Gaussian, across all cases.

### 19.1.2 The EM algorithm: expectation and maximization steps

Now that we have the necessary knowledge to understand how the posterior probabilities are calculated, let’s see how the EM algorithm iteratively fits the mixture model. The EM algorithm (like its name suggests) has two steps: expectation, and maximization. The expectation step is where the posterior probabilities are calculated for each case, for each Gaussian. This is shown in the second panel from the top in figure 19.1.

At this stage, the algorithm uses Bayes' rule, as we set out earlier, to calculate the posterior probabilities. The cases along the number line in figure 19.1 are shaded to indicate their posterior probabilities.

Next comes the maximization step. The job of the maximization step is to update the parameters of the mixture model, to maximize the likelihood of the underlying data. This means updating the means, variances and priors of the Gaussians.

Updating the mean of a particular Gaussian involves adding up the values of each case, weighted by their posterior probability for that Gaussian, and dividing by the sum of all the posterior probabilities. This is shown in equation 19.5.

**EQUATION 19.5**

$$\mu_k = \frac{\sum_{i=1}^{n} p(k\mid x_i)x_i}{\sum_{i=1}^{n} p(k\mid x_i)}$$

Think about this for a second. Cases that are close to the mean of the distribution will have a high posterior probability for that distribution, and so will contribute more to the updated mean. Cases far away from the distribution will have a small posterior probability, and will contribute less to the updated mean. The result is that the Gaussian will move towards the mean of the cases that are most probable under this Gaussian. You can see this illustrated in the third panel of figure 19.1.

The variance of each Gaussian is updated in a similar way. This time, we sum the squared difference between each case and the Gaussian’s mean, multiplied by the case’s posterior, then divide by the sum of posteriors. This is shown in equation 19.6. The result is that the Gaussian will get wider or narrower, based on the spread of the cases that are most probable under this Gaussian. You can also see this illustrated in the third panel of figure 19.1.

**EQUATION 19.6**

$$\sigma_k^2 = \frac{\sum_{i=1}^{n} p(k\mid x_i)(x_i-\mu_k)^2}{\sum_{i=1}^{n} p(k\mid x_i)}$$

The last thing to be updated are the prior probabilities for each Gaussian. As mentioned already, the new priors are calculated by dividing the sum of the posterior probabilities for a particular Gaussian by the number of cases, as shown in equation 19.7. This means that a Gaussian for which many cases have a large posterior probability, will have a large prior probability. Conversely, a Gaussian for which few cases have a large posterior, will have a small prior probability. You can think of this as a soft or probabilistic equivalent to setting the prior equal to the proportion of cases belonging to each Gaussian.

**EQUATION 19.7**

$$p(k)=\frac{\sum_{i=1}^{n}p(k\mid x_i)}{n}$$

Once the maximization step is complete, we perform another iteration of the expectation step, this time computing the posterior probabilities for each case under the new Gaussians. Once this is done, we then re-run the maximization step, once again updating the means, variances, and priors for each Gaussian based on the posteriors.

![](img/a22105d68c35e8d5bd3c7bafb4644881_486_0.png)

**Figure 19.1** The expectation-maximization algorithm for two, 1-dimensional Gaussians. Circles represent cases along a number line. Two Gaussians are randomly initialized along the line. In the expectation step, the posterior probability of each case for each Gaussian is calculated (indicated by shading). In the maximization step, the means, variances, and priors for each Gaussian are updated based on the calculated posteriors. The process continues until the likelihood converges.

This cycle of expectation-maximization continues iteratively until either a specified number of iterations is reached, or until the overall likelihood of the data under the model changes by less than a specified amount (called convergence).

### 19.1.3 What if we have more than one variable?

In this section I’ll extend what we learned about how the EM algorithm works in one dimension, to when we are clustering over multiple dimensions.

It is rare to come across a univariate (one-dimensional) clustering problem. Usually, our datasets contain multiple variables we wish to use to identify clusters. I limited my explanation of the EM algorithm for Gaussian mixture models in the previous section, because a univariate Gaussian has only two parameters: its mean and variance. When we have a Gaussian distribution in more than one-dimension (a multivariate Gaussian), we need to describe it using its centroid, and its covariance matrix.

We’ve come across centroids in previous chapters, they are simply a vector of means, one for each dimension/variable in the dataset. A covariance matrix is a square matrix whose elements are the covariance between variables. For example, the value in the second row, third column of a covariance matrix indicates the covariance between variables two and three in the data. Covariance is an unstandardized measure of how much two variables change together. A positive covariance means that as one variable increases, so does the other. A negative covariance means that as one variable increases, the other decreases. A covariance of zero usually indicates no relationship between the variables at all. We can calculate the covariance between two variables using equation 19.8.

**EQUATION 19.8**

$$\operatorname{Cov}(x,y) = \frac{\sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}{n-1}$$

> While covariance is an unstandardized measure of the relationship between two variables, correlation is a standardized measure of the relationship between two variables. We can convert covariance into correlation by dividing it by the product of the variables' standard deviations.

The covariance between one variable and itself is simply that variable’s variance. Therefore, the diagonal elements of a covariance matrix are variances of each of the variables.

> In fact, covariance matrices are often called variance-covariance matrices for this reason.

So if the EM algorithm only estimated a variance for each Gaussian, in each dimension, the Gaussians would be perpendicular to the axes of the feature space. Put another way, it would force the model to assume there were no relationships between the variables in the data. It’s usually more sensible to assume there will be some degree of relationship between the variables, and so estimating the covariance matrix allows the Gaussians to lie diagonally across the feature space.

> As we estimate the covariance matrix, this means that Gaussian mixture model clustering is insensitive to variables on different scales. Therefore, we don’t need to scale our variables before training the model.

So when we’re clustering over more than one dimension, the EM algorithm randomly initializes the centroid, covariance matrix, and prior for each Gaussian. It then calculates the posterior probability for each case, for each Gaussian in the expectation step. In the maximization step, the centroid, covariance matrix, and prior probability are updated for each Gaussian. The EM algorithm continues to iterate until either the maximum number of iterations is reached, or the algorithm reaches convergence. The EM algorithm for a bivariate case is illustrated in figure 19.2.

[/content]

We need to translate all English text, preserving formatting.

Let's translate.

First line: "Notice that the evidence has been expanded to more concretely show how the probability of drawing case $x_i$ from either Gaussian is the sum of the probabilities of drawing it from each Gaussian independently."

Translate: "注意，证据已扩展以更具体地展示如何从任一高斯分布中抽取案例 $x_i$ 的概率等于从每个高斯分布独立抽取它的概率之和。"

Second sentence: "Equation 19.2 allows us to calculate the posterior probability of case $x_i$ belonging to Gaussian $k$."

Translate: "方程 19.2 使我们能够计算案例 $x_i$ 属于高斯分布 $k$ 的后验概率。"

Third: "Equation 19.3 shows the same calculation, but for the posterior probability of case $x_i$ belonging to Gaussian $j$."

Translate: "方程 19.3 展示了相同的计算，但针对案例 $x_i$ 属于高斯分布 $j$ 的后验概率。"

Now **EQUATION 19.3** => **公式 19.3** (bold). Keep the equation unchanged.

Equation block unchanged.

"So far, so good. But how do we calculate the likelihood and the priors?" => "目前为止，一切就绪。但我们如何计算似然和先验呢？"

"The likelihood is the probability density function of the Gaussian distribution, which tells us the relative probability of drawing a case with a particular value, from a Gaussian distribution with a particular combination of mean and variance."

Translate: "似然是高斯分布的概率密度函数，它告诉我们在给定均值和方差组合的高斯分布中，抽取特定数值的相对概率。"

"The probability density function for Gaussian distribution $k$ is shown in equation 19.4, but it isn’t necessary for you to memorize it."

Translate: "高斯分布 $k$ 的概率密度函数在方程 19.4 中给出，但你不需要记忆它。"

**EQUATION 19.4** => **公式 19.4**.

Equation block unchanged.

"where $\mu_k$ and $\sigma_k^2$ are the mean and variance, respectively, for Gaussian $k$."

Translate: "其中 $\mu_k$ 和 $\sigma_k^2$ 分别是高斯分布 $k$ 的均值和方差。"

"At the start of the algorithm, the prior probabilities are generated randomly, just like the means and variances of the Gaussians."

Translate: "在算法开始时，先验概率是随机生成的，就像高斯分布的均值和方差一样。"

"These priors get updated at each iteration to be the sum of the posterior probabilities for each Gaussian, divided by the number of cases."

Translate: "这些先验在每次迭代中都会更新为每个高斯分布的后验概率之和除以案例数量。"

"You can think of this as the mean posterior probability for a particular Gaussian, across all cases."

Translate: "你可以把这看作是对某一高斯分布在所有案例中的平均后验概率。"

"### 19.1.2 The EM algorithm: expectation and maximization steps"

Translate: "### 19.1.2 EM 算法：期望步骤和最大化步骤"

"Now that we have the necessary knowledge to understand how the posterior probabilities are calculated, let’s see how the EM algorithm iteratively fits the mixture model."

Translate: "现在我们已经拥有理解后验概率计算所需的知识，让我们看看 EM 算法如何迭代地拟合混合模型。"

"The EM algorithm (like its name suggests) has two steps: expectation, and maximization."

Translate: "EM 算法（顾名思义）包含两个步骤：期望步骤和最大化步骤。"

"The expectation step is where the posterior probabilities are calculated for each case, for each Gaussian."

Translate: "期望步骤是计算每个案例、每个高斯分布的后验概率的地方。"

"This is shown in the second panel from the top in figure 19.1."

Translate: "这在图 19.1 中从上往下数第二个面板中显示。"

"At this stage, the algorithm uses Bayes' rule, as we set out earlier, to calculate the posterior probabilities."

Translate: "在此阶段，算法使用我们 earlier 所述的贝叶斯规则来计算后验概率。" Need to translate "earlier" maybe "先前". So: "在此阶段，算法使用先前所述的贝叶斯规则来计算后验概率。"

"The cases along the number line in figure 19.1 are shaded to indicate their posterior probabilities."

Translate: "图 19.1 中的数轴上的案例被阴影标记以指示其后验概率。"

"Next comes the maximization step."

Translate: "接下来是最大化步骤。"

"The job of the maximization step is to update the parameters of the mixture model, to maximize the likelihood of the underlying data."

Translate: "最大化步骤的任务是更新混合模型的参数，以最大化底层数据的似然。"

"This means updating the means, variances and priors of the Gaussians."

Translate: "这意味着更新高斯分布的均值、方差和先验。"

"Updating the mean of a particular Gaussian involves adding up the values of each case, weighted by their posterior probability for that Gaussian, and dividing by the sum of all the posterior probabilities."

Translate: "更新某一高斯分布的均值需要将每个案例的值乘以其在该高斯分布中的后验概率，然后除以所有后验概率之和。"

"This is shown in equation 19.5."

Translate: "这在方程 19.5 中给出。"

**EQUATION 19.5** => **公式 19.5**.

Equation unchanged.

"Think about this for a second. Cases that are close to the mean of the distribution will have a high posterior probability for that distribution, and so will contribute more to the updated mean."

Translate: "再思考一下。靠近分布均值的案例后验概率较高，因此会对更新后的均值作出更大贡献。"

"Cases far away from the distribution will have a small posterior probability, and will contribute less to the updated mean."

Translate: "远离分布的案例后验概率较小，对更新后的均值贡献较少。"

"The result is that the Gaussian will move towards the mean of the cases that are most probable under this Gaussian."

Translate: "结果是高斯分布会向在该高斯分布下最可能的案例均值移动。"

"You can see this illustrated in the third panel of figure 19.1."

Translate: "你可以在图 19.1 的第三个面板中看到此现象的示例。"

"The variance of each Gaussian is updated in a similar way."

Translate: "每个高斯分布的方差也以类似的方式更新。"

"This time, we sum the squared difference between each case and the Gaussian’s mean, multiplied by the case’s posterior, then divide by the sum of posteriors."

Translate: "此时，我们对每个案例与高斯均值的平方差乘以该案例的后验概率，然后除以后验概率之和。"

"This is shown in equation 19.6."

Translate: "这在方程 19.6 中给出。"

"The result is that the Gaussian will get wider or narrower, based on the spread of the cases that are most probable under this Gaussian."

Translate: "结果是高斯分布会根据在该高斯分布下最可能的案例的分布情况而变宽或变窄。"

"You can also see this illustrated in the third panel of figure 19.1."

Translate: "你也可以在图 19.1 的第三个面板中看到此现象的示例。"

**EQUATION 19.6** => **公式 19.6**.

"The last thing to be updated are the prior probabilities for each Gaussian."

Translate: "最后要更新的是每个高斯分布的先验概率。"

"As mentioned already, the new priors are calculated by dividing the sum of the posterior probabilities for a particular Gaussian by the number of cases, as shown in equation 19.7."

Translate: "如前所述，新的先验概率通过将特定高斯分布的后验概率之和除以案例数量来计算，如方程 19.7 所示。"

"This means that a Gaussian for which many cases have a large posterior probability, will have a large prior probability."

Translate: "这意味着，后验概率大的案例较多的高斯分布会拥有更大的先验概率。"

"Conversely, a Gaussian for which few cases have a large posterior, will have a small prior probability."

Translate: "相反，后验概率大的案例较少的高斯分布会拥有较小的先验概率。"

"You can think of this as a soft or probabilistic equivalent to setting the prior equal to the proportion of cases belonging to each Gaussian."

Translate: "你可以把这视为一种软化或概率化的方式，即将先验设置为属于每个高斯分布的案例比例。"

**EQUATION 19.7** => **公式 19.7**.

"Once the maximization step is complete, we perform another iteration of the expectation step, this time computing the posterior probabilities for each case under the new Gaussians."

Translate: "在最大化步骤完成后，我们再次执行期望步骤，这次计算在新高斯分布下每个案例的后验概率。"

"Once this is done, we then re-run the maximization step, once again updating the means, variances, and priors for each Gaussian based on the posteriors."

Translate: "完成后，我们再次运行最大化步骤，继续根据后验概率更新每个高斯分布的均值、方差和先验。"

"![](img/a22105d68c35e8d5bd3c7bafb4644881_486_0.png)"

Keep image link unchanged.

"**Figure 19.1** The expectation-maximization algorithm for two, 1-dimensional Gaussians. Circles represent cases along a number line. Two Gaussians are randomly initialized along the line. In the expectation step, the posterior probability of each case for each Gaussian is calculated (indicated by shading). In the maximization step, the means, variances, and priors for each Gaussian are updated based on the calculated posteriors. The process continues until the likelihood converges."

Translate: "**图 19.1** 两个一维高斯的期望-最大化算法。圆点表示数轴上的案例。两个高斯随机初始化在数轴上。在期望步骤中，计算每个案例对每个高斯的后验概率（由阴影指示）。在最大化步骤中，根据计算出的后验概率更新每个高斯的均值、方差和先验。过程持续进行，直到似然收敛。"

"### 19.1.3 What if we have more than one variable?"

Translate: "### 19.1.3 如果我们有多于一个变量呢？"

"In this section I’ll extend what we learned about how the EM algorithm works in one dimension, to when we are clustering over multiple dimensions."

Translate: "在本节中，我将把我们在一维情况下学到的 EM 算法原理扩展到多维聚类的情形。"

"It is rare to come across a univariate (one-dimensional) clustering problem."

Translate: "单维（一维）聚类问题很少出现。"

"Usually, our datasets contain multiple variables we wish to use to identify clusters."

Translate: "通常，我们的数据集包含多个变量，我们希望利用这些变量来识别聚类。"

"I limited my explanation of the EM algorithm for Gaussian mixture models in the previous section, because a univariate Gaussian has only two parameters: its mean and variance."

Translate: "我在上一节中对高斯混合模型的 EM 算法解释有限，因为单维高斯只有两个参数：均值和方差。"

"When we have a Gaussian distribution in more than one-dimension (a multivariate Gaussian), we need to describe it using its centroid, and its covariance matrix."

Translate: "当我们拥有多维高斯分布（多变量高斯）时，需要使用其均值向量（ centroid）和协方差矩阵来描述它。"

"We’ve come across centroids in previous chapters, they are simply a vector of means, one for each dimension/variable in the dataset."

Translate: "我们在之前的章节中已经了解到均值向量（centroid），它只是一个每个维度/变量的均值向量。"

"A covariance matrix is a square matrix whose elements are the covariance between variables."

Translate: "协方差矩阵是一个方阵，其元素是变量之间的协方差。"

"For example, the value in the second row, third column of a covariance matrix indicates the covariance between variables two and three in the data."

Translate: "例如，协方差矩阵第二行第三列的值表示数据中变量二和变量三之间的协方差。"

"Covariance is an unstandardized measure of how much two variables change together."

Translate: "协方差是一个未标准化的度量，用于衡量两个变量共同变化的程度。"

"A positive covariance means that as one variable increases, so does the other."

Translate: "正协方差表示一个变量增加时，另一个变量也会增加。"

"A negative covariance means that as one variable increases, the other decreases."

Translate: "负协方差表示一个变量增加时，另一个变量会减少。"

"A covariance of zero usually indicates no relationship between the variables at all."

Translate: "协方差为零通常表示变量之间没有任何关系。"

"We can calculate the covariance between two variables using equation 19.8."

Translate: "我们可以使用方程 19.8 计算两个变量之间的协方差。"

**EQUATION 19.8** => **公式 19.8**.

Equation unchanged.

"> While covariance is an unstandardized measure of the relationship between two variables, correlation is a standardized measure of the relationship between two variables."

Translate: "> 与协方差不同，相关系数是对两个变量关系的标准化度量。"

"We can convert covariance into correlation by dividing it by the product of the variables' standard deviations."

Translate: "我们可以通过将协方差除以变量的标准差乘积来将其转换为相关系数。"

"The covariance between one variable and itself is simply that variable’s variance."

Translate: "一个变量与自身的协方差等同于该变量的方差。"

"Therefore, the diagonal elements of a covariance matrix are variances of each of the variables."

Translate: "因此，协方差矩阵的对角线元素是每个变量的方差。"

"> In fact, covariance matrices are often called variance-covariance matrices for this reason."

Translate: "> 事实上，协方差矩阵常被称为方差-协方差矩阵，正因于此。"

"So if the EM algorithm only estimated a variance for each Gaussian, in each dimension, the Gaussians would be perpendicular to the axes of the feature space."

Translate: "因此，如果 EM 算法仅在每个维度上估计每个高斯的方差，高斯会与特征空间的坐标轴垂直。"

"Put another way, it would force the model to assume there were no relationships between the variables in the data."

Translate: "换句话说，这将迫使模型假设数据中的变量之间没有关系。"

"It’s usually more sensible to assume there will be some degree of relationship between the variables, and so estimating the covariance matrix allows the Gaussians to lie diagonally across the feature space."

Translate: "通常更合理的做法是假设变量之间存在一定程度的关系，因此估计协方差矩阵使得高斯能够在特征空间中呈对角线分布。"

"> As we estimate the covariance matrix, this means that Gaussian mixture model clustering is insensitive to variables on different scales."

Translate: "> 随着我们估计协方差矩阵，这意味着高斯混合模型聚类对不同尺度的变量不敏感。"

"Therefore, we don’t need to scale our variables before training the model."

Translate: "因此，我们在训练模型前无需对变量进行标准化。"

"So when we’re clustering over more than one dimension, the EM algorithm randomly initializes the centroid, covariance matrix, and prior for each Gaussian."

Translate: "因此，在多维聚类时，EM 算法会随机初始化每个高斯的均值向量（centroid）、协方差矩阵和先验概率。"

"It then calculates the posterior probability for each case, for each Gaussian in the expectation step."

Translate: "随后，它在期望步骤中计算每个案例对每个高斯的后验概率。"

"In the maximization step, the centroid, covariance matrix, and prior probability are updated for each Gaussian."

Translate: "在最大化步骤中，每个高斯的均值向量、协方差矩阵和先验概率会被更新。"

"The EM algorithm continues to iterate until either the maximum number of iterations is reached, or the algorithm reaches convergence."

Translate: "EM 算法会持续迭代，直到达到最大迭代次数或算法收敛为止。"

"The EM algorithm for a bivariate case is illustrated in figure 19.2."

Translate: "双变量（二维）情况下的 EM 算法在图 19.2 中示例。"

Now we need to wrap everything in [content]...[/content].

Check for any bold/italic/links: we have **EQUATION 19.3**, **EQUATION 19.4**, **EQUATION 19.5**, **EQUATION 19.6**, **EQUATION 19.7**, **Figure 19.1**, **Figure 19.2**? The figure caption includes **Figure 19.1** which is bold. Should translate to **图 19.1**? In example they kept bold for "Figure 19.1"? In example they had "**Figure 19.1** The expectation-maximization algorithm..." and translation kept "**图 19.1** The expectation-maximization algorithm..." So we need to keep bold markers and translate the word "Figure". So **图 19.1**.

Similarly **Figure 19.2** => **图 19.2**.

Also there is "**EQUATION 19.3**" etc. Should translate to **公式 19.3** etc.

Check for any italic: there are none besides maybe *itatic* in note but not in text. In the text there is "*hard to forget*" but not present. So no italic.

Check for inline code: there is `$x_i$`, `$k$`, `$j$`, `$p(k\mid x_i)$`, etc. Those are math delimiters, not inline code. Inline code is like `` `code` ``. There's none. The code block is a fenced code block with python-like code, we keep unchanged.

Check for links: none.

Check for list items: there are no bullet list items, just paragraphs and headings.

Check for tables: none.

Check for quote blocks: there is a blockquote (">") but we keep as is, just translate the content.

Check for headings: "### 19.1.2 The EM algorithm: expectation and maximization steps" => translate heading.

"### 19.1.3 What if we have more than one variable?" => translate.

Make sure to keep line breaks exactly as original. Also ensure we don't miss any line.

Now produce final answer with [content] ... 