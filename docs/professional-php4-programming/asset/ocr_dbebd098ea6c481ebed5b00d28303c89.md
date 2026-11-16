```
$body .= "Name: $name\n";
$body .= "E-Mail: $email\n\n";
$body .= "Comments: \n$comment\n";
mail("devon@sitetronics.com", "WAPMail", $body, "From: $email");
$text = new HAW_text("Thank you for your input!");
$text->set_br(1);
$link = new HAW_link("Home", "homepage.wml");
$page->add_text($text);
$page->add_link($link);
$page->create_page();
?>
```

# Image Creation and Manipulation

The GD image manipulation library is a useful library allowing the dynamic creation and modification
of images from PHP. It can be downloaded from http://www.boutell.com/gd/.

# Installing the GD Library

Windows users will need to obtain the dynamic module (which can be found in the Windows
distribution of PHP) and place it in their extensions directory. UNIX users will need to obtain the
libpng (http://www.libpng.org/pub/png/) and zlib (http://www.info-zip.org/pub/infozip/zlib/) libraries,
and optionally the FreeType (http://www.freetype.org/) and LibJPEG (ftp://ftp.uu.net/graphics/jpeg/)
libraries, and install them before making and installing GD. The following installation instructions
assume X-Windows and automake are installed:

+   - Installing zlib is a snap: simply configure with "./configure --shared" and "make" and
+   "make install".
+   - After unpacking libpng, copy the makefile that matches your OS distribution into the top
+   libpng directory (for example, to copy the standard UNIX makefile, you would "cp
+   scripts/makefile.std makefile"). Check out the makefile and pngconf.h to check for
+   any changes you wish to make, then run "make install".
+   - To install LibJPEG, you will need to run "./configure --enable-shared", then "make"
+   and "make install".
+   - Installing the FreeType library is a bit more difficult – configure with "./configure --
+   enable-shared --x-includes=/usr/X11R6/include --x-
+   libraries=/usr/X11R6/lib". Next, run "make" and "make install".
+   - Finally, build and install GD by unpacking it and running "make" and "make install".

To add GD support to PHP, you simply add --with-gd=/usr/local/gd (or the directory in which
the GD library was installed) to the configure script, and build and install PHP as normal.