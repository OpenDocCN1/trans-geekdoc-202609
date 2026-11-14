But if you assume both _p_(_app_) and _p_(_other_) are 50 percent, then when comparing the two values using the MAP decision rule, you might as well just drop them. Thus, you can classify a tweet as app-related if:

```
p(word₁|app) p(word₂|app) ...>= p(word₁|other) p(word₂|other) ...
```

Pause a moment and contemplate this point. To build a naïve Bayes classification model, you need only track frequencies of historic app-related and non-app-related words. Well, that’s not hard!

# A Couple More Odds and Ends

Now, before you get started in Excel, you have to address these two practical hurdles in implementing naïve Bayes in Excel or in any programming language:

+   - Rare words
+   - Floating-point underflow

# Dealing with Rare Words

The first is the problem of _rare words_. What if you get a tweet that you’re supposed to classify but there’s the word _Tubal-cain_ in it? Based on past data in the training set, perhaps one or both classes have never seen this word. A place where this happens a lot on Twitter is with shortened URLs, since each new tweet of a URL might have a different, never-seen-before encoding.

You can assume this:

```
p("Tubal-cain"|app) = 0
```

But then you’d get the following:

```
p("Tubal-cain"|app) p(word₂|other) p(word₃|other)... = 0
```

Tubal-cain effectively “zeros out” the entire probability calculation.

Instead, assume that you’ve seen “Tubal-cain” once before. You can do this for all rare words.

But wait—that’s unfair to the words you _actually_ have seen once. So add 1 to them, too.

But that’s unfair to the words you’ve _actually seen_ twice. So, add 1 to every count.

This is called _additive smoothing_, and it’s often used to accommodate unseen words in bag-of-words models.