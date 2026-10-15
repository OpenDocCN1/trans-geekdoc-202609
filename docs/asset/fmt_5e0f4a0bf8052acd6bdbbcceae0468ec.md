
点击“浏览”按钮（位于“背景图像”文本框旁），进入 `birds_phpcs5/images` 文件夹，并选择 `birds_bg_gradient.jpg`。

在“背景重复”下拉菜单中选择 `repeat-x`。

点击“确定”后，页面背景会从浅米色改为从浅紫渐变至浅灰的垂直渐变。

## 12. 接下来进行一些 CSS3 魔法——将侧边栏从右侧移至左侧

默认样式规则会将侧边栏浮动到右侧，并通过主内容的 margin 创建间距。可以通过将侧边栏浮动到左侧并给出足够的负左 margin，使其位于主内容的对侧。在此之前，需要调整主内容的 margin。

点击“检查”按钮，移动光标直至选中页面左侧的主内容。其 margin 由包装 `<div>` 控制，点击文档窗口底部的“标签选择器”中的 `<div#container>`。属性面板显示其 `margin` 属性为 `0 -240px 0 0`，即右侧已为侧边栏预留了 240 像素的空间。需要将这部分空间移到对侧。将 margin 属性改为 `0 0 0 240px`，这会把主内容移至页面右侧，同时把侧边栏推至下方。

![Image](img/tip.jpg) TIP：

Twenty Ten 样式表中对包装 `<div>` 使用负右 margin 非常不寻常，原因是其 `width` 属性被设为 `100%`。负值会缩小宽度，从而为侧边栏腾出空间。如果想复习 CSS 知识，可以参考我的书籍 *Getting StartED with CSS*（friends of ED，2009，ISBN: 978-1-4302-2543-0）。

## 13.

再次点击“检查”按钮，移动光标直至整个侧边栏被高亮。选择它，Tag 选择器会选中 `<ul.xoxo>`。想要编辑的规则是它在层级结构中的下一条规则。点击“标签选择器”中的 `<div.widget-area#primary>`。

属性面板显示没有样式，需向上移动层级。下一条规则 `#primary, #secondary` 正是需要修改的规则。

![Image](img/fig04_21.jpg)

## 14.

将 `float` 的值从 `right` 改为 `left`。侧边栏会移动到页面左侧，但仍位于主内容下方。

## 15.

点击“添加属性”，输入 `margin-left`，并将值设为 `-1180px`（即负 1180 像素）。侧边栏在底层 HTML 结构中位于主内容之后，但结合左浮动和大负左 margin，它可以跨越主内容，正确地位于左侧边距区域。

## 16.

为主内容添加一些 CSS3 的炫酷效果。点击“检查”按钮，移动光标直至主内容被高亮并选择它。Tag 选择器显示已选中 `<div.post-1 post type-post hentry category-uncategorized#post-1>`。虽然这是一个复杂的 CSS 选择器，但“规则”面板会选中层级结构最底部的 `hentry` 类规则，该规则目前仅设置了 `margin` 属性。

虽然可以通过 CSS 样式面板添加更多属性，但直接在样式表中编辑更为便捷。样式表超过 1,000 行，快速定位正确规则的办法是使用“代码导航”。

在 Windows 上按住 Alt 键，在 Mac 上按住 Cmd+Opt，然后点击“欢迎使用 WordPress”默认帖子的任意位置，即可启动代码导航——一种针对所点区域的上下文感知工具。虽然有许多规则影响该区域，但应在面板底部找到 `.hentry`，如下图所示。

![Image](img/fig04_22.jpg)

在代码导航中点击 `.hentry` 链接，打开样式表的分屏视图。此技巧能直接将光标定位到 `.hentry` 样式规则内部。

## 17. 按照以下方式修改样式规则：

```css
.hentry {  
  margin: 0 0 48px 0;  
  padding:5px 5px 5px 15px;  
  background-color: #FFF;  
  -moz-border-radius: 20px;  
  -webkit-border-radius: 20px;  
  border-radius: 20px;  
  -moz-box-shadow: 10px 10px 5px #888;  
  -webkit-box-shadow:10px 10px 5px #888;  
  box-shadow: 10px 10px 5px #888;  
  border: 1px solid #eee;  
}
```

以 `-moz` 和 `-webkit` 开头的属性是 CSS3 `border-radius` 与 `box-shadow` 的浏览器专用实现。按此顺序排列可确保在官方属性被浏览器支持时，效果仍能保持。

If you refresh Live View by pressing F5 or clicking anywhere in Live View, you’ll see the post now has a white background with rounded corners. In the Mac version of Dreamweaver, you’ll also see a drop shadow as shown in the following screen shot.

![Image](img/fig04_23.jpg)

### NOTE:

The Windows version of Live View fails to render the drop shadow correctly. However, if you view the finished WordPress site in a recent version of Safari, Google Chrome, or Firefox, the drop shadow is rendered correctly on both Windows and Mac OS X. Internet Explorer 8 and earlier ignores the CSS3 properties and just displays a rectangular white background.

**18** Save `style.css`.

Hopefully, by now you’ve got the picture. You use the Inspect button or Code Navigator in Live View to identify elements on the page and inspect the style rules that govern their display. The Tag selector at the bottom of the Document window shows you where the element resides in the document hierarchy. Most CSS properties are inherited, so you often need to go back up the hierarchy to find the element where a specific rule has been applied. The CSS Styles panel in Current mode also allows you to work back up the cascade of rules affecting the selected element.

Styling a web page requires patience and skill. If you have a good command of CSS, you’ll find working in Live View with these tools make styling WordPress, Joomla!, or Drupal very similar to working with a static HTML page. This lesson has concentrated on styling the front page of a WordPress site, but Live View is navigable in Dreamweaver CS5. Just hold down Ctrl/Cmd while clicking a link, and you can inspect and style all pages and views within a CMS.

To round out this lesson, let’s take a look at a WordPress template and make a slight change so that the text heading can be hidden from visual browsers. When editing CMS templates it’s a good idea to set up site-specific code hints.

#### Enabling site-specific code hints for WordPress, Drupal, and Joomla!

WordPress, Drupal, and Joomla! use many custom functions to generate the content for each page. For example, WordPress provides the `bloginfo()` function ([`codex.wordpress.org/Template_Tags/bloginfo`](http://codex.wordpress.org/Template_Tags/bloginfo)) to display information about your site. Dreamweaver uses code introspection to generate hints for your chosen CMS, speeding up editing page templates or functions.

The following instructions show how to enable site-specific code hints for WordPress in the phpcs5 site. The procedure is identical for Drupal and Joomla!

**1.** Make sure that the phpcs5 site is selected in the Files panel, and that the active document is from the same site or that all documents are closed.

**2.** Choose Site > Site-Specific Code Hints. As long as you haven’t previously set up site-specific code hints for the same site, the Site-Specific Code Hints dialog box automatically recognizes not only which CMS is installed, but also the correct folder.

![Image](img/fig04_24.jpg)

**3.** All that’s necessary is to check that the Sub-root text field points to the folder that contains the top level of the CMS. If it doesn’t, click the folder icon next to the Sub-root text field, and select the correct folder.

**4.** After checking the Sub-root text field, just click OK. That’s all there is to it.

**5.** Dreamweaver inserts a file called `dw_php_codehinting.config` into the site root and automatically cloaks it to prevent it from being uploaded to your remote server when you use site synchronization to update your files. This file is used only in your local development environment.

#### Editing a WordPress page template

The first time you dive into a WordPress template can be a baffling experience, but the Twenty Ten theme is well commented. If you understand the HTML structure of the template you’re working with, it’s not too difficult to work out where to add custom features, such as a static paragraph, or remove elements that you don’t want. As long as you make the changes to a template in a child theme, you can always delete the template and use the parent theme’s default version if you make a mistake.

**1.** Open `index.php` in the top-level wordpress folder and click Live View to display the front page of the Birds of a Feather site.

**2.** Click Live Code to display in Split view the underlying HTML output generated by WordPress. Adjust Split view so you can see the code and “Just another WordPress site” at the top right of the page (you might need to scroll horizontally in Live View).

**3.** Click between the words “Just” and “another” in Live View. Depending on the size of your monitor, this should scroll Code view so that the equivalent HTML output is in the center with the insertion point between the two words, as shown on line 24 in the following screen shot:

![Image](img/fig04_25.jpg)

You can’t edit the output in Live Code, because it’s dynamically generated by WordPress, but inspecting the output here gives you a good idea of what to look for when you open the WordPress template.

The text you clicked is in a `<div>` that has the ID `site-description`. You can also see on line 19 that the main heading has the ID `site-title`, and that the text is wrapped in a link that returns to the front page of the WordPress section of the site.

The final point to notice is that the `alt` attribute of the header image on line 26 is empty. The HTML specification requires all images to have alternative text (in the `alt` attribute), but it’s recommended to use an empty string when the image is purely decorative. This redesign incorporates text into the image, so the same text should be inserted into the `alt` attribute in case the image is not displayed for any reason.
