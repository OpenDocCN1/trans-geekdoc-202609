The Traveler's Journal section is composed of three parts: a title, an author byline, and the body text of the article. The title is enclosed in a heading, and the body text is marked up in <p> tags, so in both cases the HTML markup represents the content reasonably well. The author byline is not so easy to categorize. It's represented in bold, using the <strong> tag. However, the author byline is bolded not because it is stronger, or more emphatic, than the surrounding text, but because it performs another function: it gives credit to the author. Again, since HTML doesn't have an <author_byline> tag, this is a good opportunity to create a custom CSS style.

The result of this new style, which we will call .author, will merely add bold to the element to which it is attached (in this case, a <p> tag), and it won't look any different in a browser than it does now. But making this change will make the code describe the text a little more meaningfully, and you'll also see the concept of inheritance in action again.

![](bbox=[0.24, 0.36, 0.64, 0.65])

2) Click New CSS Style. In the New CSS Style dialog, select Class in the Selector Type group, and verify that newland.css is still specified in the Define in group. In the Name field, type .author. Click OK.

![](bbox=[0.24, 0.77, 0.68, 0.91])