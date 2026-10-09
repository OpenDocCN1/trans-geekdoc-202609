# Chapter

2

Static Code Analysis Tooling

# What Is It?

I like to introduce programming ideas by sharing a definition from a reliable source. In this case, Wikipedia:

> Static program analysis is the analysis of computer software that is performed without actually executing programs, in contrast with dynamic analysis, which is analysis performed on programs while they are executing. In most cases the analysis is performed on some version of the source code, and in the other cases, some form of the object code.

The part of this that intrigued me when I first started looking into it was the “without actually executing programs” part. About a decade ago, I tried creating my own tool that would perform static analysis of PHP code to figure out dependencies and language constructs you needed to test. It quickly led me down a rabbit hole of figuring out how to parse PHP tokens and abstract syntax trees.