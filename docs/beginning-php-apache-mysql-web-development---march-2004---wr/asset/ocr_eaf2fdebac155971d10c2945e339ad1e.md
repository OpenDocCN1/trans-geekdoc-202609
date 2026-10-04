# Appendix C

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

626