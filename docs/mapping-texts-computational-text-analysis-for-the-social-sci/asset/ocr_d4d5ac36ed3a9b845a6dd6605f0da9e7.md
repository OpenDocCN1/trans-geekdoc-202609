# # 10 Core Inductive

INDUCTIVE approaches find patterns in text, just like deductive approaches. However, we now allow the patterns to show themselves. Imagine creating a map for a community. If we assume they require a road map, we'd proceed deductively, from a set of “road-like” features (highways, interstates, streets) to our representation of those features. If instead, we track where people tend to wander using wearable GPS devices and then create a representation of paths that emerge, we’ve engaged in inductive reasoning. In inductive research, generally, we identify patterns as they emerge from our research.

This chapter reviews some core inductive approaches in computational text analysis. We start with finding **document similarities**. We then move to **clustering documents** and then discuss a popular family of inductive approaches called **topic modeling**.

+   THIS SECTION NEEDS:
+   * tidyverse
+   * text2map
+   * text2vec

# ## DOCUMENT SIMILARITY

Quantifying _similarities_ is foundational to computational text analysis— especially finding _document similarities_. In fact, many text analysis applications that we encounter when writing and teaching revolve around document similarities—for instance, plagiarism detection software (Bail 2012). While we can use similarity metrics deductively—if, say, we have a hypothesis about which authors write more similarly—we can also use them inductively, allowing patterns of similarity to emerge from a corpus.

# ### One-Mode Projections

DTMs are bimodal matrices: the documents are in the rows, the words are in the columns, and each cell indicates the extent to which a word is present in a document. Thinking of DTMs like this opens a world of analytical possibilities from network science.

Recall the _one-mode projection_, which turns a two-mode matrix into one-mode matrices.<sup>1</sup> We’ll focus on the document-level projection here.

<sup>1</sup> See Math Basics and Text to Numbers.