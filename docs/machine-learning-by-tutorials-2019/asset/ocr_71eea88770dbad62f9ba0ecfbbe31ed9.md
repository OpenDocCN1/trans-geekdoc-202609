items that came before it in the sequence. It's its serial nature of RNNs that makes them slower than other neural networks, such as CNNs. This is true of both training and inference.

These recurrent connections allow RNN layers to adjust their output based on what they've seen so far in the sequence, much like you interpret the word "fish" in the following two sentences depending on the words before it: "I like to fish. I like fish." In the first sentence, the speaker likes to catch fish, or at least try to; in the second, the speaker probably likes to eat fish, but may also enjoy fish as an animal. Either way, the definition of "fish" depends on context.

> Note: The previous diagram showed two outputs from each layer, one going to the next layer and one going off to...somewhere? That's to indicate how the output for each timestep can be used within an RNN layer, through the recurrent connection, as well as passed to the next, possibly recurrent, layer of the network. The final output of an RNN layer can be the output for the sequence's last timestep, or the entire sequence of outputs the layer generated while processing the input sequence.

Early implementations of this basic RNN design showed was possible to learn relationships between timesteps in a sequence, but they don't actually do it well. Due to how the underlying math works, they take too long to train and can't relate items separated by many timesteps. For example, imagine an RNN processing our example sentence — it would likely remember the fox is brown, but it might have forgotten that there is a cat by the time it gets to the dog at the end of the sentence.

In reality a basic RNN could properly handle sentences like that, but relationships span much greater distances in many sequences. To continue with our reading example, while words within a sentence are surely related to each other, they can also be related to words in sentences earlier in the same paragraph, many pages in the same chapter or several chapters in a book. The distance between relationships can be arbitrarily long, and basic RNNs simply aren't suited to handle that.

But then came LSTMs.

# Long short-term memory

The acronym LSTM stands for the odd-sounding phrase long short-term memory, and it refers to a different kind of recurrent unit capable of dealing with