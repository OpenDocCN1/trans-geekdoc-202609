# WORD EMBEDDINGS: THE FIRST GENERATION

“You shall know a word by the company it keeps!” Firth (1957:11) made this emphatic declaration to argue that *habitual collocations* capture word meaning. It is in these chronic relations that we can best understand what people “mean” by a word by how people use that word.

18 The consistent co-occurrences of words.

# THIS SECTION NEEDS:

+   - text2map
+   - text2vec
+   - stringi
+   - tidyverse
+   - textclean
+   - quanteda
+   - rtrek
+   - ggrepel

We might call the set of other words with which our focal word habitually collocates a “context.” Importantly, though, a word can pop up in many different contexts. This is called the “distributional hypothesis”: that “difference of meaning correlates with difference of distribution” (Harris 1954:156).

If we combine these two linguistic theories—(1) a word is defined by the context of its use and (2) a word can have many such contexts across which it is distributed—we have the core idea behind word embeddings.

19 Here, understood as how authors use a word.

Specifically, with a word embedding model, each word is represented as a series of numbers with a length of however many dimensions. Each dimension is an axis of meaningful variation. The meaning of a word is “distributed” across all of these axes. So, we can’t exactly interpret dimensions in isolation (cf. Tsvetkov et al. 2015).

20 Each unique word might have more than one vector depending on the type of word embedding model. We’ll return to this when we discuss token embeddings.

The output of training embeddings is a word-by-dimension *word vector matrix*. Each row is a word in the corpus vocabulary and each column is one of the dimensions. Within this matrix, two words’ vectors are “closer” in the “embedding space” if they occur in similar contexts. As we’ll see, we can use embeddings to explore “formal” relations—opposition, juxtaposition, similarity—between words in a corpus and also between documents.

# Word Embedding Basics

The cells of a term-co-occurrence matrix (TCM) include the frequency with which a “target word” occurs in the same context as a “context word.” The rows are (usually) the target words and the columns are the context words. Each cell is the (weighted) frequency with which the column word occurs “next to” the target word in a set context window. Every word is a target word distributed across contexts. Each word is also a context word defined as a distinct context.

21 This could be an asymmetric window, for example, five words *on just one side* of the target word.

Take Kennedy’s Rice speech. We’ll treat the lines as separate documents and turn the first few lines into a TCM with a window of size 5—for each target (row) word, we define a context window as the five words on either side of the target word. We’ll use `fcm()` to make our TCM.

22 quanteda calls TCMs “feature co-occurrence matrices”; thus, FCM.