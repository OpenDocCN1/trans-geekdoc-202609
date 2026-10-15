
1. In the Dreamweaver Files panel, expand the wordpress and wp-content folders, select the themes folder, right-click, and choose New Folder. Name the new folder `birds_phpcs5`. The new folder should be inside the themes folder at the same level as twentyten.

![Image](graphics/fig04_10.jpg)

2. Expand the twentyten folder, and double-click style.css to open it in the Document window.

3. The first eight lines of style.css look like this:

```
/*  

Theme Name: Twenty Ten  

Theme URI: http://wordpress.org/  

Description: The 2010 default theme for WordPress.  

Author: the WordPress team  

Version: 1.0  

Tags: black, blue, white, two-columns, fixed-width, custom-header, custom-background, theme-options, threaded-comments, sticky-post, translation-ready, microformats, rtl-language-support, editor-style  

*/
```

This tells WordPress what the theme is called, plus some basic information about the theme.

4. Choose File > Save As or press Ctrl+Shift+S/Shift+Cmd+S. In the Save As dialog box, navigate to the birds_phpcs5 folder, and save the file with the same name (style.css). When asked if you want to update links, click No.

5. Close the original style.css, and make sure you’re working in the version in the birds_phpcs5 folder. The file path should be visible in the Browser Navigation toolbar.

![Image](graphics/fig04_11.jpg)

Alternatively, click the Open Documents icon ![Image](graphics/open-doc.jpg) at the top of the Coding toolbar to reveal the file path.

6. The Theme Name comment must contain a unique name, which cannot consist only of numbers (that’s why it’s “Twenty Ten,” not “2010”). When creating a child theme, you need to specify the parent theme as the child theme’s template. Without these two changes, WordPress won’t recognize your child theme. Changes to the remaining comments are optional. Amend the comments at the top of style.css like this:

```
/*  

Theme Name: **Birds of a Feather**  

**Template: twentyten**  

Theme URI: **http://foundationphp.com/phpcs5/**  

Description: **Adaptation of** the 2010 default theme for WordPress.  

Author: **David Powers, but mainly** the WordPress team  

Version: 1.0  

Tags: **purple, pink,** blue, white, two-columns, fixed-width, custom-header, custom-background, theme-options, threaded-comments, sticky-post, translation-ready, microformats, rtl-language-support, editor-style  

*/
```

The parent is identified by `Template` followed by a colon and its folder name.

7. Save style.css and close it.

8. This is sufficient for WordPress to identify the new theme, but it’s a good idea to add an image to distinguish it from others in your Dashboard. The image should be about 300 pixels wide and must be called screenshot.png. Copy screenshot.png from lesson04/start/images to the birds_phpcs5 folder. The child theme folder should now contain two files.

![Image](graphics/fig04_12.jpg)

You’ll add more files later, but that’s sufficient for now.

### ![Image](graphics/tip.jpg)**TIP:**

If you create a mockup of your final design in a graphics program, such as Fireworks or Photoshop, you can create screenshot.png by scaling the mockup and exporting it as a `.png` file. If it can’t find screenshot.png, WordPress displays a text description of the theme.

#### **Activating the child theme**

The child theme needs to be activated before you can style it in Dreamweaver.

**1.** In your browser, log into the WordPress Dashboard. Depending on how you set up your testing environment, the URL should be one of the following:

• **Virtual host.** [http://phpcs5/wordpress/wp-admin/](http://phpcs5/wordpress/wp-admin/)

• **Localhost.** [http://localhost/phpcs5/wordpress/wp-admin/](http://localhost/phpcs5/wordpress/wp-admin/)

**2** Expand the Appearance section in the column on the left of the Dashboard, and select Themes. The new Birds of a Feather theme should be displayed in the Available Themes section.

![Image](graphics/fig04_13.jpg)

**3.** Click the Activate link for the Birds of a Feather theme. After a few seconds, Birds of a Feather is displayed as the Current Theme and Twenty Ten moves down to the Available Themes section.

**4.** Click the Widgets link in the Appearance menu to open the widget settings screen. The child theme inherits the default settings of the Twenty Ten theme. You can study all the options later. For now, remove the Recent Comments and Meta widgets from the Primary Widget Area by dragging them from the sidebar on the right back to the Available Widgets area.

**5.** Drag the Categories widget to move it just below the Search widget. The Primary Widget Area should now look like this:

![Image](graphics/fig04_14.jpg)

**6** Click the Background link in the Appearance menu. This allows you to set a background image and color for the site. However, it does this by generating a `<style>` block in the head of the page. It’s better to use style.css to handle this, so leave this screen unchanged.

**7.** Click the Header link in the Appearance menu. This is one of the cleverest parts of the new Twenty Ten theme. It offers a choice of eight header images for your site. You can also upload your own images. The problem is that if your image isn’t exactly the same size as used by Twenty Ten (940 × 198 pixels), you’re prompted to crop it. WordPress doesn’t crop your original, but instead makes a copy. If your image’s height is less than 198 pixels, it’s stretched. The result is often unsatisfactory.

The height and width of the header images are controlled by a custom function in the Twenty Ten theme. To change the default values, you need to override that function. Leave your browser open at the current page, and return to Dreamweaver.

**8.** Custom functions for WordPress themes are stored in a file called functions.php. If you attempt to redefine an existing function, PHP throws a fatal error, but WordPress overcomes this problem with a simple conditional statement. All the functions in the parent theme’s functions.php file are wrapped in a conditional statement that checks whether a function of the same name has already been defined. If it hasn’t, the parent theme defines the function. Otherwise, it uses the one defined by the child theme.

Choose File > New. Set Page Type to PHP, set Layout to <none>, and click Create. Switch to Code view, and delete all the HTML code inserted by Dreamweaver. You should have a completely blank page.

**9.** Add an opening PHP tag at the top of the new page, and save it as **functions.php** in the birds_phpcs5 folder.

**10** Double-click functions.php in the twentyten folder to open it in the Document window. The file contains extensive comments that help you understand what the functions are for and how to override them.

**11** Scroll down to around line 47 to locate the following code:

if ( ! isset( $content_width ) )  

  $content_width = 640;

This defines the width of the main content `<div>` in the Twenty Ten theme. As you can see, the conditional statement sets the value to 640 (pixels) only if `$content_width` hasn’t already been defined. So, to change the width to a different value, you need to add `$content_width` to functions.php in the child theme. Otherwise, this value is used.

**12** The header image for Birds of a Feather is 20 pixels wider than the Twenty Ten images, so you can expand the content by the same amount.

Switch to the empty functions.php file you created for the child theme, and add the following code after the opening PHP tag:

<?php  

**$content_width = 660;**

**13** Switch back to the Twenty Ten version of functions.php, and scroll down to locate the following line of code (around line 53):

if ( ! function_exists( 'twentyten_setup' ) ):

This conditional statement checks whether a function called `twentyten_setup()` has already been defined. If it hasn’t, it creates the function, which—as the name suggests—defines the default settings for the Twenty Ten theme.
