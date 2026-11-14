```
</ul>
</div>
<div class="page">
<div class="content">
```

+   3. Create a new file to be named header.html and stored in the includes directory.

+   4. Paste in the copied code.

+   5. Save the file.

# # Adding Dynamic Functionality to the Header

The next series of steps add dynamic functionality to the HTML template by incorporating PHP within the HTML. You'll want to do this for anything that might change on a page-by-page basis or otherwise won't be static. For the header file, there are two areas that should be dynamic: the page title and the highlighting of the top navigation link (see the first tab in Figure 3.7).

+   1. In header.html, use an if-else clause to define the page title:

```
<title><?php if (isset($page_title)) {
echo $page_title;
} else {
echo 'Knowledge is Power: And It Pays to Know';
}
? ></title>
```

The page's title shows at the top of the browser window, in bookmarks, and in the browser's history; it should be different from one page to the next. The aptly named $page_title variable will be available to the header file to represent that value. However, proper programming says that you shouldn't assume that the variable exists. So this code first checks if that variable is set (that is, has a value). If it is, that value will be printed as the page's title. If $page_title is not set, a default title will be used.

+   2. Remove the list items (between the opening and closing MENU comments) that constitute the top navigation tabs.

The navigation tab for the currently viewed page has a specific CSS class applied to it, which changes how it appears. You could use JavaScript to create this effect, but for easy, all-browser compatibility, I'll make this happen in PHP.