# Introduction

packages. It also shows to document, unit test, and benchmark custom packages. The chapter's last sections provide brief reviews of the tools provided with the gc compiler, and Go's standard library.

Although Go is quite a small language, it is a very rich and expressive language (as measured in syntactic constructs, concepts, and idioms), so there is a surprising amount to learn. This book shows in idiomatic Go style right from the start.* This approach, of course, means that some things are shown fully explained. We ask the reader to trust that it will be explained over the course of the book (and, of course, cross-references are provided for everything that is not explained on the spot).

Go is a fascinating language, and one that is really nice to use. It's not hard to learn Go's syntax and idioms, but it does introduce some new concepts that may be unfamiliar to many readers. This book tries to give the readers the conceptual breakthroughs—especially in object-oriented Go and in concurrent Go programming—that might take weeks or months for those whose guide is the good but rather terse documentation.

# Acknowledgments

Every technical book I have ever written has benefited from the help and advice of others, and this one is no different in this regard.

I want to give particular thanks to two friends who are programmers with no prior Go experience: Jasmin Blanchette and Trenton Schulz. Both have contributed to my books for many years, and in this case their feedback helped to ensure that this book will meet the needs of other programmers new to Go.

The book was also greatly enhanced by the feedback I received from core developer Nigel Tao. I didn't always take his advice, but his feedback was always illuminating and resulted in great improvements both to the code and to the text.

I had additional help from others, including David Boddie, a programmer new to Go, who gave some valuable feedback. And Go developers Ian Taylor, and especially Russ Cox, between them solved many problems both of code and concepts, and provided clear and precise explanations that contributed greatly to the book's accuracy.

During the writing of the book I asked many questions on the golang-nuts mailing list and always received thoughtful and useful replies from many different

> * The exception is that in the early chapters we always declare channels to be bidirectional, even when they are used only unidirectionally. Channels are declared to have a particular direction wherever this makes sense, starting from Chapter 7.