```
```
   1  <body>
   2  <div id="container">
   3    <div id="top">
   4      <h1>Header</h1>
   5    </div>
   6    <div id="leftnav">
   7      <p>
   8      Some text goes here...
   9      </p>
  10    </div>
  11    <div id="content">
  12      <h2>Subheading</h2>
  13      <p>
  14        Some text goes here...</p>
  15      </p>
  16      Some text goes here
  17    </p>
  18  </div>
  19  <div id="footer">
  20    Footer
  21  </div>
  22 </div>
  23 </body>```
```

You may be surprised at just how short and un-complicated it is. Let’s take a look at this code in a little more detail, because understanding the basics of div-based page layout is vital if you want to know more about how web sites work.

On line 2 we create a div and we name it container. This is the overall div that contains the rest of the page. It doesn’t matter what names you choose for your divs, but many web people choose to call the main div the container.

On line 3 we create another div called top. This is effectively inside the container because we haven’t yet closed the container div. The top div gets closed on line 5, and its contents (just an h1 heading) appear on line 4.

Between lines 6 and 10 we create another div called leftnav, the contents of which is just a single paragraph. Lines 11 to 18 hold the content div, which is the right-hand column in the illustration above. Lines 19 to 21 create our footer div.

Finally, on line 22, we close the container div.