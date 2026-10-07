We're looking at the actual output. Above image is another example from Andrej Karpathy's blog. Here, it's not just showing us if it is active or not, but we can see the guessed letters.

There are six rows.

+   - At the top row, it's showing if it's active or not. Green means active and Blue means not active.
- In the other five lines it is saying what the neural network is predicting, what letter is going to appear in next. Notice the 2nd row shows some letters matched diagonally-left (next in 1st row) to some of them. More deep-red means more possibility. Dark-red means very likely prediction and light red means unlikely prediction.
- We can also see the NN detecting the non-active blue text. For example: "English-language".

![](bbox=[0.099, 0.219, 0.9, 0.287])

+   - We can clearly see that this neural network is looking for URLs. That's why all are green. Following image shows how the NN is guessing the answer letters.

![](bbox=[0.266, 0.347, 0.733, 0.415])

![](bbox=[0.297, 0.447, 0.702, 0.513])

+   - Most-probable-predictions (deep-red) also gets wrong. Eg: ".com" for ".co.il".
- Most of it can predict "www" successfully.

# 12.2.8 Additional Readings

+   - For more, check his blog, karpathy.github.io. There's a couple more examples that and of the previous examples that we looked at.
- Actually it is important to know what's going inside the neural network. RNN, CNN, ANN, those are so advanced (and complex) that we need to analyze what's going on inside those architectures (we need to study them and treat them as an allen-being test!).

# Additional Reading:

The Unreasonable Effectiveness of Recurrent Neural Networks

![](bbox=[0.469, 0.753, 0.879, 0.893])

By Andrej Karpathy (2015)

Link:

http://karpathy.github.io/2015/05/21/rnn-effectiveness/