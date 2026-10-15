
### `![Image](graphics/note.jpg)`**NOTE:**

This conditional statement ends with a colon rather than an opening curly brace. This is an alternative syntax for control structures. See [http://docs.php.net/manual/en/control-structures.alternative-syntax.php](http://docs.php.net/manual/en/control-structures.alternative-syntax.php).

`14` To create your own default settings for the child theme, you need to copy the function definition to the version of functions.php in birds_phpcs5. The function definition begins like this (around line 75):

function twentyten_setup() {  

  // This theme styles the visual editor with editor-style.css to match the theme style.  

add_editor_style();

The final section of the function definition looks like this (around lines 171–178):

   'sunset' => array(  

     'url' => '%s/images/headers/sunset.jpg',  

     'thumbnail_url' => '%s/images/headers/sunset-thumbnail.jpg',  

     /\* translators: header image description \*/  

     'description' => \_\_( 'Sunset', 'twentyten' )  

   )  

 ) );  

}

Select the entire function description, and copy it to your clipboard.

`15` Paste the function definition into functions.php in the birds_phpcs5 folder. If you copied and pasted the code correctly, Dreamweaver should display “No syntax errors” in the Info Bar at the top of the Document window.

`16` Scroll down to locate this code (around line 35):

define( 'HEADER_IMAGE', '%s/images/headers/path.jpg' );

This defines the default header image for the Twenty Ten theme (the tree-lined path). To display a different image, change the filename like this:

define( 'HEADER_IMAGE', '%s/images/headers/**cormorants.jpg**' );

You’ll add this and other images to the relevant folder shortly.

`17` The next section of code defines the width and height of the header image. Change the width from 940 to **960** and the height from 198 to **150** like this:

define( 'HEADER_IMAGE_WIDTH', apply_filters('twentyten_header_image_width', **960** ) );  

define( 'HEADER_IMAGE_HEIGHT', apply_filters( 'twentyten_header_image_height', **150** ) );

`18` About 20 lines farther down is a long section of code that begins like this:

register_default_headers( array(  

  'berries' => array(  

  'url' => '%s/images/headers/berries.jpg',  

  'thumbnail_url' => '%s/images/headers/berries-thumbnail.jpg',  

  /\* translators: header image description \*/  

  'description' => \_\_( 'Berries', 'twentyten' )  

  ),

This passes a multidimensional array to `register_default_headers()`, a function new to WordPress 3.0, which defines the choice of header images offered by the theme. The default Twenty Ten images are all 940 pixels wide and 198 pixels high, so they won’t fit the child theme.

The media files for this lesson contain two header images called cormorants.jpg and seagulls.jpg, together with two smaller versions called cormorants-thumbnail.jpg and seagulls-thumbnail.jpg. Change all instances of berries in the multidimensional array to **cormorants**, and cherryblossom(s) to **seagulls**. There are only two header images, so you need to delete the other six subarrays. When you have finished, the final section of functions.php should look like this:

  register_default_headers( array(  

    '**cormorants**' => array(  

      'url' => '%s/images/headers/**cormorants**.jpg',  

      'thumbnail_url' => '%s/images/headers/**cormorants**-thumbnail.jpg',  

      /\* translators: header image description \*/  

      'description' => \_\_( '**Cormorants**', 'twentyten' )  

    ),  

    '**seagulls**' => array(  

      'url' => '%s/images/headers/**seagulls**.jpg',  

      'thumbnail_url' => '%s/images/headers/**seagulls**-thumbnail.jpg',  

      /\* translators: header image description \*/  

      'description' => \_\_( '**Seagulls**', 'twentyten' )  

    )  

  ) );  

}

`19` Save functions.php and copy cormorants.jpg, cormorants-thumbnail.jpg, seagulls.jpg, and seagulls-thumbnail.jpg from lesson04/start/images to twentyten/images/headers. The images must go in the parent theme’s folder because that’s where `register_default_headers()` expects to find them.

`20` Return to the Header page in the WordPress administrative area. Click the Background link in the Appearances menu, and then click Header to reflect the changes you have made. The Custom Header section should now display the two Birds of a Feather header images, and the text in the Upload Image section should show the new default dimensions of 960 × 150 pixels.

![Image](graphics/fig04_15.jpg)

If necessary, compare your code with lesson04/completed/functions.php.

#### **Styling the child theme**

All that remains now is to adjust the styles to give the theme its own look. Most of the remaining tasks are done in Live View and the CSS Styles panel.

**1.** Close functions.php if it’s still open, and create a new folder called **images** in the birds_phpcs5 folder. Copy birds_bg_gradient.jpg from lesson04/start/images to the new folder. You’ll use this later as a background image to the new theme.

**2.** Double-click index.php in the main wordpress folder to open it in the Document window. Switch to Design view if necessary, and click Live View. The Birds of a Feather site should display with the new default header and the edited sidebar.

![Image](graphics/fig04_16.jpg)

**3.** The header image is now wider than the menu bar. To fix that, click the Inspect button in the Document toolbar. As you move your pointer over Live View, you’ll see different sections of the page highlighted. The content of an element is light blue or aqua, padding is mauve, and margins are yellow.

Notice that as you move from element to element, the currently highlighted element is also selected in the Tag selector at the bottom of the Document window. When your pointer is over the black menu bar below the header image, you should see `<div#access>` highlighted in the Tag selector. Click the menu bar to select it.

**4** Selecting an element turns off the Inspect button, allowing you to move your pointer without highlighting other elements. Open the CSS Styles panel by clicking its tab or by choosing Window > CSS Styles. On Windows, you can also use the keyboard shortcut Shift+F11 (there is no Mac shortcut).

Make sure the Current button is selected at the top of the CSS Styles panel and that the Rules pane is visible in the middle section. If the middle section is titled About, click the Cascade icon as indicated in the following screen shot. You might need to close other panels and drag the panes inside the CSS Styles panel to see the rules and properties listed.

![Image](graphics/fig04_17.jpg)

The Rules pane displays all the style rules that affect the current selection. Sometimes you need to examine several rules before finding the right one, but on this occasion, it should be the one selected by Dreamweaver. It’s the `#access` rule shown in the preceding screen shot.

Select `#access` in the Rules pane. This reveals that the `width` property is set to `940px`. Click the value to edit it, and change the number to **960**. The px unit is controlled by a separate menu, so you don’t need to change it.

![Image](graphics/fig04_18.jpg)

As soon as you press Enter/Return to confirm the edit, the menu bar in Live View expands to match the width of the header image.

**5.** Although the header image and menu bar are now the same length, there’s a gap of about 20 pixels of white space on the left of both elements. Finding the cause of the gap is a process of elimination, but if you look farther down the page, you’ll see there’s a similar gap on both sides of the horizontal line above the footer.

Click the Inspect button again, position the pointer over the footer so that the full width below the horizontal line is highlighted, and click to select it.

![Image](graphics/fig04_19.jpg)
