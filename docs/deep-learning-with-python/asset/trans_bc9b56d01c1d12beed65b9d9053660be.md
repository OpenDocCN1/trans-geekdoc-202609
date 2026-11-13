

对于种子文本生成，我们将使用提示词“this movie”：所有生成的文本都将以此开头。

```
Listing 12.7 The text-generation callback

import numpy as np

tokens_index = dict(enumerate(text_vectorization.get_vocabulary()))

def sample_next(predictions, temperature=1.0):
    predictions = np.asarray(predictions).astype("float64")
    predictions = np.log(predictions) / temperature
    exp_preds = np.exp(predictions)
    predictions = exp_preds / np.sum(exp_preds)
    probas = np.random.multinomial(1, predictions, 1)
    return np.argmax(probas)

class TextGenerator(keras.callbacks.Callback):
    def __init__(self,
                 prompt,
                 generate_length,
                 model_input_length,
                 temperatures=(1.,),
                 print_freq=1):
        self.prompt = prompt
        self.generate_length = generate_length
        self.model_input_length = model_input_length
        self.temperatures = temperatures
        self.print_freq = print_freq

    def on_epoch_end(self, epoch, logs=None):
        if (epoch + 1) % self.print_freq != 0:
            return
        for temperature in self.temperatures:
            print("== Generating with temperature", temperature)
            sentence = self.prompt
            for i in range(self.generate_length):
                tokenized_sentence = text_vectorization([sentence])
                predictions = self.model(tokenized_sentence)
                next_token = sample_next(predictions[0, i, :])
                sampled_token = tokens_index[next_token]
                sentence += " " + sampled_token
                print(sentence)

prompt = "This movie"
text_gen_callback = TextGenerator(
    prompt,
    generate_length=50,
    model_input_length=sequence_length,
    temperatures=(0.2, 0.5, 0.7, 1., 1.5))
```

让我们对这个模型调用fit()。

```
Listing 12.8 Fitting the language model

model.fit(lm_dataset, epochs=200, callbacks=[text_gen_callback])
```

以下是训练200个时代后我们能够生成的一些精选示例。请注意，标点符号不在我们的词汇表中，因此生成的文本都没有任何标点符号：

- With temperature=0.2
- “this movie is a [UNK] of the original movie and the first half hour of the movie is pretty good but it is a very good movie it is a good movie for the time period”
- “this movie is a [UNK] of the movie it is a movie that is so bad that it is a [UNK] movie it is a movie that is so bad that it makes you laugh and cry at the same time it is not a movie i dont think ive ever seen”

- With temperature=0.5
- “this movie is a [UNK] of the best genre movies of all time and it is not a good movie it is the only good thing about this movie i have seen it for the first time and i still remember it being a [UNK] movie i saw a lot of years”
- “this movie is a waste of time and money i have to say that this movie was a complete waste of time i was surprised to see that the movie was made up of a good movie and the movie was not very good but it was a waste of time and”

- With temperature=0.7
- “this movie is fun to watch and it is really funny to watch all the characters are extremely hilarious also the cat is a bit like a [UNK] [UNK] and a hat [UNK] the rules of the movie can be told in another scene saves it from being in the back of”
- “this movie is about [UNK] and a couple of young people up on a small boat in the middle of nowhere one might find themselves being exposed to a [UNK] dentist they are killed by [UNK] i was a huge fan of the book and i havent seen the original so it”

- With temperature=1.0
- “this movie was entertaining i felt the plot line was loud and touching but on a whole watch a stark contrast to the artistic of the original we watched the original version of england however whereas arc was a bit of a little too ordinary the [UNK] were the present parent [UNK]”
- “this movie was a masterpiece away from the storyline but this movie was simply exciting and frustrating it really entertains friends like this the actors in this movie try to go straight from the sub thats image and they make it a really good tv show”

- With temperature=1.5
- “this movie was possibly the worst film about that 80 women its as weird insightful actors like barker movies but in great buddies yes no decorated shield even [UNK] land dinosaur ralph ian was must make a play happened falls after miscast [UNK] bach not really not wrestlemania seriously sam didnt exist”

> - "this movie could be so unbelievably lucas himself bringing our country wildly funny things has is for the garish serious and strong performances colin writing more detailed dominated but before and that images gears burning the plate patriotism we you expected dyan bosses devotion to must do your own duty and another"

由此可见，较低的温度值会产生非常枯燥重复的文本，有时甚至会导致生成过程陷入循环。温度较高时，生成的文本会变得更有趣、更惊喜，甚至更具创造性。温度过高时，局部结构开始瓦解，输出看起来大多是随机的。在这里，合适的生成温度似乎约为0.7。始终尝试多种采样策略！学习到的结构与随机性之间的巧妙平衡，正是生成变得有趣的关键。

请注意，通过训练更大的模型、更长的时间、更多的数据，你可以生成远比这更连贯、更真实的样本——GPT-3这类模型的输出正是语言模型能够实现的良好示例（GPT-3本质上与我们在这个示例中训练的东西相同，只是拥有深度的Transformer解码器堆栈和更大的训练语料库）。但不要指望能生成任何有意义的文本，除非靠纯粹的随机机会和你自身解读的魔力：你所做的不过是从一个统计模型中采样数据，该模型描述哪些词会跟在哪些词之后。语言模型只有形式，没有实质。

自然语言是多种事物：一种沟通渠道，一种作用于世界的方式，一种社交润滑剂，一种构思、存储和检索你自己想法的方式……语言的这些用途正是其意义的来源。尽管名为“语言模型”，深度学习“语言模型”实际上并未捕捉语言的这些基本方面。它无法沟通（它没有沟通的主题，也没有沟通的对象），它无法作用于世界（它没有主体性和意图），它无法进行社交，也没有任何借助文字来处理的想法。语言是心智的操作系统，因此，要使语言有意义，它需要一个心智来驱动它。

语言模型所做的是捕捉我们在用语言生活时所生成的可观察产物（书籍、在线电影评论、推文）的统计结构。这些产物恰好具有统计结构，这只是人类实现语言方式的副产物。来做个思想实验：如果我们的语言在压缩通信方面做得更好，就像计算机处理大多数数字通信一样，会怎样呢？语言不会变得不那么有意义，仍然可以实现其众多目的，但它将缺乏任何内在的统计结构，因此就无法像你刚才那样对其进行建模了。

## 12.1.6 总结

- 你可以通过训练模型，基于之前的 token 来预测下一个 token(s)，从而生成离散序列数据。
- 在文本的情况下，这样的模型称为语言模型。它可以基于单词或字符。
- 采样下一个 token 需要在遵循模型判断可能的内容和引入随机性之间取得平衡。
- 处理此问题的一种方法是 softmax 温度的概念。始终尝试不同的温度以找到合适的那个。

## 12.2 DeepDream

DeepDream是一种艺术图像修改技术，它使用卷积神经网络学习到的表征。它最初由谷歌于2015年夏季发布，实现使用的是Caffe深度学习库（这比TensorFlow的首个公开版本早几个月）。³ 由于它能够生成迷幻的图片（参见，例如，图12.4），它迅速成为网络热门，这些图片充满了算法错觉产物、鸟羽和狗眼——这是DeepDream卷积网络在ImageNet上训练的副产物，ImageNet中狗品种和鸟类物种被大量过度代表。

![](img/ab452ecf572a1f1372915be13bd8088f_400_0.png)

图 12.4 DeepDream 输出图像示例

³ Alexander Mordvintsev, Christopher Olah, 和 Mike Tyka，“DeepDream：可视化神经网络的代码示例，”Google研究博客，2015年7月1日，http://mng.bz/xXIM。

