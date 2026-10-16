simplest thing the team could ship (usually a "Hello world" website) and then iterate on small bits of functionality in manageable chunks, just like how we did here.

The skill is knowing how to split work up, and that comes with practice and with some lovely TDD to help you on your way.

# Property based tests

+   - Built into the standard library
+   - If you can think of ways to describe your domain rules in code, they are an excellent tool for giving you more confidence
+   - Force you to think about your domain deeply
+   - Potentially a nice complement to your test suite

# Postscript

This book is reliant on valuable feedback from the community. Dave is an enormous help in practically every chapter. But he had a real rant about my use of 'Arabic numerals' in this chapter so, in the interests of full disclosure, here's what he said.

> Just going to write up why a value of type int isn't really an 'arabic numeral'. This might be me being way too precise so I'll completely understand if you tell me to f off.
> 
> A digit is a character used in the representation of numbers - from the Latin for 'finger', as we usually have ten of them. In the Arabic (also called Hindu-Arabic) number system there are ten of them. These Arabic digits are:
> 
> 0 1 2 3 4 5 6 7 8 9
> 
> A numeral is the representation of a number using a collection of digits. An Arabic numeral is a number represented by Arabic digits in a base 10 positional number system. We say 'positional'