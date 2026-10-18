

## 17. 感知机学习算法

从数学上讲，感知机学习算法如下。对于每个权重 `wj`：`wj ← wj + η (t − y) xj`，其中 `t` 是给定输入的正确输出（1 或 0），`y` 是感知机的实际输出，`xj` 是与权重 `wj` 关联的输入，而 `η` 是 `learning rate`，由程序员给出的值。箭头表示更新。阈值通过创建一个额外的“输入” `x[0]` 来纳入，其恒定值为 1，其关联权重 `w[0] = −threshold`。有了这个额外的输入和权重（称为偏置），只有当输入乘以权重的总和（即输入向量与权重向量之间的点积）大于或等于 0 时，感知机才会触发。通常，输入值会被缩放并应用其他变换，以防止权重增长过大。

## 18. 参考文献

引自 M. Olazaran，“A Sociological Study of the Official History of the Perceptrons Controversy，”*Social Studies of Science* 26，no. 3 (1996)：611–59。

## 19. 参考文献

M. A. Boden，*Mind as Machine: A History of Cognitive Science*（Oxford: Oxford University Press, 2006），2:913。

## 20. 参考文献

M. L. Minsky 和 S. L. Papert，*Perceptrons: An Introduction to Computational Geometry*（Cambridge, Mass.: MIT Press, 1969）。

## 21. 布尔函数

从技术角度讲，任何布尔函数都可以由具有线性阈值单元和一个内部（“隐藏”）层的完全连接多层网络来计算。

## 22. 参考文献

Olazaran，“Sociological Study of the Official History of the Perceptrons Controversy。”

## 23. 参考文献

G. Nagy，“Neural Networks—Then and Now，”*IEEE Transactions on Neural Networks* 2，no. 2 (1991)：316–18。

## 24. 参考文献

Minsky 和 Papert，*Perceptrons*，231–32。

## 25. 参考文献

J. Lighthill，“Artificial Intelligence: A General Survey，”载于 *Artificial Intelligence: A Paper Symposium*（London: Science Research Council, 1973）。

## 26. 参考文献

引自 C. Moewes 和 A. Nürnberger，*Computational Intelligence in Intelligent Data Analysis*（New York: Springer, 2013），135。

## 27. 参考文献

M. L. Minsky，*The Society of Mind*（New York: Simon & Schuster, 1987），29。

## 2: 神经网络与机器学习的兴起

### 1. 激活值

每个隐藏单元和输出单元的激活值 `y` 通常通过计算输入到该单元的向量 `x` 与连接到该单元的权重向量 `w` 之间的点积，并对结果应用 Sigmoid 函数来计算：`y = 1/(1 + e^(−()x.w^))`。`x` 和 `w` 向量还包括“偏置”权重和激活值。如果单元具有非线性输出函数（例如 Sigmoid），则只要有足够的隐藏单元，网络就可以以任何所需的近似程度计算任何函数（有最小限制）。这一事实称为通用近似定理。有关更多详细信息，请参见 M. Nielsen，*Neural Networks and Deep Learning*，neuralnetworksanddeeplearning.com。

### 2. 反向传播

对于具有一定微积分背景的读者：反向传播是一种 `gradient descent`，它近似了网络中每个权重 `w` 在“误差曲面”上最陡下降的方向。该方向是通过计算误差函数（例如，输出与目标之间差值的平方）相对于权重 `w` 的梯度来计算的。例如，考虑从输入单元 `i` 到隐藏单元 `h` 的连接上的权重 `w`。权重 `w` 沿最陡下降方向进行修改，其幅度由传播到单元 `h` 的误差、单元 `i` 的激活值以及用户定义的 `learning rate` 决定。有关反向传播的深入解释，我推荐 Michael Nielsen 编写的免费在线书籍 *Neural Networks and Deep Learning*。

### 3. 网络权重

在我的网络中，有 324 个输入、50 个隐藏单元和 10 个输出单元，从输入到隐藏层有 324 × 50 = 16,200 个权重，从隐藏层到输出层有 50 × 10 = 500 个权重，总共 16,700 个权重。

### 4. 参考文献

D. E. Rumelhart, J. L. McClelland, and the PDP Research Group, *Parallel Distributed Processing: Explorations in the Microstructure of Cognition* (Cambridge, Mass.: MIT Press, 1986), 1:3.

### 5. 参考文献

同上，113。

### 6. 参考文献

引自 C. Johnson，“Neural Network Startups Proliferate Across the U.S.,” *The Scientist*, Oct. 17, 1988。

### 7. 参考文献

A. Clark, *Being There: Putting Brain, Body, and World Together Again* (Cambridge, Mass.: MIT Press, 1996), 26.

### 8. GOFAI

正如 Douglas Hofstadter 指出的那样，语法正确的版本是“good old old-fashioned AI”，但 GOOFAI 不像 GOFAI 那样朗朗上口。

## 3: AI 春天

### 1. 参考文献

Q. V. Le et al., “Building High-Level Features Using Large-Scale Unsupervised Learning,” in *Proceedings of the International Conference on Machine Learning* (2012), 507–14.

### 2. 参考文献

P. Hoffman, “Retooling Machine and Man for Next Big Chess Faceoff,” *New York Times*, Jan. 21, 2003.

### 3. 参考文献

D. L. McClain, “Chess Player Says Opponent Behaved Suspiciously,” *New York Times*, Sept. 28, 2006.

### 4. 参考文献

引自 M. Y. Vardi, “Artificial Intelligence: Past and Future,” *Communications of the Association for Computing Machinery* 55, no. 1 (2012): 5.

### 5. 参考文献

K. Kelly, “The Three Breakthroughs That Have Finally Unleashed AI on the World,” *Wired*, Oct. 27, 2014.

### 6. 参考文献

J. Despres, “Scenario: Shane Legg,” *Future*, accessed Dec. 4, 2018, future.wikia.com/wiki/Scenario:\_Shane\_Legg.

### 7. 参考文献

引自 H. McCracken, “Inside Mark Zuckerberg’s Bold Plan for the Future of Facebook,” *Fast Company*, Nov. 16, 2015, [www.fastcompany.com/3052885/mark-zuckerberg-facebook](http://www.fastcompany.com/3052885/mark-zuckerberg-facebook).

### 8. 参考文献

V. C. Müller 和 N. Bostrom, “Future Progress in Artificial Intelligence: A Survey of Expert Opinion,” 载于 *Fundamental Issues of Artificial Intelligence*, ed. V. C. Müller (Cham, Switzerland: Springer International, 2016), 555–72.

### 9. 参考文献

M. Loukides 和 B. Lorica, “What Is Artificial Intelligence?,” *O’Reilly*, June 20, 2016, [www.oreilly.com/ideas/what-is-artificial-intelligence](http://www.oreilly.com/ideas/what-is-artificial-intelligence).

### 10. 参考文献

S. Pinker, “Thinking Does Not Imply Subjugating,” 载于 *What to Think About Machines That Think*, ed. J. Brockman (New York: Harper Perennial, 2015), 5–8.

### 11. 参考文献

A. M. Turing, “Computing Machinery and Intelligence,” *Mind* 59, no. 236 (1950): 433–60.

### 12. 参考文献

J. R. Searle, “Minds, Brains, and Programs,” *Behavioral and Brain Sciences* 3, no. 3 (1980): 417–24.

### 13. 参考文献

J. R. Searle, *Mind: A Brief Introduction* (Oxford: Oxford University Press, 2004), 66.

### 14. AI 术语

术语 `strong AI` 和 `weak AI` 也被用来表示类似于 `general AI` 和 `narrow AI` 的含义。Ray Kurzweil 就是这样使用它们的，但这与 Searle 的原始含义不同。

