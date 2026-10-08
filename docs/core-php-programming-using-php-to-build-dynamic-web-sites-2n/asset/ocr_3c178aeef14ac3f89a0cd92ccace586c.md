# Chapter 19. GENERATING GRAPHICS

Dynamic Buttons

Generating Graphs on the Fly

Bar Graphs

Pie Charts

Stretching Single-Pixel Images

This chapter explores generating graphics using the GD extension functions described in Chapter 12. "Image Functions." It is important to be aware of the issues involved in terms of the creation of graphics on the fly. The first is that it is relatively costly in terms of CPU time. In most cases the flexibility of dynamic graphics is not worth what you pay in the load imposed on the server. Another issue is that making nice-looking graphics from PHP functions is not easy. Common techniques like drop shadows are next to impossible. As you will see in the examples that follow, a lot of work goes into creating simple, flat charts. While there is adequate support for text, you'd expect a word processor to not exist. Text does wrap at line ends. There is no concept of learning, spacing, or descenders. Regardless, generating graphics makes sense in some situations. This chapter contains some real examples that you can start with very little modification.

In the first edition of this text, the examples in this chapter created GIF images. Since the GD library has dropped support for GIFs as a key component of the GIF standard relies on a patented process for compressing data. Instead, the GD library produces PNG and JPEG images. Turn back to Chapter 12 for more information on this issue.

# Dynamic Buttons

Images wrapped in anchor tags are a common navigational device. Instead of plain text, this method allows you to create buttons similar to those created in the operating system, or ever fanciful icons. In most cases it is best to leave these as created in your favorite graphics editor, because the time between changes is relatively long. On the other hand, if you have a button that changes often, it may make sense to create it dynamically with PHP. The content of the button, the label, needs to be available as a string in PHP. It could be a statement setting the value of a variable. It could also be a value retrieved from a file or database.

An illustration will make this idea clear. Corporate Web sites have a section for press releases. Instead of just a list of text links, your client want a graphic of a flaming newspaper for each press release, all under the title "Hot off the Press." Each newspaper has text over the top with the headline from the press release. With a small