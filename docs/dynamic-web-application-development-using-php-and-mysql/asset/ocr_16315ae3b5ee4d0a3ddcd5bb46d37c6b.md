# FIGURE 2.12  The UML extension symbol for a) a web page and b) its stereotype equivalent

![](bbox=[0.427, 0.103, 0.686, 0.204])

# FIGURE 2.13  A simple storyboard

![](bbox=[0.194, 0.267, 0.892, 0.371])

# FIGURE 2.14  UML extension symbols for (a) a client page and (b) a form

![](bbox=[0.404, 0.454, 0.703, 0.554])

Note that in this notation, we normally use the form icon as a composition component of a client page (the black diamond indicates that the page is partly composed of the form). However if we follow the one-form-per-page usability pattern (Graham 2002), also known as button gravity because it puts the emphasis on a single ‘Submit’ button on each page, then we can dispense with the separate page icon and use the form icon to represent a complete form page.

Looking at each page in turn, we might define the home page and buildings quote page using the ‘client page’ icon, whereas the others use the ‘form’ icon. There is no requirement to use these symbols, but they can help to visualise a typical webflow, which will frequently start from a client page, then move through one or more form pages, gathering data in a ‘wizard’ style, and finally arrive at a summary page that shows the user the result of the webflow (Figure 2.15).

# 2.7  Building further use cases

So far, so good. We have written a use case realisation for the ‘Get buildings insurance quote’ use case and we have a simple storyboard. As we are performing analysis activities we have made no attempt to consider data types, page layout, component types or any