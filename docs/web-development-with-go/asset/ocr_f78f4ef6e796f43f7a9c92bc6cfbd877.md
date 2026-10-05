# 4.5. CONTEXTUAL ENCODING

If you are interested in learning about more HTML symbol and character codes do a quick search for “HTML character codes”.

There are several sites out there that list all of the & . . .; style codes, and you can test each out by editing the test.html file we created earlier.

This happens because otherwise it would be impossible for your browser to know whether you wanted the string <script> to show the same text on the screen, or if instead you want it to be treated as HTML code. As a result, your browser treats any text inside of < as an HTML element. If you want to show the < character on your website you need to use the &lt; string, which would be displayed as < by the browser as it renders the page.

If the html/template package hadn’t encoded the < character, your web page would have instead parsed the name as if it were an actual script and rendered one of those annoying alerts messages like in Figure 4.2.

![](bbox=[0.221, 0.574, 0.777, 0.735])

Figure 4.2: An annoying JavaScript alert