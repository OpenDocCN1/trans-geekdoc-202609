# # 24 Optimization

> > "Preoptimization is the root of all evils"
> Donald Knuth, The Art of Computer Programming

In some situations after writing a PHP-based web site application, developers may find that the site or application is not fast enough to meet their performance requirements. So they'll have to optimize their code to reduce the execution time of the scripts. While PHP is generally a fast scripting language, there are some techniques, tips, and tricks that can be used to optimize the code.

In this chapter we'll cover:

+   - Techniques that help optimize code
+   - Advanced database concepts that can further improve the performance of PHP programs

# ## The Right Language

The first question a developer facing a performance issue should check is if they're using the right programming language. Perhaps the language interpreter causes most of the slow down, so there's little point in optimizing the code; it'll never be enough.

Several programming languages were benchmarked to check how fast they were compared to PHP. The benchmarks involved a lot of different types of scripts using different operations; the results are an average of all the tests.