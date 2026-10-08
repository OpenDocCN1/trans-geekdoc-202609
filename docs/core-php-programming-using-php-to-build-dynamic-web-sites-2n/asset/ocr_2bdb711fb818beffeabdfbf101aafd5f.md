# Chapter 12. IMAGE FUNCTIONS

Analyzing Images

Creating JPEG, PNG, and WBMP Images

The majority of the image functions draw their functionality from the GD library, free software for manipulating images. These require the GD extension to be loaded, via php3.ini or the di extension. The functions in the first section of this chapter are not part of the GD extension and should always be available to you.

The GD library was created at Boutell.com, a company that has contributed several Open Source tools to the Web community. The library historically supported GIF image creation, but in 1999 this functionality was pulled in favor of PNG format files. The compression algorithm used in GIF creation is patented, which means permission must be granted to software authors who use PNG, on the other hand, is an open specification. It also happens to be superior to GIF. Support for PNG added to the fourth generations of the two most popular browsers, Netscape Navigator and Microsoft Internet Explorer, using PNG is feasible. In 2000, support for JPEG and WBMP images was added to GD.

The GD library's home on the Web is <http://www.boutell.com/gd/>. The URL for PNG's page home is <http://www.cdrom.com/pub/png>.

Two of the functions in this section require a special library to deal with TrueType fonts: imageffbox and imagettext. Likewise, the functions that work with PostScript fonts require their own library. Consequently, these functions may not be available to you, depending on how PHP was compiled.

Chapter 19, "Generating Graphics," makes use of the functions in this chapter to explore some practical uses.

# Analyzing Images

These functions are part of PHP's core and do not require loading an extension.

string gamma_correct_tag(string color, double original, double new)

The gamma_correct_tag adjusts an HTML color from one gamma to another. Video display hardware is given a gamma rating that describes relatively how bright images appear. Identical images appear lighter on Macintosh than on the typical Windowsel clone. The W3C has a discussion about color spaces that includes information about gamma values: <http://www.w3.org/Graphics/Color/sRGB.html>.