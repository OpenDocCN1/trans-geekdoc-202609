the developer analyses the images of all symbols and forms a standard symbol base that is used for recognition. Also, the developer implements methods for selecting symbols and extracting their characteristic features.

However, this approach severely limits the image recognition system. This is indicated by several factors. First, if the system is learned by a certain set of symbols, then there is appearance of the image of another symbol (for example, the symbol belongs to another alphabet) and the system can not recognise it. Thus, it is necessary to further study the system.

If the system implements generalised algorithms for selecting characteristic elements, then there are images of symbols that may not have such characteristic elements. For example, the image of the symbol ‘O’ does not have such characteristic elements that are not displayed in the images of the symbols in Fig. 8.36. In this position, we need to develop additional algorithms.

Symbol recognition of a text takes a lot of time, especially if a text document has a large volume.

Using the methods to recognise a text document by words requires a complete revision of all the existing methods and the development of new methods. One of the methods that realises the recognition of text documents by words is based on the parallel shift technology.

The use of parallel shift technology for recognition of text documents is done as follows:

For each image of a symbol or word that comes to the input of the image recognition system, the standard FAIs are formed in the form of codes that are written into the memory of the standards. In this case, the image recognition system is not trained in advance. Template FAIs are formed during the formation of an image of an unknown symbol or word on the input of the recognition system.

In addition, for the formation of a template FAI, no preliminary visual analysis of the image of each symbol or word is required. That is, there is no need for a preliminary search and selection of characteristic features, which make such a method universal. In fact, use of the technology of parallel shift allows recognition of images of symbols and their combinations of any shape without preliminary analysis. In this case, the number of characters that form a word or number can be any.

The base of pattern codes can be implemented in several ways. The first method forms the base of the pattern codes of large volumes. Here each symbol and each combination of symbols is defined by its own pattern code.

The second method consists of generating the codes of pattern FAI for single-symbol images, and their combinations are represented by the identifier code. If the symbols and their combinations are defined by the