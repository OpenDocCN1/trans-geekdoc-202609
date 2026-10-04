
## Appendix C

| Function | Description |
| --- | --- |
| imagecoloreactalpha(name, red, green, blue, alpha) | Similar to imagecolorexact, except takes into account the alpha level. |
| imagecolorresolve(name, red, green, blue) | Returns either the index of the exact color or the closest color available in the palette of the named image. |
| imagecolorresolvealpha(name, red, green, blue, alpha) | Similar to imagecolorresolve, except takes into account the alpha level. |
| imagecolorset(name, index, red, blue) | Sets the color for the palette of the named file. |
| imagecolorsforindex(name, index) | Returns value for red, blue, and green for the specified index. |
| imagecolortotal(name) | Returns the number of available colors in the palette of the named image. |
| imagecolortrans(name[, color]) | Sets named color as transparent in the named image. |
| imagecopy(dest_name, source_name, dest_x, dest_y, source_x, source_y, source_width, source_height) | Copies an image based on named parameters. |
| imagecopymerge(dest_name, dest_x, dest_y, source_x, source_y, source_width, source_height, pct) | Similar to imagecopy, but copies an image based on named parameters including percent (when set to 100, acts identically to imagecopy). |
| imagecopymergegray(dest_name, source_name, dest_x, dest_y, source_x, source_y, source_width, source_height, pct) | Similar to imagecopymerge, except copies image in grayscale. |
| imagecopyresampled(dest_name, source_name, dest_x, dest_y, source_x, source_y, dest_width, source_height) | Copies and resizes a resampled image based on named parameters. |
| imagecopyresized(dest_name, dest_x, dest_y, source_x, source_y, dest_width, dest_height) | Copies and resizes an image based on named parameters. |
| imagecreate(width, height) | Creates a new image based on width and height. |
| imagecreatefromgd2(name) | Creates a new image from a GD file or URL. |
| imagecreatefromgd2part(name, x, width, height) | Creates a new image from a part of a GD file or URL. |

## PHP Functions

| Function | Description |
| --- | --- |
| imagecreatefromgd(name) | Creates a new image from a GD file or URL. |
| imagecreatefromgif(name) | Creates a new image from the named GIF file. |
| imagecreatefromjpeg(name) | Creates a new image from the named JPEG or JPG file. |
| imagecreatefrompng(name) | Creates a new image from the named PNG file. |
| imagecreatefromstring(name) | Creates a new image from an image stream in the named string. |
| imagecreatefromwebp(name) | Creates a new image from named file or URL. |
| imagecreatefromxbm(name) | Creates a new image from named file or URL. |
| imagecreatefromxpm(name) | Creates a new image from named file or URL. |
| imagecreatetruecolor(x_size, y, y_size) | Returns an image identifier based on a black image to the named parameters. |
| imagedashedline(name, x1, y1, x2, color) | Draws a dashed line based on named parameters. Similar to imageline. |
| imagedestroy(name) | Deletes the named image. |
| imageellipse(name, cx, cy, width, height, color) | Draws an ellipse based on the named parameters. |
| imagefill(name, x, y, color) | Fills the entry with one color based on the named parameters. |
| imagefilledarc(name, cx, cy, width, start, end, color, style) | Draws a filled ellipse based on the named parameters. |
| imagefilledellipse(name, cx, cy, width, height, color) | Draws a filled ellipse based on the named parameters. |
| imagefilledpolygon(name, points, num_of_points, color) | Draws a filled polygon based on the named parameters. |
| imagedrectangle(name, x1, y1, x2, color) | Draws a filled rectangle based on the named parameters. |
| imagefilltoborder(name, x, y, border_color, color) | Fills the entry with a color and outlines with a border color, based on named parameters. |
| imagefontheight(font) | Returns the height of the named font in pixels. |
| imagefontwidth(font) | Returns the width of the named font in pixels. |
| imagegammacorrect(name, inputgamma, outputgamma) | Corrects the gamma levels in a GD image. |

## Appendix C

| Function | Description |
| --- | --- |
| imagegd2(name[, filename, chunk_size, type]) | Outputs the named GD file to the browser based on the named parameters. |
| imagegd(name[, filename]) | Sends the named GD file to the browser. |
| imagegif(name[, filename]) | Sends the named GIF image (filename) to another file or to a browser as the named image. |
| imageinterlace(name[, interlace]) | Toggles whether or not interlacing is on or off for the named image. |
| imagejpeg(name[, filename, quality]) | Sends the named JPEG image (filename) to another file or to a browser as the named image. |
| imageline(name, x1, x2, y2, color) | Draws a solid line based on the named parameters. Similar to imagashedhedline. |
| imageloadfont(font) | Loads the named font. |
| imagepallettecopy(destination, source) | Copies the named color palette. |
| imagepng(name[, filename]) | Sends the named PNG image (filename) to another file or to a browser as the named image. |
| imagepolygon(name, points, num_of_points, color) | Draws an empty polygon based on the named parameters. |
| imagebox(text, font, size, width, angle) | Returns the coordinates for a text box using a PostScript font, based on named parameters. |
| imagesencodefont(encoding_file) | Loads the named encoding vector for a PostScript font. |
| imageextendfont(font_index, extend) | Extends a PostScript font. |
| imagesfreefont(font_index) | Frees the named PostScript font from memory. |
| imageloadfont(filename) | Loads the named PostScript font file. |
| imagesslant(font_index, slant) | Slants the named PostScript font. |
| imagetext(name, text, font, size, foreground_color, background_color, x, y[, space, tightness, antialias]) | Writes a text string using the named PostScript font and based on named parameters. |
| imagerectangle(name, x1, y1, x2, y2, color) | Draws an empty rectangle based on the named parameters. |
| imagerotate(name, angle, color) | Rotates an image based on the named parameters. Sets the flag to save with the image's alpha information. |
| imagesetbrush(name, brush) | Sets the brush for line drawing. |

## PHP Functions

| Function | Description |
| --- | --- |
| imagesetpixel(name, x, y, color) | Draws a pixel based on the named parameters. |
| imagesetstyle(name, style) | Sets the style for line drawing. |
| imagesetthickness(name, thickness) | Sets the thickness for line drawing. |
| imagesettile(name, tile) | Sets the tile image for fill functions. |
| imagestring(name, font, x, y, string, color) | Draws a horizontal string based on the named parameters. |
| imagestringup(name, font, x, y, string, color) | Draws a vertical string based on the named parameters. |
| imagesx(name) | Determines the width of the named image. |
| imagesy(name) | Determines the height of the named image. |
| imagetruecolortpalette(name, dither, colors) | Converts a true color image to a color palette based on the named parameters. |
| imagettfbox(size, angle, font_filename, text) | Draws a text box using the TrueType font and based on the named parameters. |
| imagetext(name, size, x, y, color, font_filename, text) | Writes a text string using the TrueType font. |
| imagetypes() | Displays the image types supported by the PHP version currently used. |
| iptembed(data, filename) | Embeds International Press Telecommunications Council (IPTC) data into a JPEG file. |
| iptcparse(iptcblock) | Parses an IPTC block into tags. |
| jpeg2wbmp(jpegfilename, wbfilename, height, width, threshold) | Converts a JPEG file into a WBMP file. |
| png2wbmp(pngfilename, wbfilename, height, width, threshold) | Converts a PNG file into a WBMP file. |

read_exif_data(filename)

## Mail Functions

Use these functions to send mail directly from your PHP script.

| Function | Description |
| --- | --- |
| ezmlm_hash(addr) | Displays the hash value used by EZLM scripts. |
| mail(to, subject, message[], headers[]) | Sends mail based on the named parameters. |
