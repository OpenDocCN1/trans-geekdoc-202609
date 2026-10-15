
A major advantage of the Widget Browser is that it provides a visual context for you to change a widget’s default settings and save your own presets. The degree of configuration possible within the Widget Browser depends on how the author has set it up, but Andres Cayon’s LightBox Gallery Widget has many options.

## Creating your own widget preset

The following instructions show how to change the color scheme and adjust the layout ready for insertion into gallery.php.

1. Open the Adobe Widget Browser, if necessary, select My Widgets, and click the LightBox Gallery Widget thumbnail.

2. Make sure the Preview button at the top right of the Widget Browser is selected, and select “Vertical white” in the Developer Presets.

3. Click Configure at the bottom left to display the available options.

![Image](graphics/fig12_07.jpg)

The sliding panels on the left provide access to the widget’s editable features. Hover your pointer over a setting to display a tooltip describing its purpose. Changes are reflected immediately in the Live View tab on the right.

4. Type `Vertical phpcs5` in the Name field at the bottom right. Adding a description is optional.

5. Click GALLERY to reveal the next options. Change Width from 120 to `240`, and leave the other settings unchanged. Live View displays the thumbnails in rows of two.

6. Click THUMBNAILS to reveal the options for styling the thumbnails.

7. Click the Background color box, and select white from the color palette.

8. Click the Hover Background color box. When the pointer is over the thumbnails, they will have a sky blue border. Type `79B4D9` into the text box at the top of the color palette, and press Enter/Return to apply the value.

![Image](graphics/fig12_08.jpg)

### ![Image](graphics/note.jpg)**NOTE:**

The color palette in the Widget Browser doesn’t use a hash sign at the beginning of the color value. At the time of this writing, moving the pointer over any of the color swatches changes the color displayed next to the hexadecimal value. However, the correct color is registered when you press Enter/Return.

9. Change Bottom Border from 20 to `10`, and set all Margin values to `0`.

10. Click IMAGE CONTAINER BOX to display the options for the full size image. Change Opacity to `0.6`, and select light gray (CCCCCC) for Background. These two settings control the color and transparency of the page when the full size image is displayed.

You can test the effect by clicking one of the thumbnails in the Live View tab. Resize the Widget Browser, if necessary, to see the full effect.

11. The ICONS section lets you choose your own images for a loading indicator (such as an animated `.gif` file), as well as next, previous, and close buttons. The defaults are fine.

12. The INTERNATIONALIZATION section controls the text used to display the image count (for example, “Image 3 of 10”). The defaults are fine for a website in English. JavaScript is Unicode-compliant, so you can use accented characters or nonalphabetic scripts for other languages.

13. Save the changes by clicking Save Preset at the bottom right of the Widget Browser. *This is very important*. If you forget to do so, your settings won’t be reflected in the widget when you insert it in the page in Dreamweaver.

The Widget Browser returns you to the normal Preview screen with “Vertical phpcs5” listed under MY PRESETS.

14. Close the Widget Browser. You’ll be working in Dreamweaver for the rest of this lesson.

## Inserting a widget in a page

The integration of the Widget Browser with Dreamweaver CS5 makes it very easy to insert a preconfigured widget into a page. Here’s how you do it.

1. Open your copy of gallery.php in the lesson12/workfiles folder, and click anywhere inside the `<h2>` text that reads “Places to visit in.”

2. In the Tag selector at the bottom of the Document window, click `<div#places>` to select the `<div>` that contains the heading. Dreamweaver’s visual aids display the margins on both sides as hatched areas. (Choose View > Visual Aids > CSS Layout Box Model if you can’t see the hatched areas.)

![Image](graphics/fig12_09.jpg)

The gallery widget is designed to fit in the 240-pixel margin on the left of the `<div>`. To position the insertion point correctly, press the left keyboard arrow once. Open Split view to confirm that the insertion point is immediately to the left of the opening `<div>` tag, as shown at the beginning of line 12 in the following screen shot.

![Image](graphics/fig12_10.jpg)

3. Choose Insert > Widget, and select LightBox Gallery Widget and the “Vertical phpcs5” preset in the Widget dialog box.

![Image](graphics/fig12_11.jpg)

4. Click OK to insert the widget. It should be inserted in the margin to the left of the text. While selected, it’s surrounded by a turquoise border with a tab at the top left indicating the widget type and its ID. The thumbnails are represented by broken image icons.

### ![Image](graphics/note.jpg)**NOTE:**

If you can’t see the widget’s turquoise border and tab, choose View > Visual Aids, and click Invisible Elements.

![Image](graphics/fig12_12.jpg)

5. Save gallery.php. Dreamweaver displays Copy Dependent Files, which lists 17 files that will be inserted into various folders when you click OK. The number of files and their ultimate location depends on the widget you have chosen. See the sidebar “Keeping Track of a Widget’s Files.”

If your phpcs5 site is in a virtual host, the broken image icons will be replaced by thumbnail images as soon as you click OK. If you’re working in a subfolder of localhost, there’s no change. However, it doesn’t matter, because you’re not going to use the default images anyway.

6. Look at the Dependent Files toolbar at the top of the Document window. In addition to Source Code and destinations.css, four new files have been added: `jquery.js`, `lightbox.js`, `lightbox.css`, and `sample_lightbox_layout.css`.

### Keeping Track of a Widget’s Files

Most widgets insert a mixture of images, style sheets, and JavaScript files. Spry widgets accessed through the Widget Browser keep all related files together in a folder called Spry-UI-1.7. Other widgets follow their own conventions.

The LightBox Gallery Widget uses three separate folders in your site root: css, images, and scripts. If the folders already exist, the widget’s files are mixed in with yours. It also creates a subfolder called lightbox in the images folder. This is what the folders contain:

- **css.** Two style sheets, lightbox.css and sample_lightbox_layout.css

- **images.** Ten images with names beginning with lightboxdemo

- **images/lightbox.** Five navigation images

- **scripts.** Two JavaScript files, jquery.js and lightbox.js

Deleting a widget removes the code and links from the page but not the files that have been added to your site, because they might be required by other pages. So, it’s important to read the Copy Dependent Files alert to know where all the files will be stored. If you’re not sure whether to use a widget, set up a separate test site in Dreamweaver to avoid cluttering your file structure with unwanted files.

7. Open gallery.php in Code view, and make sure that Source Code is selected in the Related Files toolbar. In the `<head>` of the page, you’ll see that the external JavaScript and CSS files have been attached (around lines 7–10). Immediately following is a large block of embedded CSS (around lines 11–65). The `<style>` block begins with the following comment:

/\* BeginOAWidget\_Instance\_2127022: #gallery \*/

At the end of the block is a similar comment:

/\* EndOAWidget\_Instance\_2127022 \*/

Instead of editing the external style sheets, the Widget Browser exploits the CSS cascade by embedding all your changes in the `<head>` of the page. The comments enable Dreamweaver to identify the relevant code if you decide to delete the widget.
