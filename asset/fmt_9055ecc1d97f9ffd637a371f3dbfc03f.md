
现在每一行的总和为 1.0。
我们的流程并不精确地模仿 sklearn 通过 `TfidfVectorizer` 执行的步骤；我们不会试图去调和我们的手动步骤与 sklearn 方法之间的差异；只需记住，至少我们使用了不同的停用词，这会影响 IDF 权重计算中使用的权重。

在 [13] 中：

```python
sparse = (sk_txt.TfidfVectorizer(norm='l1', stop_words='english')
    .fit_transform(docs))

sparse.todense()
```

Out[13]:

```python
matrix([[0.3896, 0.   , 0.6104, 0.   , 0.   , 0.   , 0.   , 0.   ],
        [0.   , 0.2419, 0.   , 0.379 , 0.   , 0.   , 0.379 , 0.   ],
        [0.1948, 0.1948, 0.   , 0.   , 0.3052, 0.3052, 0.   , 0.   ],
        [0.3593, 0.3593, 0.   , 0.   , 0.   , 0.   , 0.   , 0.2814]])
```

### 14.1.2 文本学习示例

为了将这些想法付诸实践，我们需要一批带有预分类标签的合理文档。幸运的是，sklearn 为我们提供了获取这些文档的工具。这些数据并不随你的 sklearn 发行版安装；相反，你需要导入并调用一个工具来下载它。下面的导入操作会完成必要的步骤。

在 [14] 中：

```python
from sklearn.datasets import fetch_20newsgroups

twenty_train = fetch_20newsgroups(subset='train')
```

二十个新闻组数据集（Twenty Newsgroups）包含来自 20 个老式互联网新闻组的约 20,000 份文档。新闻组是一种在线论坛，有点类似于可由多人同时参与的电子邮件线程。针对许多不同的讨论主题都有对应的新闻组：宗教和政治总是特别热烈，但也有很多关于各种运动、爱好及其他兴趣的小组。该分类问题是取任意一篇文档，判断它来自哪个讨论组。

在 [15] 中：

```python
print("the groups:")

print(textwrap.fill(str(twenty_train.target_names)))
```

the groups:
['alt.atheism', 'comp.graphics', 'comp.os.ms-windows.misc',
'comp.sys.ibm.pc.hardware', 'comp.sys.mac.hardware', 'comp.windows.x',
'misc.forsale', 'rec.autos', 'rec.motorcycles', 'rec.sport.baseball',
'rec.sport.hockey', 'sci.crypt', 'sci.electronics', 'sci.med',
'sci.space', 'soc.religion.christian', 'talk.politics.guns',
'talk.politics.mideast', 'talk.politics.misc', 'talk.religion.misc']

示例的实际内容是文本邮件，包括带有发件人、收件人和主题的头部部分。以下是第一个示例的前十行：

In [16]:

```python
print("\n".join(twenty_train.data[0].splitlines()[:10]))
```

```

From: lerxst@wam.umd.edu (where's my thing)

Subject: WHAT car is this!?

Nntp-Posting-Host: rac3.wam.umd.edu

Organization: University of Maryland, College Park

Lines: 15

I was wondering if anyone out there could enlighten me on this car I saw the other day. It was a 2-door sports car, looked to be from the late 60s/early 70s. It was called a Bricklin. The doors were really small. In addition, the front bumper was separate from the rest of the body. This is

```

一旦数据可用，我们几乎可以立即应用 TF-IDF 转换器来获得文档的有用表示。

In [17]:

```python
ct_vect  = sk_txt.CountVectorizer()

tfidf_xform = sk_txt.TfidfTransformer()

docs_as_counts = ct_vect.fit_transform(twenty_train.data)

docs_as_tfidf  = tfidf_xform.fit_transform(docs_as_counts)
```

我们可以将该数据连接到任何学习模型。这里我们使用朴素贝叶斯的一种变体：

In [18]:

```python
model = naive_bayes.MultinomialNB().fit(docs_as_tfidf,
    twenty_train.target)
```

现在，你可能会问我们是否可以将所有这些步骤包装到一个管道中。当然可以！

In [19]:

```python
doc_pipeline = pipeline.make_pipeline(sk_txt.CountVectorizer(),
    sk_txt.TfidfTransformer(),
    naive_bayes.MultinomialNB())
```

在我们开始评估之前，让我们减少我们考虑的类别数量：

```python
categories = ['misc.forsale',
    'comp.graphics',
    'sci.med',
    'sci.space']
```

我们甚至可以做得更好。`TfidfVectorizer` 将两个预处理、特征提取步骤合并到一个组件中。因此，这里是解决此问题的超级紧凑方法：

```python
twenty_train = fetch_20newsgroups(subset='train',
    categories=categories,
    shuffle=True,
    random_state=42)

doc_pipeline = pipeline.make_pipeline(sk_txt.TfidfVectorizer(),
    naive_bayes.MultinomialNB())

model = doc_pipeline.fit(twenty_train.data, twenty_train.target)
```

我们可以快速评估模型的性能：

```python
twenty_test = fetch_20newsgroups(subset='test',
    categories=categories,
    shuffle=True,
    random_state=42)

doc_preds = model.predict(twenty_test.data)

cm = metrics.confusion_matrix(twenty_test.target, doc_preds)

ax = sns.heatmap(cm, annot=True,
    xticklabels=twenty_test.target_names,
    yticklabels=twenty_test.target_names,
    fmt='3d') # cells are counts

ax.set_xlabel('Predicted')

ax.set_ylabel('Actual');
```

你会很快注意到 k-means 将两个混合物种错误地分开了——实际上它们是更垂直地分割的，但 k-means 将它们水平分割了。在没有目标值——实际物种——来区分两者的情况下，算法没有任何指导来区分纠缠的物种。更重要的是，在聚类中，没有“正确”的定义。标准仅仅由算法的工作方式定义。

尽管 sklearn 目前不提供它们作为现成的技术，但 k-means 和其他聚类技术可以像我们在第 13.2 节中讨论的方法那样进行核化。在下一节中，我们将使用聚类来查找并定义视觉词的同义词，以在不同的局部词汇之间构建全局词汇。我们将把含义大致相同的不同局部词组合成单个、代表性的全局词。

## 14.3 处理图像

有很多很多方法可以处理图像，使学习者能够对它们进行分类。我们已经谈到过对非表格数据使用核。聪明的人们创造了许多从原始图像像素中提取特征的方法。更高级的学习技术——比如深度神经网络——可以从图像中构建非常复杂、有用的特征。关于这些主题，有整本书可供阅读；我们不可能涵盖所有这些内容。相反，我们将专注于一种技术，它非常好地建立在本书前两个主题之上：词袋和聚类。通过协同使用这两种技术，我们将能够构建一个强大的特征提取器，将我们的图像从像素网格转换为可用且有用的学习特征表。

### 14.3.1 视觉词袋

我们有一个总体策略想要实现。我们想要——以某种方式——模仿我们在文本分类中使用的词袋方法，但用于图像。由于我们没有字面上的词，我们需要想出一些。幸运的是，有一种非常优雅的方法可以做到这一点。我会给你一个故事化的过程视图，然后我们再深入细节。

想象你正在参加一个派对。派对在艺术博物馆举办，但参加者来自各行各业、世界各地。艺术博物馆非常大：你没有希望查看每一幅画。但，你在周围闲逛了一会儿，开始形成一些关于你喜欢什么和不喜欢什么的想法。过了一会儿，你感到疲倦，前往咖啡馆喝点东西。当你啜饮清爽的饮料时，你注意到周围还有其他人，也累了，坐在你旁边。你想知道他们是否可能对你应该查看的其他画作有一些好的推荐。

获取推荐有几个难度等级。所有与会者对艺术都有自己的喜好和厌恶；描述这些偏好有许多不同、简单和复杂的方式；而且许多与会者说不同的语言。现在，你可以到处闲逛，从那些说你语言并以对你有意义的方式描述他们偏好的人那里获得一些推荐。但想象一下你错过了多少其他信息！如果有一种方法可以将所有这些个人词汇翻译成所有与会者都可以用来描述画作的群体词汇，那么我们就可以让每个人看到他们可能喜欢的画作。

我们解决这个问题的方法是结合所有个人词汇并将它们分组为同义词。然后，个人用来描述画作的每个术语都可以翻译成全局同义词。例如，所有与红色相似的术语——猩红、红宝石、栗色——都可以翻译成单一术语红色。一旦我们这样做，就不再有数十种不兼容的词汇，我们有一个单一的群体词汇，可以以共同的方式描述画作。我们将使用这个群体词汇作为我们词袋的基础。然后，我们可以遵循类似于文本分类的过程来构建我们的学习模型。

### 14.3.2 我们的图像数据

我们需要一些数据来工作。我们将使用 Caltech101 数据集。如果你想在家中跟进，从 www.vision.caltech.edu/Image_Datasets/Caltech101/101_ObjectCategories.tar.gz 下载并解压缩数据。

数据集中共有 101 个类别。类别代表世界上的物体，例如猫和飞机。你会看到下面有 102 个类别，因为有两组人脸，一组难一组易。

In [24]:

```python
# exploring the data

objcat_path = "./data/101_ObjectCategories"

cat_paths = glob.glob(osp.join(objcat_path, "**"))

all_categories = [d.split('/')[-1] for d in cat_paths]

print("number of categories:", len(all_categories))

print("first 10 categories:\n", textwrap.fill(str(all_categories[:10])))
```

```

number of categories: 102

first 10 categories:

['accordion', 'airplanes', 'anchor', 'ant', 'BACKGROUND_Google',

'barrel', 'bass', 'beaver', 'binocular', 'bonsai']

```

数据本身就是字面上的图形文件。这里有一个手风琴：

In [25]:

```python
from skimage.io import imread

test_path = osp.join(objcat_path, 'accordion', 'image_0001.jpg')

test_img = imread(test_path)

fig, ax = plt.subplots(1,1,figsize=(2,2))

ax.imshow(test_img)

ax.axis('off');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_511_0.png)

很可能是一个合理的猜测，如果没有一些预处理——特征提取——我们几乎没有希望正确地对这些图像进行分类。

### 14.3.3 端到端系统

对于我们的学习问题，我们有一篮子图像和它们所属的类别。我们构建端到端学习系统的策略如图 14.1 和 14.2 所示。以下是主要步骤：

- 用其自己的局部视觉词描述每个图像。
- 将这些局部词分组为各自的同义词。同义词将形成我们的全局视觉词汇。
- 将每个局部视觉词翻译成全局视觉词。
- 用全局词的计数替换全局视觉词的列表。这给我们一个 BoGVW——bag of (global visual) words (或简单地 BoVW, for bag of visual words)。
- 学习 BoGVW 与目标类别之间的关系。

当我们想要预测新的测试图像时，我们将：

- 将测试图像转换为其自己的局部词。
- 将局部词翻译成全局词。
- 为测试图像创建 BoGVW。
- 用 BoGVW 进行预测。

对于新测试图像的预测过程依赖于训练好的学习系统中的两个组件：我们在步骤 2 中构建的翻译器和我们在步骤 5 中构建的学习模型。

![](img/d94e4cd766940d79abed0bc6ba4e4344_512_0.png)

图14.1 我们图像标注系统的概要。

![](img/d94e4cd766940d79abed0bc6ba4e4344_512_1.png)

图14.2 我们图像标注系统中各步骤的图形化视图。

#### 14.3.3.1 提取局部视觉单词

将图像转换为其局部单词形式是我们不会打开的一个黑盒。我们将直接使用OpenCV（一个图像处理库）中的例程，称为`SIFT_create`，它可以提取图像中有趣的部分。这里，“有趣”指的是图像中边缘的方向和形状的角点等内容。每张图像都会被转换为一个局部单词表。每张图像的表具有相同数量的列，但行数不同。有些图像具有更显著的特征，需要用更多的行来描述。图形化表示如图14.3所示。

![](img/d94e4cd766940d79abed0bc6ba4e4344_513_0.png)

图14.3 从图像中提取局部视觉单词。

我们将使用几个辅助函数来定位硬盘上的图像文件，并从每张图像中提取局部单词。

In [26]:

```python
def img_to_local_words(img):

    ' heavy lifting of creating local visual words from image '

    sift = cv2.xfeatures2d.SIFT_create()

    key_points, descriptors = sift.detectAndCompute(img, None)

    return descriptors

def id_to_path(img_id):

    ' helper to get file location '

    cat, num = img_id

    return osp.join(objcat_path, cat, "image_{:04d}.jpg".format(num))
```

```python
def add_local_words_for_img(local_ftrs, img_id):

    ' update local_ftrs inplace '

    cat, _ = img_id

    img_path = id_to_path(img_id)

    img = imread(img_path)

    local_ftrs.setdefault(cat, []).append(img_to_local_words(img))
```

由于处理图像可能花费大量时间，为了讨论方便，我们将只限制在几个类别上。我们还会对愿意创建的全局词汇表单词数量设置一个限制。

In [27]:

```python
# set up a few constants

use_cats = ['accordion', 'airplanes', 'anchor']

use_imgs = range(1,11)

img_ids = list(it.product(use_cats, use_imgs))

num_imgs = len(img_ids)

global_vocab_size = 20
```
