# Chapter 1: What Are Tcl and Tk?

# In This Chapter

+   - Trying out Tcl
+   - Creating a simple Tcl program
+   - Adding comments to a Tcl program
+   - Breaking up long lines in a Tcl program

When most people think of LAMP, they think of Linux, Apache, MySQL, Perl, and PHP. However, many large businesses have adopted another language for in-house development: Tcl. Tcl stands for Tool Command Language and is pronounced (don’t laugh) “tickle.” I’m not going to lie to you; Tcl is a strange language. The syntax is unusual. But once you start to understand the language, you’ll find that it’s very powerful, useful, and even object-oriented.

Along with Tcl is an interesting library for creating graphical user interfaces (GUIs) called Tk. Tk stands for Toolkit (nothing fancy, I know, but then again, neither is Tool Command Language). Although the name Tk may be boring, the library is not. Tk is a rich library that includes objects for creating windows and controls and for processing events. Tk can be used with other languages besides Tcl. Most languages have a Tk interface so you can create rich GUIs in Tk using the language of your choice.

![](bbox=[0.05, 0.645, 0.14, 0.725])

If you’re interested in using Tk with a language other than Tcl (many people use Tk with the Python language, for example), the information in this part of the book is still relevant. Although this part focuses on Tk from within Tcl, the functions are the same regardless of what language you use.

# Trying Out Tcl

The easiest way to become familiar with the strange behavior of Tcl is to try out a few examples. If you already know another language, remember that what you’re about to see is quite different from most other languages.