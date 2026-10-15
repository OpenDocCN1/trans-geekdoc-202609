
require_once('db_definitions.php');  

if (isset($_GET['state'])) {  

   try {  

     $pix = getGalleryByState($dbRead, $_GET['state']);  

     if ($pix) {  

        // generate the new widget  

     }  

   } catch (Exception $e) {  

        echo $e->getMessage();  

   }  

}

**13** In gallery.php, locate the `foreach` loop that populates the gallery widget (it should be around lines 108–110). Copy it to your clipboard, and paste it in load_gallery.php under the “generate the new widget” comment. Remove the opening and closing PHP tags from the code you just pasted. The finished code in load_gallery.php looks like this:

<?php  

require_once('library.php');  

require_once('db_definitions.php');  

if (isset($_GET['state'])) {  

   try {  

     $pix = getGalleryByState($dbRead, $_GET['state']);  

     if ($pix) {  

        // generate the new widget  

        **foreach ($pix as $pic) { ?>**  

        **<li> <a href="../../cms/image_upload/<?php echo $pic['filename']; ?> title="<?php echo $pic['name'] . ': ' . $pic['caption']; ?>"> <img src="../../cms/image_upload/<?php echo $pic['filename']; ?>" width="120" alt="<?php echo $pic['caption']; ?>" /> </a> </li> <?php }**  

     }  

   } catch (Exception $e) {  

        echo $e->getMessage();  

   }  

}

This script takes the value of `state` passed to it by the `GET` method and uses it to generate the `<li>` elements for the gallery widget. This listing uses links relative to the document, but if your phpcs5 site is in a virtual host, the `../..` at the beginning of the file paths is not needed.

**14** To test this script in Live View, you need to pass a value to it using the `GET` method. Choose View > Live View Options > HTTP Request Settings.

In the dialog box that opens, click the plus button next to “URL request,” and type **state** in the Name field and **California** in the Value field. Set the Method menu to **GET**, and click OK.

![image](graphics/fig12_21.jpg)

If your testing environment is in a virtual host and the image paths are relative to the site root (in other words, they begin with a leading slash), you can test the page immediately.

If you’re using a subfolder of localhost, you need to add `../` to the beginning of the image paths so they begin `../../../cms`. This is a temporary measure, because the script is lower in the site hierarchy than gallery.php.

Save load_gallery.php, select Split or Design if you’re still in Code view, and click Live View. You should see the thumbnail images related to California with a bullet point to the left of each one. The bullet points are suppressed by CSS when the widget is displayed in gallery.php.

Exit Live View. If you added the extra `../` at the beginning of the image paths, delete it, and save the script again. *This is very important*. The image paths need to be relative to gallery.php, not to this script.

**15** Now test gallery.php in a browser. The Go button is hidden by jQuery, but when you select a different state from the `<select>` menu, the California thumbnails fade out and those related to the selected state fade in—without reloading the page. Proof that the page hasn’t been reloaded lies in the fact that the master details for California haven’t been replaced by the selected state.

![image](graphics/fig12_22.jpg)

You can compare your code with gallery_02.js and load_gallery.php in lesson12/completed/scripts.

#### Refreshing the list of places

Refreshing the images without the matching list of places looks odd. In theory, you could refresh the gallery and the text with the same call to the web server, but text loads more quickly than images, so two calls to the server are likely to result in a better user experience. The code for the PHP script to refresh the list of places follows the same pattern as for the gallery widget. Here it is in full (it’s in lesson12/completed/scripts/load_places.php):

<?php  

require_once('library.php');  

require_once('db_definitions.php');  

if (isset($_GET['state'])) {  

   try {  

     $places = getPlacesByState($dbRead, $_GET['state']);  

     if ($places) { ?>  

        <h2>Places to visit in <?php echo $_GET['state']; ?> </h2>  

      <?php  

        foreach ($places as $place) { ?>  

        <p><strong><?php echo $place['name']; ?>: </strong><?php echo substr($place['description'], 0, strpos($place['description'], '. ')+1); ?> <a href="details.php?place=<?php echo $place['link_name']; ?>">Learn more</a></p>  

<?php }  

   } catch (Exception $e) {  

        echo $e->getMessage();  

   }  

}

This outputs the contents of the `<div>` with the ID `places`. The jQuery `onchange` event handler needs to fade out the existing content of the `<div>`, display a message that it’s fetching new content, and then refresh the page when the response is received from the server. The amended function looks like this (the complete JavaScript file is in gallery_03.js in lesson12/completed/scripts):

stateSelector.change(function() {  

   var selectedState = stateSelector.val();  

   var gallery = $('#gallery > ul');  

   **var places = $('#places');**  

   **places.fadeOut();**  

   **places.html('<h2>Getting places to visit in ' + selectedState + '</h2>');**  

   **$.get('scripts/load_places.php', {state: selectedState}, function(data) {**  

      **places.html(data).hide();**  

    **places.fadeIn();**  

    **document.title = 'Destinations West: ' + selectedState;**  

    gallery.fadeOut();  

    $.get('scripts/load_gallery.php', {state: selectedState}, function(data) {  

      gallery.html(data).hide();  

      gallery.fadeIn();  

      $('#gallery a').lightBox(options);  

    });  

   });  

});

Notice that the second call to `$.get()` is nested inside the anonymous function that handles the response to the first call to the server. This ensures that the gallery is refreshed only after the list of places has been updated.

Amend gallery.js and copy load_places.php from lesson12/completed/scripts to the scripts folder in lesson12/workfiles, and then reload gallery.php in your browser. Selecting a new state from the `<select>` menu now refreshes the whole page. As noted earlier, Ajax shouldn’t be used to replace the entire content of a page. This is simply a demonstration of how to combine jQuery and PHP to refresh multiple page elements.

### Creating Clean URLs

Search engines and browsers are quite happy dealing with query strings, but many people dislike them, because they look ugly and are hard to remember. One reason for using the `state_name` and `link_name` values in the query strings was to make the URLs more user friendly. If your web server supports URL rewriting, you can go one step further, and use those values in the URL without a query string. Not all web servers support URL rewriting, so you need to check with your hosting company or server administrator for advice and instructions.

If your web server runs on Apache, a quick way to find out is to run `phpinfo()` and search for `mod_rewrite`. If it’s listed and your server allows you to create an .htaccess file, you should be able to use clean URLs. The rules for using `mod_rewrite` can be confusing, but it’s relatively simple to replace a single value in a query string. For example, the following URL:

http://phpcs5/lesson12/workfiles/details.php?place=Hollywood

can be rewritten like this:

http://phpcs5/destinations/Hollywood

This is done by placing an .htaccess file with the following commands in the phpcs5 site root:

<IfModule mod_rewrite.c>  

   RewriteEngine on  

   RewriteCond %{REQUEST_FILENAME} !-f  

   RewriteCond %{REQUEST_FILENAME} !-d  

   RewriteRule ^places/(.*)$ /lesson12/completed/details_clean.php?place=$1  

   RewriteRule ^states/(.*)$ /lesson12/completed/gallery_clean.php?state=$1  

</IfModule>
