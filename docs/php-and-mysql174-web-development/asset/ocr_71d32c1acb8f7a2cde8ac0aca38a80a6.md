# Drawing Figures and Graphing Data

You can use the imagetftext() function to actually draw the text onto the button:
imagetftext($im, $font_size, 0, $text_x, $text_y, $White,
$font_name, $button_text);

This function takes a lot of parameters. In order, they are the image identifier, font size in points, the angle you want to draw the text, the starting x and y coordinates of the text, the text color, the font name, and finally, the actual text to go on the button.

> Note
The font file needs to be available on the server and is not required on the client's machine because the client will use it as an image.

# Finishing Up

Finally, you can output the button to the browser:
header('Content-type: image/png');
imagepng($im);

Then it's time to clean up resources and end the script:
imagedestroy($im);

That's it! If all went well, you should now have a button in a browser window that looks similar to the one you saw in Figure 21.5.

# Drawing Figures and Graphing Data

In the preceding application, we looked at existing images and text. We haven't yet looked at an example with drawing, so let's do that now.

In this example, you run a poll on your website to test whom users will vote for a fictitious election. You store the results of the poll in a MySQL database and draw a bar chart of the results using the image functions.

Graphing is the other thing functions are primarily used for. You can chart any data you want-sales, web hits, or whatever takes your fancy.

For this example, we first spend a few minutes setting up a MySQL database called poll contains one table holds the candidates' names in the candidate column and the number of votes they received in the num_votes column. We created a user for this database called poll, with password poll. This script is straightforward to set up, and you can create it by running the SQL script shown in Listing 21.3. You can do this piping through a root login

```
mysql -u root -pYOUR_PASSWORD < pollsetup.sql
```