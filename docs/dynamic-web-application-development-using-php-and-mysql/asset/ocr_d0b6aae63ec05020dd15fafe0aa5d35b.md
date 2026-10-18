# 4.4 Applying styles with ‘class’ and ‘id’ attributes

So far we have looked at how to apply styles to specific HTML elements, such as H1, H2 and P. In many cases this is useful, but there are occasions when we want to:

+   - Apply the same style to more than one type of HTML element.
+   - Apply a style to some, but not all, instances of a particular HTML element.
+   - Apply a style to one specific instance of an element.

To do this we need some way of labelling parts of our HTML so that we can apply styles to elements that are identified by these labels. We can do this in two ways:

+   - We can use the ‘class’ attribute. This enables us to group a number of elements as belonging to a single class. Then we can apply a style to all members of the class.
+   - We can use the ‘id’ attribute. This can be used to give an element a unique id. This id can be used to apply a style that is not used anywhere else in the document.

# Using the ‘class’ attribute

The class attribute can be applied to many elements. In addition, a given element can belong to more than one class. The class attribute is very useful as a way of applying styles across a range of different elements. For example, let us assume that we want both major headings (H1) and subheadings (H2) to be centred. We could, of course, apply the same style separately to both H1 and H2 elements in the style sheet. However a more flexible and maintainable approach is to use a class attribute. The first step is to identify both H1 and H2 elements as belonging to the same class. The name of a class is decided by the author of the page. In the next example we apply the class name ‘heading’ to all instances of both H1 and H2 elements.

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
"http://www.w3.org/TR/html4/strict.dtd">
<HTML>
<HEAD>
    <LINK href="webhomecover.css" rel="stylesheet" type="text/css">
    <TITLE>Our Insurance Cover</TITLE>
</HEAD>
<BODY>
    <!-- File: example4-5.htm -->
    <H1 class="heading">We provide the following types of insurance</H1>
    <H2 class="heading">Buildings Cover</H2>
    <P>You may think you're "safe as houses" but you'd be surprised how many
things can damage the building you live in. Fires, earthquakes, subsidence, run-
away trucks, cricket balls through windows or the occasional meteor. Best to be
covered!
    </P>
    <H2 class="heading">Contents Cover</H2>
    <P>You may not realise just how much the stuff you have would cost to replace.
If the burglars move in while you're on holiday, could you afford to replace the
TV, the stereo, the chairs, the cupboards, the crockery, etc?
    </P>
```