
their support of gif images. There, if you want to use the GD functions with gif images, you will need a version of the GD libraries older than 1.6. However, these older libraries do not support png files. Versions later than 1.6 do support png.

## TABLE E-29 GD FUNCTIONS

| Function | Returns | Action |
|---|---|---|
| imagecreate(int x_size, int y_size) | int | Creates a new image |
| imagetypes(void) | int | Returns the types of images supported in a bitfield — 1=gif, 2=jpeg, 4=png, 8=wbmp |
| imagecreatefromgif (string filename) | int | Creates a new image from GIF file or URL |
| imagecreatefromjpeg (string filename) | int | Creates a new image from JPEG file or URL |
| imagecreatefrompng (string filename) | int | Creates a new image from PNG file or URL |
| imagecreatefromwbmp (string filename) | int | Creates a new image from WBMP file or URL |
| imagegif(int im [, string filename]) | int | Outputs GIF image to browser or file |
| imagepng(int im [, string filename]) | int | Outputs PNG image to browser or file |
| imagejpeg(int im [, string filename [, int quality]]) | int | Outputs JPEG image to browser or file |
| imagewbmp(int im [, string filename]) | int | Outputs WBMP image to browser or file |
| imagedestroy(int im) | int | Destroys an image |
| imagecolorallocate(int im, int red, int green, int blue) | int | Allocates a color for an image, will usually be assigned to a variable for later use. |

## TABLE E-29 GD FUNCTIONS (Continued)

| Function | Returns | Action |
|---|---|---|
| `imagepalettecopy(int dst, int src, int blue)` | int | Copies the palette from the src image onto the dst img the palette to the specified color |
| `imagecolorclosesthwb(int im, int red, int green, int blue)` | int | Gets the index of the color with the hue, whiteness and blackness nearest to the given color |
| `imagecolordeallocate(int im, int index)` | int | De-allocates a color for an image |
| `imagecolorresolve(int im, int red, int green, int blue)` | int | Gets the index of the specified color or its closest possible alternative |
| `imagecolorexact(int im, int red, int green, int blue)` | int | Gets the index of the specified color. Returns -1 if the color does not exist |
| `imagecolorset(int im, int col, int red, int green, int blue)` | int | Sets the color for the specified palette index |
| `imagecolorsforindex(int im, int col)` | array | Gets the colors for an index, in red, green, and blue |
| `imagegammacorrect(int im, double inputgamma, double outputgamma)` | int | Applies a gamma correction to a GD image |
| `imagesetpixel(int im, int x, int y, int col)` | int | Sets a single pixel; the x and y coordinates start at the top left, and col is the color for the pixel |
| `imageline(int im, int x1, int y1, int x2, int y2, int col)` | int | Draws a line |
| `imagedashedline(int im, int x1, int y1, int x2, int y2, int col)` | int | Draws a dashed line |
| `imagerectangle(int im, int x1, int y1, int x2, int y2, int col)` | int | Draws a rectangle |

| Function | Returns | Action |
|---|---|---|
| imagefilledrectangle (int im, int x1, int y1, int x2, int y2, int col) | int | Draws a filled rectangle |
| imagearc(int im, int cx, int cy, int w, int h, int s, int e, int col) | int | Draws a partial ellipse |
| imagefilltoborder(int im, int x, int y, int border, int col) | int | Fills the image im, to the borders specified by x and y coordinates with the color in the fifth argument |
| imagefill(int im, int x, int y, int col) | int | Floods fill starting at the x and y coordinates using the color specified in the fourth argument |
| imagecolorstotal(int im) | int | Returns the number of colors in an image's palette |
| imagecolortransparent (int im [, int col]) | int | Defines a color as transparent. Returns the identifier of the new color |
| imageinterlace(int im [, int interlace]) | int | Enables or disables interlace |
| imagepolygon(int im, array point, int num_points, int col) | int | Draws a polygon. The array will take the following form: points[0] = x0, points[1] = y0, points[2] = x1, points[3] = y1 |
| imagefilledpolygon(int im, array point, int num_points, int col) | int | Draws a filled polygon |
| imagefontwidth(int font) | int | Gets font width |
| imagefontheight(int font) | int | Gets font height |
| imagechar(int im, int font, int x, int y, string c, int col) | int | Draws a character |

## TABLE E-29 GD FUNCTIONS (Continued)

| Function | Returns | Action |
|---|---|---|
| imagecharup(int im, int font, int x, int y, string c, int col) | int | Draws a character rotated 90 degrees counterclockwise |
| imagestring(int im, int font, int x, int y, string str, int col) | int | Draws a string horizontally |
| imagestringup(int im, int font, int x, int y, string str, int col) | int | Draws a string vertically — rotated 90 degrees counterclockwise |
| imagecopy(int dst_im, int src_im, int dst_x, int dst_y, int src_x, int src_y, int src_w, int src_h) | int | Copies part of an image |
| imagecopymerge(int src_im, int dst_im, int dst_x, int dst_y, int src_x, int src_y, int src_w, int src_h, int pct) | int | Merges one part of an image with another |
| imagecopyresized(int dst_im, int src_im, int dst_x, int dst_y, int src_x, int src_y, int dst_w, int dst_h, int src_w, int src_h) | int | Copies and resizes part of an image |
| imagesx(int im) | int | Gets image width |
| imagesy(int im) | int | Gets image height |
| imagettfbbox(int size, int angle, string font_file, string text) | array | Gives the bounding box of a text using TrueType fonts |
| imagettftext(int im, int size, int angle, int x, int y, int col, string font_file, string text) | array | Writes text to the image using a TrueType font |
| imagepsloadfont(string pathname) | int | Loads a new font from specified file |

| Function | Returns | Action |
|---|---|---|
| imagepsfreefont (int font_index) | bool | Frees memory used by a font |
| imagepsextendfont (int font_index, double extend) | bool | Extends or condenses (if extend < 1) a font |
| imagepstext(int image, string text, int font, int size, int xcoord, int ycoord [, int space, int tightness, double angle, int antialias]) | array | Draws a text string over an image |
| imagepsloadfont(string pathname) | int | Loads a new font from specified file |
| imagepsfreefont(int font_index) | bool | Frees memory used by a font |
| imagepsencodefont(int font_index, string filename) | bool | Changes a font's character encoding vector |
| imagepsextendfont(int font_index, double extend) | bool | Extends or condenses (if extend < 1) a font |
| imagepsslantfont(int font_index, double slant) | bool | Slants a font |
| imagepstext(int image, string text, int font, int size, int xcoord, int ycoord [, int space, int tightness, double angle, int antialias]) | array | Rasterizes a string over an image |
| imagepsbbox(string text, int font, int size [, int space, int tightness, int angle]) | array | Returns the bounding box needed by a string if rasterized |
| imagepsbbox(string text, int font, int size [, int space, int tightness, int angle]) | array | Returns the bounding box needed by a string if rasterized |

![](img/de0823012275cf4ceebdb822a56e6b71_510_0.png)

Use of these functions requires the GD library from http://www.boutell.com/gd/ and for PHP to be compiled --with-gd.

## Table E-30 IMAP FUNCTIONS

| Function | Returns | Action |
|---|---|---|
| `imap_open(string mailbox, string user, string password [, int options])` | int | Opens an IMAP stream to a mailbox |
| `imap_popen(string mailbox, string user, string password [, int options])` | int | Opens a persistant IMAP stream to a mailbox |
| `imap_reopen(int stream_id, string mailbox [, int options])` | int | Reopens an IMAP stream to a new mailbox |
| `imap_close(int stream_id [, int options])` | int | Closes an IMAP stream |
| `imap_append(int stream_id, string folder, string message [, string flags])` | int | Appends a new message to a specified mailbox |
| `imap_num_msg(int stream_id)` | int | Gives the number of messages in the current mailbox |
| `imap_ping(int stream_id)` | int | Checks if the IMAP stream is still active |
| `imap_num_recent(int stream_id)` | int | Gives the number of recent messages in current mailbox |
| `imap_expunge(int stream_id)` | int | Permanently deletes all messages marked for deletion |
| `imap_headers(int stream_id)` | array | Returns headers for all messages in a mailbox |
| `imap_body(int stream_id, int msg_no [, int options])` | string | Reads the message body |
