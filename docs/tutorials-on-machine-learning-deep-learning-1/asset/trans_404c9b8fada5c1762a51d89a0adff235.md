

# 注意：

非常重要的一点是，这些内容中没有任何一个是实际上被编码进神经网络的。它在自主运行。
所有这一切都是由网络自己学习的。

通过数千次迭代和轮次（Epochs），使用许多隐藏状态（或实际的记忆单元），它根据重要性分配这些状态来跟踪事物……它分配不同的隐藏状态来跟踪不同的事物/主题。

所以它真的在自我进化，决定什么是重要的，什么是不重要的。

## 示例 3：在某些文本上训练的 RNN 示例。对于人类来说是无法识别的。它来自某个程序的源代码。

```python
fields = string representation from user space
tags = unpack title string buf, _, rem, size = len
str = ""
width back = "main"
return r(ptr, [main])
nof the currently completed string fields, PATH max
get the long-length depth
```

- 该单元格正在执行某些操作，但无法识别正在发生什么。
这与上一章的 CNN 示例非常，在应用滤波器或特征检测器后，我们寻找的是检测到的特征；在池化层（Pooled-layer）和扁平层（Flattened-Layer），CNN 可以识别它，但人类不能。
保存正在发生着，当处理后的特征到达最后一层时，它们对人眼来说是完全无法识别的。但它们对大多数人是有意义的。你们中 95% 的人真的知道发生了什么。
但在 5% 的情况下，我们看到了过的示例 1 和示例 2。

## 示例 4：我们现在将通过逐点运算（pointwise-operation）分析我们 LSTM-RNN 中的输入 h1，跳过输出值（output-value）或输出门（output-gate），现在我们将回溯在输出 h1 中产生的内容——

| | | y n e t | n | | English | language | cell | of | f | s | a |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|-|
| d | w e n s | a l a b a c h | | s | n | t | i c a g e | b u f e r d e h o a n b f i r | | |
| w - 2 | p o s s i b l e | s s i e n | g h / m | T v o r z i | c d e e n e a s s i e l e e h e d | l r i t r a o n |
| r - d | a b p n t w | t r o l c i e n s | p i l l a v d | u l t h a a o | t t u i f |
| s p t c o o a 2 | r i o l c i e n r s | p i l l a v d | e x t | e d n m | o b u v b s | m b l |
| g e s t n e w s a p o r | | | Y e d o t h | A h r o n t h | | | | H a b r a | l a n g u u |
| a a w s o r | | | | f e a n e m t i | | | | | | | |
| i l s c o r e t a n h | T h o a t i n g e r m u w | y s | | | # T A e g | o u e n d |
| u e v l r t d | B a t M a s u t | A s s o g s | | | S M b o l u s T u e n d |
| a d i l l i t i c p | | l S V h w t s | D u n e g g o | | | C o u l l o C e b y s s | |
| c a l l c c a : | | | G o b a s | | | h t t | | | w i o b l e s | |
| s t l l | | | h e o v e l t | | d e w a i e l | r t o a e e | T & a i |
| n k l | | | A n & s | | | o w | i s a s e n e n | m c c f t t | |
| | | | | | | b a c m r t o p g r o b l i e r n a f i d l o p |
| i l y | | | H e r r e t | P e r r t e a a n t h | | | | w o n b o m d s t n / s |
| k c o o s a n t | h a i l n n t e h a s c r o n | s a a d | x n e | w a a m r a d h i e r | | | |
| d e t t t | T c m m g g g | W o n | | | b a e r f | d u t c h n a r n e s | | |
| n s a l | | | D u n e r u i l a a l | | | | e n a p i l a n f i r n a l i n a l |

我们正在查看实际输出。上方是 Andrej Karpathy 博客上的另一个示例。在这里，它只是显示它是否激活，但我们可以看到预测的字母。

- 有六行。
- 在顶部行，它显示是否激活。绿色表示激活，蓝色表示未激活。
- 在其他五行，它在预测下一个将出现的字母。注意第二行显示了与第一行匹配的某些字母。红色表示可能性更多，深红色表示可能性很大，浅红色表示不太可能。
- 我们还可以看到检测到的“English-language”。

(注：由于原文中存在大量重复的描述性，译文已按要求整合核心含义并避免了冗余重复输出)
