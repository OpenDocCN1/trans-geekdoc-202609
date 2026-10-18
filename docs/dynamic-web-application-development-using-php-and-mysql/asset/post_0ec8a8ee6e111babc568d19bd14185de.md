
the service navigation bar might include detailed use case options such as ‘change address’, ‘change level of cover’, ‘add cover’, etc.

## Breadcrumbs
The idea of breadcrumbs comes from fairy stories where the characters leave a trail of breadcrumbs through the woods in order to find their way home again. In stories, these are usually eaten by birds, leading to disaster, but this is unlikely to happen on web sites. The role of breadcrumbs is to tell the user where they are relative to the home page. Each time the user moves to a new page, another breadcrumb is added to the list, so it is easy for the user to see the path they have taken through the site. In addition, the components of the breadcrumb list should be hyperlinked, so clicking on any breadcrumb will take you to that page. Breadcrumbs are often a secondary part of the navigation bar and may be used in conjunction with a search box (Figure 2.25).

FIGURE 2.25 The ‘breadcrumbs’ pattern

![](img/b2471264f405d17994ef173e4b9cec92_66_0.png)

## Three-region layout
The three-region layout pattern is actually based largely on the patterns we have already introduced (site logo at top left, the navigation bar and breadcrumbs). If we use these patterns, two regions (the top and side navigation bars) are already used, and we are left with a main page area, which will contain the current content (Figure 2.26). This pattern is very common in web applications, and can be implemented using tables, frames or style sheets. We favour style sheets over tables and tables over frames, since one rule we should be aware of is ‘no frames on public sites’. The main reason for not using frames is that browser support is not very reliable for frames, in particular when presenting pages on the mobile Internet. However we may consider not using the three-region layout at all when supporting mobile clients, and favour simpler approaches that separate out the navigation from the content. We address these issues when we look at adaptive web applications for mobile clients in chapter 14. Although many sites still use tables for structure, increasing browser support for sophisticated style sheets makes them the more favoured approach.

FIGURE 2.26 The ‘three-region layout’ pattern

![](img/b2471264f405d17994ef173e4b9cec92_66_1.png)

## Home page
The three-region layout is recommended as a consistent layout for all the pages on a web site. The home page, however, can be an exception to the three-region layout rule, since it has a special role as the starting point for users, and can therefore have some special characteristics. It should not, however, be just a splash screen, which users may find frustrating as it may take a long time to load and run (if, for example, it includes an animation or movie, as some web sites favour). Rather, it needs to include navigation to the main use cases to enable the user to quickly and easily get started on their goals. Figure 2.27 shows a suggested outline for the home page pattern. It gives the site logo more prominence than does the three-region layout pattern, placing it in the centre of the screen: Beneath the logo there is some brief information that should convey the main message of the web site. Beneath this message, prominent links, perhaps using buttons or images, provide quick access to all the most important use cases in the system. Finally, some more information about the main features of the site may appear. Overall the intention of the home page pattern is to have a high level of impact while enabling the user to get started on their goals as quickly as possible.

## Site map
One of the suggested links for the navigation bar is the site map. Like the home page, the site map has a special role in a web application, because it provides a bird's eye view of the whole application to the user, allowing direct access to any part of the site (or at least those parts that would sensibly allow direct access) without needing to know how to navigate through other pages. Many site maps are just lists of text. However a more interesting and useful site map would provide a workflow overview, showing not just a list of links but a visual map of the routes through the web application. Exactly how the site map might appear depends on the application, but Figure 2.28 indicates some of the features that might be included: visual components that represent hyperlinks to web pages but also some indication of the links that already exist between these pages. There are many ways of laying out a graphical site map. A web search for 'graphical site map' should give you plenty of links to sites with different styles that can be used.

FIGURE 2.27 The 'home page' pattern

![](img/b2471264f405d17994ef173e4b9cec92_67_0.png)

FIGURE 2.28 The ‘site map’ pattern

![](img/b2471264f405d17994ef173e4b9cec92_68_0.png)

FIGURE 2.29 Reusing content across multiple pages

![](img/b2471264f405d17994ef173e4b9cec92_68_1.png)

## Store content in the database
Web applications often have to provide the same content across many different pages of a web site. Figure 2.29 shows a very simple example of this type of requirement. Here, we may want to add a simple footer (“© WebHomeCover.com 2000–2008”) to the bottom of every page. The last thing we would want to have to do would be to add this to every single page and have to maintain each instance of this data separately. If, for example, we had 154 pages in our web application, and we wanted to update the footer to ‘© WebHomeCover.com 2000–2009’, we would have to do this 154 times. It should be noted that the footer example has a number of simple solutions, because it is consistent across every page, but it illustrates a concept that is very common in web applications, which is that the same underlying data may need to appear in different ways across different parts of a web site. As a more complex example, consider a site where the user logs in. In applications like this, the user’s login name, or perhaps some alias, often appears somewhere on the pages that they visit after the point where they have logged in.

The most important pattern that we have in dynamic web applications is simply to store content in a database. Maintaining a web application can get very complex, and we do not want to have to copy and paste large amounts of content for every update to the application. Therefore we need to store content in one place, in the database, and construct pages dynamically. To take our simple ‘footer’ example, the string of text used for the page footer could be stored in one place, in the database, and read from that database each time it is required in a page. If the footer needs to be updated, it only needs to be updated in one place – the database.

## General design guidelines
There are many sources for general design guidelines for web applications. These examples are taken from (Sparks 2004).

- Design around existing content, not future content
  A web application should be based around what you already have, not what you might have later. This is a basic principle of agile development – we get the simplest thing possible working early and then develop it over time. An over-complex application structure designed to cater for things that might come along later is unnecessary.
- Avoid unnecessary images
  Images take time to load and every image download is a separate HTTP connection. There are many contexts (e.g. on a mobile device) where this is a major overhead. Don’t use images where text will suffice.
- Exploit hyperlinks
  Use hyperlinks as much as possible. This is really only directly relevant to static rather than dynamic content, since in a lot of dynamic content scenarios we have to guide the user through a restricted set of pathways. However we should make sure that the navigation around our site is well supported by hyperlinks.
- Use cascading style sheets (CSS)
  As well as being difficult to build and maintain, HTML that includes its own presentation specification can get very large. Using cascading style sheets (covered in Chapter 4) reduces the size of HTML page downloads.
- Make navigation flow
  This is an important aspect of web applications, because the user workflow has to make sense. We need to take care to provide the right number of user pathways from particular points in time. One important aspect is making sure that the user can backtrack correctly from any point in a web application, for example being able to get out of the checkout in an on-line purchasing situation in a controlled way.
- Visit your own site regularly
  You are more likely to spot problems in your web applications by approaching them as a user from the outside in, rather than just looking at them from the developer perspective, from the inside out.
