

## 8.11 张量分解方法

连通性分析中的另一种有趣方法是*链路预测*，它不仅提供了一种连通性度量，还能追踪网络中节点间链路的变化。链路预测问题出现在由多种关系类型连接的对象群组中。解决方案不仅应允许识别相关性（在链接模式之间），还应揭示各种关系对预测性能的影响。

在文献[\[75\]](#c08.xhtml#c8-bib-0075)中，继文献[\[76\]](#c08.xhtml#c8-bib-0076)的工作之后，假设对象倾向于与具有相似特征的其他对象形成链路，且相关对象共享相似的行为模式。为了构建链路模式预测，考虑一组*N*个对象*X* = {*x* [1], *x* [2], …, *x*[*N*] }，并假设由一组*T*个轨迹矩阵[\[75\]](#c08.xhtml#c8-bib-0075)定义的对象对之间存在*T*种不同类型的关系。随后定义一个*N* × *N* × *T*的张量**Y**，其元素*y*[*i*, *j*, *t*]表示对象对*x*[*i*]和*x*[*j*]之间类型*t*的关系值，定义如下[\[75\]](#c08.xhtml#c8-bib-0075)：

对于 ∀*i,j* ∈ \[1,… *N*\]² 和 ∀*t* ∈ \[1, …, *T*\]

(8.53)![equation](images/c8-disp-0056.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>y</mi><mrow><mi>i</mi><mo>,</mo><mi>j</mi><mo>,</mo><mi>t</mi></mrow></msub><mo>=</mo><mfenced open="{" close=""><mtable><mtr><mtd><maligngroup/><malignmark/><mn>1</mn><mspace width="1em"/><mtext>if</mtext><mspace width="0.2em"/><msub><mi>x</mi><mi>i</mi></msub><mspace width="0.2em"/><mtext>links to</mtext><mspace width="0.2em"/><msub><mi>x</mi><mi>j</mi></msub><mspace width="0.2em"/><mi>by</mi><mspace width="0.2em"/><mtext>relation type</mtext><mspace width="0.2em"/><mi>t</mi></mtd></mtr><mtr><mtd><maligngroup/><malignmark/><mn>0</mn><mspace width="1em"/><mtext>otherwise</mtext></mtd></mtr></mtable></mfenced></math>

基于此，**Y** [(*i,j*,:)] 被定义为涉及对象*x*[*i*]和*x*[*j*]之间*T*种不同关系类型的*链路模式*。此处待解决的问题是：给定多关系网络中一部分相关对象的观测链路模式信息，如何找到其余对象对的未观测链路模式？[图 8.8](#c08.xhtml#c8-fig-0008) 给出了该问题及其张量模型的一个示例[\[77\]](#c08.xhtml#c8-bib-0077)。

为了用数学方式表达该问题，考虑一个非负的*N* × *N*矩阵**W**，使得其元素*w*[*i,j*]对于 ∀*i,j*∈\[1,…, *N*\]² 定义如下[\[75\]](#c08.xhtml#c8-bib-0075)：

[(8.54)](#c08.xhtml#R_c8-disp-0057)![equation](images/c8-disp-0057.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>w</mi><mrow><mi>i</mi><mo>,</mo><mi>j</mi></mrow></msub><mo>=</mo><mfenced open="{" close=""><mtable><mtr><mtd><maligngroup/><malignmark/><mn>1</mn><mspace width="1em"/><mtext>if link pattern between</mtext><mspace width="0.2em"/><msub><mi>x</mi><mi>i</mi></msub><mspace width="0.2em"/><mtext>and</mtext><mspace width="0.2em"/><msub><mi>x</mi><mi>j</mi></msub><mspace width="0.2em"/><mtext>is known</mtext></mtd></mtr><mtr><mtd><maligngroup/><malignmark/><mn>0</mn><mspace width="1em"/><mtext>if link pattern between</mtext><mspace width="0.2em"/><msub><mi>x</mi><mi>i</mi></msub><mspace width="0.2em"/><mtext>and</mtext><mspace width="0.2em"/><msub><mi>x</mi><mi>j</mi></msub><mspace width="0.2em"/><mtext>is missing</mtext></mtd></mtr></mtable></mfenced></math>

对于分解，定义了以下损失函数：

[(8.55)](#c08.xhtml#R_c8-disp-0058)![equation](images/c8-disp-0058.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>L</mi><mfenced open="(" close=")"><munder accentunder="false"><mi mathvariant="bold-italic">X</mi><mo>\_</mo></munder></mfenced><mo>=</mo><munderover><mo>&#8721;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>N</mi></munderover><munderover><mo>&#8721;</mo><mrow><mi>j</mi><mo>=</mo><mn>1</mn></mrow><mi>N</mi></munderover><msub><mi>w</mi><mrow><mi>i</mi><mo>,</mo><mi>j</mi></mrow></msub><msup><mfenced open="&#8214;" close="&#8214;"><mrow><msub><mi>y</mi><mrow><mi>i</mi><mo>,</mo><mi>j</mi><mo>,</mo><mo>:</mo></mrow></msub><mo>&#8722;</mo><msub><mi>x</mi><mrow><mi>i</mi><mo>,</mo><mi>j</mi><mo>,</mo><mo>:</mo></mrow></msub></mrow></mfenced><mn>2</mn></msup><mspace width="0.2em"/></math> ![Figure 8.8 Example of modelling the multirelational social network as a tensor for predicting the unobserved link patterns in the network. To the right is the tensor representation of the network where each slice matrix represents one relation type and each tube fibre represents the link pattern between two nodes. Unknown link patterns are represented as ‘?’ fibres.](images/c08f008.gif)

[**图 8.8**](#c08.xhtml#R_c8-fig-0008) 将多关系社交网络建模为张量以预测网络中未观测链路模式的示例。右侧是网络的张量表示，其中每个切片矩阵代表一种关系类型，每个管状纤维代表两个节点之间的链路模式。未知链路模式用‘？’纤维表示。

其中 ||. || 表示张量的 Frobenius 范数。遵循规范分解 (CANDECOMP)/PARAFAC (CP) 张量分解和公式 [(8.55)](#c08.xhtml#c8-disp-0058)，我们可以使用共轭梯度法求解以下优化问题[\[75\]](#c08.xhtml#c8-bib-0075)：

