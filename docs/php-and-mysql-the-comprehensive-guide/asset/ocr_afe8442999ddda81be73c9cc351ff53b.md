This chapter presents three samples selected as examples. Because this book focuses on PHP, we will leave this subject at a brief overview. However, to build a bridge to the programming language and at the same time provide a practical reference, we show how the respective patterns are used in the Laminas framework.

# 12.1 Laminas

The Laminas framework is one of the now countless PHP frameworks. It has an eventful history behind it: it began with the Zend company when it still played a major role in the further development of PHP. At the end of 2019, the code base was transferred to GitHub and merged into the new Laminas project. The new framework has now found a new home under the umbrella of the Linux Foundation and is being actively developed further.

It is always important to decide whether to rely completely on a framework or whether to use only some parts, but this discussion is not the subject of this book. Instead, Laminas serves as a demonstration object for some design patterns.³

Laminas itself is installed via Composer, a package and dependency manager, which we present in more detail in Chapter 38. If you do not yet have Composer on your system, please refer to that chapter first. Pyrus from the PEAR project was still supported by Zend Framework, but is not in Laminas.

![](bbox=[0.145, 0.513, 0.855, 0.793])

Figure 12.1 The Homepage of Laminas

3 In terms of market share alone, the Symfony framework (https://symfony.com) is the market leader. However, this is not relevant for the explanations in this chapter.