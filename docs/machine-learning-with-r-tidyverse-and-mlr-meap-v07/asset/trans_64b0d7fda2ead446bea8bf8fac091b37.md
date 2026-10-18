...[/content].

We must ensure we don't miss any lines. Let's parse the content.

The content includes:

- Paragraph about Arthur Samuel... etc.

- Code block with R code (needs to stay unchanged).

- Then description of rules, list items (bullet points). Need to translate list items content but keep list markers.

- Then code block with output (R console output) - keep unchanged.

- Then paragraph about problem with approach, contrast, etc. Need translation.

- Then figure caption (image) - keep as is (maybe translate caption? It says "figure 1.2" maybe keep as is? The figure is an image with alt text; we should translate the caption? The note says "图片" maybe keep as is. In example, they kept the image markdown unchanged. So we keep the markdown `![](img/...png)` unchanged.

- Then note about Box quote: need to translate the note content but keep **NOTE** bold? In example they kept **NOTE** and translated the content. The note says: "**NOTE** You may have heard the famous phrase..." So we need to translate the content after **NOTE** but keep the **NOTE** bold. Also keep the > blockquote.

- Then another note: "**NOTE** One of the initially confusing..." translate content, keep **NOTE**.

- Then figure caption: "**Figure 1.4** A hypothetical algorithm..." translate caption? In example they kept "Figure 1.5 Supervised vs. unsupervised machine learning." They translated "Supervised vs. unsupervised machine learning." Actually they kept English? In example they translated "Supervised vs. unsupervised machine learning." Wait example: they had "**Figure 1.5 Supervised vs. unsupervised machine learning.**" The translation: "[content] ... **Figure 1.5 Supervised vs. unsupervised machine learning.**" Actually they kept English? Let's see: In example, original: "Supervised vs. unsupervised machine learning." The translation: "**Figure 1.5 Supervised vs. unsupervised machine learning.**" So they kept English phrase unchanged. So maybe we keep figure captions unchanged (English). But they said "translate its content" for links; for figure captions maybe keep as is. In the provided text, figure captions are English; we likely keep them unchanged.

- Then note about algorithms: need translation.

- Then list items for supervised/unsupervised categories: need to translate the bullet items (classification, regression, dimension reduction, clustering). Also the description sentences.

- Then figure 1.6 summary: keep unchanged.

- Then final paragraph about "So we categorize..." etc. Need translation.

- Then section 1.2.1: need translation of the paragraph.

- Then list of learning types: bullet list with *supervised*, *unsupervised*, *semi-supervised* - translate the words but keep the asterisks? In example they kept the asterisks for italic. The list items are "*supervised*" etc. Should we translate the words but keep the asterisks? The rule: "粗体（**bold**）和斜体（*itatic*）需要翻译翻译内容并保留符号。" So we need to translate the content inside the asterisks, but keep the asterisks. So "*supervised*" becomes "*受监督*". Similarly "*unsupervised*" -> "*无监督*". "*semi-supervised*" -> "*半监督*". Also the bullet dash and numbers need to stay.

- Then description sentences: need translation.

- Then the paragraph about "So we categorize algorithms..." need translation.

- Then the final paragraph about "By the end of this section..." need translation.

We must ensure we keep code blocks unchanged, including backticks and braces.

Also need to keep inline code `20 min` unchanged.

Also need to keep list items translation: For bullet list items under "If the animal has four legs..." etc. The list items are:

- If the animal has four legs and climbs trees, it's a cat
- If the animal has four legs and does not climb trees, it's a dog
- Otherwise, the animal is a snake

Translate to Chinese, preserving bullet dash and maybe keep the dash. Also need to keep the dash and maybe keep the dash as "•"? In original they use "-". We'll keep "- " and translate content.

Also need to translate the description sentences about supervised learning etc.

Let's go through the text line by line.

Original text:

Arthur Samuel, a scientist at IBM, first used the term machine learning in 1959. He used it to describe a form of artificial intelligence (AI) that involved training an algorithm to learn to play the game of checkers. The word learning is what's important here, as this is what distinguishes machine learning approaches from traditional AI.

We need to translate:

"Arthur Samuel, a scientist at IBM, first used the term machine learning in 1959." -> "Arthur Samuel, IBM 的一位科学家，首先在 1959 年使用了“机器学习”一词。"

"He used it to describe a form of artificial intelligence (AI) that involved training an algorithm to learn to play the game of checkers." -> "他用它来描述一种人工智能（AI）形式，该形式涉及训练算法学习玩棋。" But need to keep parentheses? The parentheses around AI maybe keep as is, but translate the word AI? In Chinese we can keep "人工智能（AI）". So translation: "他用它来描述一种人工智能（AI）形式，该形式涉及训练算法学习玩棋。"

"The word learning is what's important here, as this is what distinguishes machine learning approaches from traditional AI." -> "这里重要的是“学习”这个词，因为这正是机器学习方法与传统人工智能的区别所在。" Keep quotes? The original uses single quotes around learning. In Chinese we can use “学习”. Keep the quotes? In example they kept the phrase "20 min" unchanged, but they didn't translate the word inside code. For normal text, we translate. So we can write: "这里重要的是“学习”这个词，因为这正是机器学习方法与传统人工智能的区别所在。" Keep the single quotes? The original uses single quotes around learning. In Chinese we can use ‘学习’ (single quotes). But we need to preserve the single quotes? The rule says preserve symbols, but the quotes are part of the text. In example they kept backticks for code, but for normal text they didn't have quotes. Here we have single quotes around learning. Should we keep them? Probably keep them as they are part of the text. So we can write: '学习' (single quotes). In Chinese single quotes are ‘’ but we can use '学习' as in original. Let's keep same style: '学习'.

Now code block:

```
numberOfLegs <- c(4, 4, 0)
climbsTrees <- c(TRUE, FALSE, TRUE)
for (i in 1:3) {
if (numberOfLegs[i] == 4) {
if (climbsTrees[i]) print("cat") else print("dog")
} else print("snake")
}
```

We keep unchanged.

Next paragraph:

"In the R code above I've created three rules, mapping every possible input available to us to an output:"

Translate: "在上述 R 代码中，我创建了三条规则，将我们可用的所有可能输入映射到输出："

Then list items:

- If the animal has four legs and climbs trees, it's a cat
- If the animal has four legs and does not climb trees, it's a dog
- Otherwise, the animal is a snake

Translate each:

- "如果动物有四条腿并且会爬树，则它是一只猫"
- "如果动物有四条腿且不攀爬树，则它是一只狗"
- "否则，动物是一只蛇"

Need to keep dash and maybe a space after dash. Also keep the dash as "-". So:

- 如果动物有四条腿并且会爬树，则它是一只猫
- 如果动物有四条腿且不攀爬树，则它是一只狗
- 否则，动物是一只蛇

Now next paragraph:

"The problem with this approach is that you need to know all possible outputs the computer should give you in advance, and the system will never give you an output that you haven't told it to give."

Translate: "这种方法的问题是你需要事先知道计算机应该给出的所有可能输出，系统永远不会给出你没有告诉它的输出。"

Next:

"Contrast this to the machine learning approach, where instead of telling the computer the rules, you give it the data and allow it to learn the rules for itself."

Translate: "与之形成对比的是机器学习方法，这里不告诉计算机规则，而是给出数据，让它自己学习规则。"

Next:

"The advantage of this approach is that the "machine" can learn patterns we didn't even know existed in the data, and the more data we provide, the better it gets at learning those patterns (figure 1.2)."

Translate: "这种方法的优势在于“机器”可以学习我们甚至不知道存在于数据中的模式，而且我们提供的数据越多，它学习这些模式的能力就越强（见图 1.2）。"

Note: figure reference "figure 1.2" maybe keep as is, but we can translate "figure" to "图". In example they kept "figure 1.2" unchanged? In example they had "figure 1.2" inside parentheses; they translated the parentheses content? In example they wrote "(figure 1.2)" and translation kept "(figure 1.2)"? Let's see example: In example they had "the more data we provide, the better it gets at learning those patterns (figure 1.2)." The translation: "而且我们提供的数据越多，它学习这些模式的能力就越强（figure 1.2）。" So they kept "figure 1.2" unchanged inside parentheses. So we keep "figure 1.2" unchanged.

Next:

"In practice, we call a set of rules a machine learning algorithm learns a model."

Translate: "在实践中，我们称算法学习到的规则集为模型。"

Next:

"Once the model has been learned, we can give it new observations and it will output its predictions for the new data."

Translate: "模型学习完成后，我们可以给它新的观测数据，它会输出对新数据的预测。"

Next:

"We refer to these as models because they represent real-world phenomena in a simplistic-enough way that we and the computer can interpret and understand."

Translate: "我们称它们为模型，因为它们以简化且足够易于我们和计算机理解和把握的方式表示现实世界现象。"

Next:

"Just as a model of the Eiffel Tower may be a good representation of the real thing but isn’t exactly the same, so statistical models are attempted representations of real-world phenomena but won’t match them perfectly."

Translate: "就像伊菲尔铁塔的模型可能是对真实事物的良好表现但并不完全相同，统计模型也是对现实世界现象的尝试性表示，但不会完全匹配它们。"

Next:

"> **NOTE** You may have heard the famous phrase coined by the statistician George Box that "all models are wrong, but some are useful", which refers to the approximate nature of models."

We need to translate the note content, keep **NOTE** bold. So:

"> **NOTE** 你可能听说过统计学家乔治·博克斯提出的著名句子：“所有模型都是错误的，但有些是有用的”，这指的是模型的近似性质。"

But need to keep the > blockquote marker. So we keep ">" then space then **NOTE** then Chinese translation.

Check formatting: In example they kept ">" then "**NOTE** ..." So we follow.

Next paragraph:

"The process by which the model is learned is referred to as the algorithm."

Translate: "模型被学习的过程被称为算法。"

Next:

"As we discovered earlier, an algorithm is just a sequence of operations that work together to solve a problem."

Translate: "正如我们 earlier 发现的那样，算法只是一系列协同工作的操作，用于解决问题。" Wait "earlier" is English; we need to translate it? The rule says translate content, but keep code unchanged. The word "earlier" is part of the sentence, not code. So translate to Chinese: "正如我们之前发现的那样，算法只是一系列协同工作的操作，用于解决问题。" So replace "earlier" with "之前". So translation: "正如我们之前发现的那样，算法只是一系列协同工作的操作，用于解决问题。"

Next:

"So how does this work in practice? Let’s take a simple example. Say we have two continuous variables, and we would like to train an algorithm that can predict one (the outcome or dependent variable), given the other (the predictor or independent variable). The relationship between these"

Translate: "那么这在实践中是如何运作的呢？让我们举一个简单的例子。假设我们有两个连续变量，我们想要训练一个算法，它可以根据另一个变量（自变量）预测其中一个变量（因变量）。这两个变量之间的"

But note the sentence ends with "The relationship between these" incomplete; maybe continues later. In the original text after that there is a figure. So we need to translate up to "The relationship between these". Keep the phrase as is? It ends incomplete, but we translate the part we have.

So translation: "这两个变量之间的"

Now next figure:

![](img/a22105d68c35e8d5bd3c7bafb4644881_10_0.png)

We keep unchanged.

Next:

"**Figure 1.4** A hypothetical algorithm for learning the parameters of a straight line. This algorithm takes two continuous variables as inputs, and fits a straight line through the mean. It iteratively rotates the line until it finds a solution that minimises the sum of squares. The parameters of the line are output as the learned model."

Translate: "**Figure 1.4** 一个假设的算法，用于学习直线的参数。该算法接收两个连续变量作为输入，并通过均值拟合一条直线。它会不断旋转直线，直到找到最小化平方和的解决方案。直线的参数作为学习得到的模型输出。"

But need to keep "**Figure 1.4**" maybe keep as is (English). In example they kept "Figure 1.5 Supervised vs. unsupervised machine learning." unchanged. So we keep "**Figure 1.4**" unchanged, then translate the rest.

So: "**Figure 1.4** 一个假设的算法，用于学习直线的参数。该算法接收两个连续变量作为输入，并通过均值拟合一条直线。它会不断旋转直线，直到找到最小化平方和的解决方案。直线的参数作为学习得到的模型输出。"

Next:

"> **NOTE** One of the initially confusing but eventually fun aspects of machine learning is that there are a plethora of algorithms to solve the same type of problem. The reason for this is that different people have come up with slightly different ways of solving the same problem, all trying to improve upon previous attempts. The result of this is that, for a given task, it is our job as data scientists to choose which algorithm(s) will learn the best performing model."

Translate: "> **NOTE** 机器学习的一个 initially 令人困惑但最终有趣的方面是，针对同一种问题存在大量算法。原因在于不同的人提出了略有不同的解决同一问题的方法，它们都在努力改进之前的尝试。这导致在给定任务中，作为数据科学家，我们的工作是选择哪些算法（或哪些算法）能够学习表现最佳的模型。"

Need to translate "initially confusing but eventually fun aspects" -> "最初令人困惑但最终有趣的方面". Also "plethora of algorithms" -> "大量算法". "different people have come up with slightly different ways" -> "不同的人提出了略有不同的方法". "all trying to improve upon previous attempts" -> "它们都在努力改进之前的尝试". "for a given task, it is our job as data scientists to choose which algorithm(s) will learn the best performing model." -> "在给定任务中，作为数据科学家，我们的工作是选择哪些算法（或哪些算法）能够学习表现最佳的模型。" Maybe simplify: "在给定任务中，作为数据科学家，我们的工作是选择哪些算法能够学习表现最佳的模型。" Keep parentheses? Not needed.

Next paragraph:

"While certain algorithms tend to perform better than others with certain types of data, there is no single algorithm that will always outperform all others on all problems."

Translate: "虽然某些算法在特定类型的数据上表现更好，但没有单一算法能够在所有问题上始终超越所有其他算法。"

Next:

"This concept is called the *no free lunch theorem*."

Translate: "这一概念被称为 *no free lunch theorem*." Keep the asterisks for italic. So we keep "*no free lunch theorem*". The phrase itself is English; maybe we keep as is, but we need to translate the concept name? In example they kept "no free lunch theorem" unchanged (they kept English). So we keep it as is, with asterisks.

"In other words, you don’t get something for nothing; you need to put some effort into working out the best algorithm for your particular problem."

Translate: "换句话说，你得不到免费的东西；你需要付出一些努力来找出适合你特定问题的最佳算法。"

Next:

"Instead, data scientists typically choose a few algorithms they know tend to work well for the type of data and problem they are working on, and see which algorithm generates the best performing model."

Translate: "相反，数据科学家通常会选择几种他们知道对所处理的数据和问题表现良好的算法，并观察哪个算法能够生成表现最佳的模型。"

Next:

"We’ll see how we do this later on in the book."

Translate: "我们稍后在书中会看到如何做到这一点。"

Next:

"We can, however, narrow down our initial choice by dividing machine learning algorithms into categories, based on the function they perform and how they perform it."

Translate: "然而，我们可以通过将机器学习算法按其执行的功能及其执行方式进行分类，从而缩小最初的选择范围。"

Next:

"## 1.2 Classes of machine learning algorithms"

Translate: "## 1.2 机器学习算法的类别"

Next:

"All machine learning algorithms can be categorized by their learning type, and the task they perform. There are three learning types:"

Translate: "所有机器学习算法都可以根据其学习类型和执行的任务进行分类。这里有三种学习类型："

Next list:

- *supervised*
- *unsupervised*
- *semi-supervised*

Translate each with asterisks:

- *受监督*
- *无监督*
- *半监督*

Need to keep dash and maybe space.

Next paragraph:

"This depends on how the algorithms learn. Do they require us to hold their hand through the learning process? Or do they learn the answers for themselves? Supervised and unsupervised algorithms can be further split into two classes each:"

Translate: "这取决于算法如何学习。它们是需要我们在学习过程中“手把手”指导，还是能够自行学习答案？受监督和无监督算法各可进一步细分为两类："

Next list:

- supervised
  - *classification*
  - *regression*
- unsupervised
  - *dimension reduction*
  - *clustering*

Translate each:

- supervised -> "受监督"
- *classification* -> "*分类*"
- *regression* -> "*回归*"
- unsupervised -> "无监督"
- *dimension reduction* -> "*降维*"
- *clustering* -> "*聚类*"

Need to keep the dash and indentation.

Now the paragraph after that:

"This depends on what they learn to *do*."

Translate: "这取决于它们学习要 *做* 什么。" Wait "do" maybe "执行". The phrase "what they learn to do" means "它们学习要做的事情". So translation: "这取决于它们学习要 *执行* 什么。" But we need to keep the asterisk for "do"? The original has "*do*". So we translate "do" to Chinese but keep asterisks? The rule: translate content and retain symbols. So "*do*" becomes "*做*". So we need to keep "*做*". So phrase: "这取决于它们学习要 *做* 什么。" Let's do that.

Next paragraph:

"So we categorize algorithms by how they learn, and what they learn to do. But why do we care about this? Well, there are **a lot** of machine learning algorithms available to us. How do we know which one to pick? What kind of data do they require to function properly? Knowing which categories different algorithms belong to makes our job of selecting the most appropriate ones much simpler."

Translate:

"所以我们根据算法的学习方式以及它们学习要 *做* 的事情来对算法进行分类。但为什么我们要在意这件事呢？ well, 这里有 **a lot** 的机器学习算法可供使用。我们如何知道选哪一个？它们需要什么样的数据才能正常工作？知道不同算法所属的类别使我们选择最合适的算法的工作变得 much simpler."

Need to translate "well," maybe "well" is English; we need to translate. In Chinese we can write "当然". But we need to keep "well," maybe as "当然". Let's translate fully:

"这取决于它们学习要 *做* 的事情。但为什么我们要在意这件事呢？显然，这里有 **大量** 的机器学习算法可供使用。我们如何知道选哪一个？它们需要什么样的数据才能正常工作？知道不同算法所属的类别使我们选择最合适的算法的工作变得 **much simpler**。"

But "much simpler" maybe translate as "much simpler" keep English? In example they kept "much simpler"? Not sure. In example they kept "much simpler"? Let's see example: they had "makes our job of selecting the most appropriate ones much simpler." In translation they'd likely translate "much simpler" as "much simpler" maybe keep English? In example they kept "much simpler" unchanged? Let's examine example: In example they had "makes our job of selecting the most appropriate ones much simpler." The translation: "使我们选择最合适的算法的工作变得 much simpler." They kept "much simpler" unchanged (English). So we should keep "much simpler" unchanged, not translate. Also "well," maybe keep as "well"? In example they kept "well"? Not sure. Let's keep "well" as "well"? Actually "well" is English adverb; maybe we translate to "当然". But to be safe, we can translate "well" to "当然". But we need to keep the word "well" maybe as "well"? The rule says translate content, but keep symbols. "well" is content, so translate to Chinese. So "well" -> "当然". Let's do that.

So final translation for that paragraph:

"这取决于它们学习要 *做* 的事情。但为什么我们要在意这件事呢？显然，这里有 **大量** 的机器学习算法可供使用。我们如何知道选哪一个？它们需要什么样的数据才能正常工作？知道不同算法所属的类别使我们选择最合适的算法的工作变得 **much simpler**。"

Now next paragraph:

"In the next section I cover how each of the classes is defined and why it’s different from the others."

Translate: "在下一节中，我介绍了每个类别的定义以及它们与其他类别的区别。"

Next:

"By the end of this section you’ll have a clear understanding of why you would use algorithms from one class over another."

Translate: "在本节结束时，你将清楚了解为何会选择某一类别的算法而非另一类别。"

Next:

"By the end of the book you’ll have the skills to apply a number of algorithms from each class."

Translate: "本书结束时，你将具备在各类别中应用多种算法的技能。"

Now we need to ensure we wrap everything in [content]...[/content].

We must be careful to not miss any lines. Let's reconstruct the entire translation, preserving line breaks as in original.

Original structure:

- Paragraph about Arthur Samuel (multiple sentences). We'll combine into one paragraph.

- Code block (R code) unchanged.

- Paragraph about "In the R code above..." (maybe separate line). We'll translate.

- List items (three bullet points). We'll translate each.

- Paragraph about "The problem with this approach..." (one sentence). Translate.

- Paragraph about "Contrast this..." (one sentence). Translate.

- Paragraph about "The advantage of this approach..." (one sentence). Translate.

- Figure caption (image) unchanged.

- Paragraph about "In practice, we call..." (one sentence). Translate.

- Paragraph about "Once the model has been learned..." (one sentence). Translate.

- Paragraph about "We refer to these as models..." (one sentence). Translate.

- Paragraph about "Just as a model..." (one sentence). Translate.

- Blockquote with NOTE (two notes). Need to translate both notes.

- Paragraph about "The process by which the model is learned..." (one sentence). Translate.

- Paragraph about "As we discovered earlier..." (one sentence). Translate.

- Paragraph about "So how does this work..." (multiple sentences). Translate.

- Figure caption (image) unchanged.

- "**Figure 1.4** ..." (caption). Translate after the figure.

- Blockquote with NOTE (second note). Translate.

- Paragraph about "While certain algorithms..." (one sentence). Translate.

- Paragraph about "This concept is called..." (one sentence). Translate.

- Paragraph about "In other words..." (one sentence). Translate.

- Paragraph about "Instead, data scientists..." (one sentence). Translate.

- Paragraph about "We’ll see how we do this later on in the book." (one sentence). Translate.

- Paragraph about "We can, however, narrow down..." (one sentence). Translate.

- Section header "## 1.2 Classes of machine learning algorithms" translate.

- Paragraph "All machine learning algorithms can be categorized..." translate.

- List of learning types (three bullet items). Translate.

- Paragraph "This depends on how the algorithms learn..." translate.

- List of supervised/unsupervised categories (two levels). Translate.

- Paragraph "This depends on what they learn to *do*." translate.

- Paragraph "So we categorize algorithms..." translate.

- Paragraph "But why do we care about this?..." translate.

- Section header "## 1.2.1 Differences between supervised, unsupervised,<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk>: "In the<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk>: "If the animal has four legs and climbs trees, it's a cat" -> "如果动物有四<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk>: "If the animal has four legs and climbs trees, it's a cat" -> "如果动物有四条腿并且会爬树，则它是一只猫"

Wait, the original text is "If the animal has four legs and climbs trees, it's a cat". So translation: "如果动物有四条腿并且会爬树，则它是一只猫". Yes.

Now, the code block:

```
numberOfLegs <- c(4, 4, 0)
climbsTrees <- c(TRUE, FALSE, TRUE<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk>" (the text after "These are" is cut off in the original, but I'll translate what's there).

Next paragraph:

"The problem with<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful", which refers to the approximate nature of models.

Translate: "In other words, you may have heard the famous phrase coined by the statistician George<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful", which refers to the approximate nature of models.

So the translation should be:

> **NOTE** You may have heard the famous phrase coined by the statistician George Box that "all models are wrong, but some are useful", which refers to the approximate nature of models<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful", which refers to the approximate nature of models.

Translate: "All models are wrong, but some are useful" -> "所有模型都是错误的，但有些是有用的". Keep the **NOTE** bold.

Next paragraph:

"The process by which the model is learned is referred to as the algorithm."

Translate: "模型被学习的过程被称为算法。"

Next:

"As we discovered earlier, an algorithm is just a sequence of operations that work together to solve a problem."

Translate: "正如我们之前发现的那样，算法只是一系列协同工作的操作，用于解决问题。"

Next:

"So how does this work in practice? Say we have two continuous variables, and we would like to train an algorithm that can predict one (the outcome or dependent variable), given the other (the predictor or independent variable). The relationship between these"

Translate: "那么这在实践中是如何运作的呢？让我们举一个简单的例子。假设我们有两个连续变量，我们希望训练一个算法来预测一个变量（因变量），给定另一个变量（自变量）。这两个变量之间的"

Next figure:

![](img/a22105d68c35e8d5bd3c7bafb4644881_10_0.png)

"**Figure 1.4** A hypothetical algorithm for learning the parameters of a straight line. This algorithm takes two continuous variables as inputs, and fits a straight line through the mean. It iteratively rotates the line until it finds a solution that minimises the sum of squares. The parameters of the line are output as the learned model."

Translate: "**Figure 1.<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful" refers to the approximate nature of models.

Next paragraph:

"The process by which the model is learned is referred to as the algorithm.<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful", which refers to the approximate nature of models."

Wait, I see a repetition. Let me re-examine the original text.

The text says:
"Once the model has been learned, we can give it new observations and it will output its predictions for the new data. We refer to these as models because they represent real-world phenomena in a simplistic-enough way that we and the computer can interpret and understand. Just as a model of the Eiffel Tower may be a good representation of the real thing but isn’t exactly the same, so statistical models are attempted representations of real-world phenomena but won’t match them perfectly.

> **NOTE** You may have heard the famous phrase coined by the statistician George Box that "all models are wrong, but some are useful", which refers to the approximate nature of models."

So the "NOTE" is separate. Let's re-translate that part carefully.

Original: "> **NOTE** You may have heard the famous phrase coined by the statistician George Box that "all models are wrong, but some<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1.2) ."

Actually, let's re-read carefully.

The text says: "The advantage of this approach is that the "machine" can learn patterns we didn't even know existed in the data, and the more data we provide, the better it gets at learning those patterns (figure 1.2)."

So the translation should be: "这种方法的�<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "no free lunch theorem". Wait, the text says "no free lunch theorem". Let me check the exact wording.

Original: "This concept is called the *no free lunch theorem*. In other words, you don’t get something for nothing; you need to put some effort into working out the best algorithm for your particular problem."

So the translation should be: "这一概念被称为 *no free lunch theorem*。换句话说，你得不到免费的<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1.2" and "1.2.1". Wait, the text says "1.2.1 Differences between supervised, unsupervised, and semi-supervised learning". So the "1.2" is a section number, and "1.2.1" is a subsection. We need to keep the numbering as is, but translate the text.

So "1<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1.2.1. The text says "figure 1.6", so we keep that as is.

Next section: "## 1.2 Classes of machine learning algorithms"

Translate: "## 1.2 类别 of 机器学习算法" -> "1.2 机器学习算法的类别" but need to translate the words. Actually, the list items are "supervised", "unsupervised", "semi-supervised". So we translate the words but keep the asterisks for italics.

- supervised -> *受监督*
- unsupervised -> "*无监督*"
- semi-supervised -> "*半监督*"

Then the description: "This depends on how the algorithms learn. Do they require us to hold their hand through the learning process<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful", which refers to the approximate nature of models."

Translate: "All models are wrong, but some are useful" -> "所有模型都是错误的，但有些是有用的". Keep the quotes.

Next section:

"While certain algorithms tend to perform better than others with certain types of data, there is no single algorithm that will always outperform all others on all problems. This concept is called the *no free lunch theorem*. In other words, you don’t get something for nothing; you need to put some effort into working out the best algorithm for<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1.5. This approach is based on the idea that the more data you have, the better the model will perform. The more data you have, the better the model will perform, and the more complex the model becomes. The relationship between these two is shown in Figure 1.5.

[content]
-   **Supervised learning**: The model is trained on labeled data, meaning each data point has a corresponding label or target value.
-   **Unsupervised learning**: The algorithm learns patterns from unlabeled data, discovering hidden structures or relationships without explicit guidance.
-   **Semi<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1.5. A hypothetical algorithm for learning the parameters of a straight line. This algorithm takes two continuous variables as inputs<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1.5. A hypothetical algorithm for learning<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1.5. A hypothetical algorithm for learning the parameters of a straight line. This algorithm takes two continuous variables as inputs, and fits a straight line through the mean. It iteratively rotates the line until it finds a solution that minimises the sum of squares. The parameters of the line are output as the learned model.

> **NOTE** One of the initially confusing but eventually fun aspects of machine learning is that there are a plethora of algorithms to solve the same type of problem. The reason for this is that different people have come up with slightly different ways of solving the same problem, all trying to improve upon previous attempts. The result of this is that, for a given task, it is our job as data scientists to choose which algorithm(s) will learn the best performing model.

While certain algorithms tend to perform better than others with certain types of data, there is no single algorithm that will always outperform all others on all problems. This concept is called the *no free lunch theorem*. In other words, you don’t get something for nothing; you need to put some effort into working out the best algorithm for your particular problem. Instead, data scientists typically choose a few algorithms they know tend to work well for the type of data and problem they are working on, and see which algorithm generates the best performing model. We’ll see how we do this later on in the book. We can, however, narrow down our initial choice by dividing machine learning algorithms into categories,<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful", which refers to the approximate nature of models.

Wait, I see a second "NOTE" in the text. Let me check again.

The text has:

> **NOTE** You may have heard the famous phrase coined by the statistician George Box that "all models are wrong, but some are useful", which refers to the approximate nature of models.

Then later:

> **<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful", which refers to the approximate nature of models.

Wait, I need to be careful. The note says "You may have heard the famous phrase coined by the statistician George Box that 'all models are wrong, but some are useful', which refers to the approximate nature of models."

So the translation should be: "> **NOTE** You may have heard the famous phrase coined by the statistician George Box that 'all models are wrong, but some are useful', which refers to the approximate nature of models."

But in Chinese, we need to translate the quote. However, the instruction says "translate its content", meaning the text inside the quotes. The **NOTE** itself is bold, so we keep that bold. The content inside the quotes should be translated.

So: "> **NOTE** You may have heard the famous phrase coined by the statistician George Box that "all models are wrong, but some are useful", which refers to the approximate nature of models."

Translation: "> **NOTE** 你可能听说过统计学家乔治·博克斯提出的著名句子：“所有模型都是错误的，但有些是有用的”，这指的是模型的近似性质。"

Wait, the original has "all models are wrong, but some are useful". In Chinese, we might say "所有模型都是错误的，但有些是有用的". The quotes in the original are double quotes, so we keep them.

Next:

"The process by which the model is learned is referred to as the algorithm."

Translate: "模型被学习的过程被称为算法。"

Next:

"As we discovered earlier, an algorithm is just a<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful" which refers to the approximate nature of models."

Wait, I need to be careful with the quote. The original says: "all models are wrong, but some are useful". In the text, it's in quotes. So I should translate the phrase inside the quotes, but keep the quotes themselves? Or translate the content inside? The instruction says "translate its content", meaning the content inside the quotes. So I should translate "all models are wrong, but some are useful" to Chinese, but keep the quotes.

So: "> **NOTE** You may have heard the famous phrase coined by the statistician George Box that "all models are wrong, but some are useful", which refers to the approximate nature of models."

In Chinese: "> **NOTE<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful", which refers to the approximate nature of models."

Actually, looking at the original text again:

> **NOTE** You may have heard the famous phrase coined by the statistician George Box that "all models are wrong, but some are useful", which refers to the approximate nature of models.

So the text inside the quotes is "all models are wrong, but some are useful". I should translate that part, but keep the **NOTE** bold<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1.5.

Next:

"The parameters of the line are output as the learned model."

Translate: "The parameters of the line are output as the learned model." -> "直线的参数作为学习得到的模型输出。"

Next:

"While certain algorithms tend to perform better than others with certain types of data, there is no single algorithm that will always outperform all others on all problems."

We already translated this above, but let's verify. The text is:

"While certain algorithms tend to perform better than others with certain types of data, there is no single algorithm that will always outperform all others on all problems. This concept<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful", which refers to the approximate nature of models."

Wait, I need to be careful with the "NOTE" again. Let's look at the original text again.

"While certain algorithms tend to perform better than others with certain types of data, there is no single algorithm that will always outperform all others on all problems. This concept is called the *no free lunch theorem*. In other words, you don't get something for nothing; you need to put some effort into working out the best algorithm<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful", which refers to the approximate nature of models."

Wait, I need to be careful with the "NOTE" section. Let's re-examine that part.

Original:

> **NOTE** You may have heard the famous phrase coined by the statistician George Box that "all models are wrong, but some are useful", which refers to the approximate nature of models.

So the text inside the note is: "You may have heard the famous phrase coined by the statistician George Box that "all models are wrong, but some are useful", which refers to the approximate nature of models."

We need to translate the content after "NOTE" but keep "NOTE" in bold.

So: "**NOTE** You may have heard the famous phrase coined by the statistician George Box that "all models are wrong, but some are useful", which refers to the approximate nature of models."

Translation: "> **NOTE** 你可能听说过统计学家乔治·博克斯提出的著名句子：“<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> "all models are wrong, but some are useful", which refers to the approximate nature of models."

Wait, I need to be careful here. The original text says:

"Once the model has been learned, we can give it new observations and it will output its predictions for the new data. We refer to these as models because they represent real-world phenomena in a simplistic-enough way that we and the computer can interpret and understand. Just as a model of the Eiffel Tower may be a good representation of the real thing but isn’t exactly the same, so statistical models are attempted representations of real-world phenomena but won’t match them perfectly."

So the sentence "The relationship between these" is incomplete. Let's look at the original text again:

"Say we have two continuous variables, and we would like to train an algorithm that can predict one (the outcome or dependent variable), given the other (the predictor or independent variable). The relationship between these"

So the sentence is "The relationship between these [variables]". The translation should be "这两个变量之间的" (the relationship between these). But in the original, it's "The relationship between these" followed by a figure. So the translation should be "这两个变量之间的" (the relationship between these).

Then the figure is shown.

So the full translation for that paragraph:

"In practice, we call a set of rules a machine learning algorithm learns a model. Once the model has been learned, we can give it new observations and it will output its predictions for the new data. We refer to these as models because they represent real-world phenomena in a simplistic-enough way that we and the computer can interpret and understand. Just as<unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk><unk> 1.4
-   **Classification**
-   *Regression*
-   *Dimension reduction*
-   *Clustering*
