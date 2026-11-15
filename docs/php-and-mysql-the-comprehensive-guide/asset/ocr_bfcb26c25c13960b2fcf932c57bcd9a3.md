bookshops, contains a lot of material on the subject and is a hot tip for a deeper introduction to the subject. Unfortunately, due to numerous internal changes in PHP since its publication, many details are no longer up to date.

The example in this chapter was created at the end of our work on this book. We put a lot of effort into the project and, toward the end, we wondered whether this process could be optimized. We quickly came up with the idea of a book generator. You enter a topic, and the complete book comes out.

# 39.1 Programming

One principle was recognizable in many places in this book: achieve as much as possible with as little work (i.e., PHP code) as possible. We want to keep it that way in this chapter too. If you know exactly what your extension is called and which functions it should offer, you can have the complete code created (almost) automatically. To do this, there is a script called ext_skel.php in the PHP source code in the ext directory,1 which automatically creates a basic framework (skeleton) of the associated C code.

The following call must be made directly within the ext folder of the PHP source code and generates a series of data for the extension (see Figure 39.1):

```
php ext_skel.php --ext book
```

![](bbox=[0.145, 0.53, 0.857, 0.82])

Figure 39.1 "ext_skel.php" in Action

1 On GitHub: http://s-prs.co/v602297.