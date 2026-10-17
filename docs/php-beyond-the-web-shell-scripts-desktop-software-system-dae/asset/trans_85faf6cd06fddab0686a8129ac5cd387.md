

本章按类别列出了可用于在 PHP 中处理不同文件和数据格式的扩展/库/绑定。在每个类别中，你会先找到库名称，然后是它支持的文件类型列表（为简洁起见，按其常见文件扩展名指定），以及该库的主网站。如果没有常见的文件扩展名（例如流式数据格式），则使用格式名称代替。

下面的列表并不详尽，且并非所有库都允许同时读取和写入给定格式，或支持格式的所有功能。在为项目选择库之前，请查看相关文档并尝试使用。如果你没有找到能帮助你处理所需文件格式的库，请尝试使用你喜欢的搜索引擎！如果你知道或找到一个未列出的库，请发邮件给我（author@phpbeyondtheweb.com）。

## Office 文档

`OpenDocument` : odt  

[http://pear.php.net/manual/en/package.fileformats.opendocument.php](http://pear.php.net/manual/en/package.fileformats.opendocument.php)

`PHPExcel` : ods, gnm, gnumeric, xlsx, xls (biff), xls (SpreadsheeML), htm, html, sky, slk, sylk, csv, pdf  

[https://github.com/PHPOffice/PHPExcel](https://github.com/PHPOffice/PHPExcel)

`php-excel-reader` : xls (biff)  

[http://code.google.com/p/php-excel-reader/](http://code.google.com/p/php-excel-reader/)

`Excel Writer (XML) for PHP` : xls (SpreadsheeML)  

[http://sourceforge.net/projects/excelwriterxml/](http://sourceforge.net/projects/excelwriterxml/)

`php-export-data` : xls (SpreadsheeML), csv, tsv  

[https://github.com/elidickinson/php-export-data](https://github.com/elidickinson/php-export-data)

`Spreadsheet_Excel_Writer` : xls (biff)  

[http://pear.php.net/manual/en/package.fileformats.spreadsheet-excel-writer.php](http://pear.php.net/manual/en/package.fileformats.spreadsheet-excel-writer.php)

`SimpleExcel` : xlsx, htm, html, csv, tsv, json  

[http://faisalman.github.com/simple-excel-php/](http://faisalman.github.com/simple-excel-php/)

`PHPPowerPoint` : pptx  

[http://phppowerpoint.codeplex.com/](http://phppowerpoint.codeplex.com/)

`PHPWord` : docx  

[http://phpword.codeplex.com/](http://phpword.codeplex.com/)

`Cairo extension` : pdf, ps, svg  

[http://www.php.net/manual/en/book.cairo.php](http://www.php.net/manual/en/book.cairo.php)

`tcPDF` : pdf  

[http://www.tcpdf.org/](http://www.tcpdf.org/)

`DomPDF` : pdf  

[https://github.com/dompdf/dompdf](https://github.com/dompdf/dompdf)

`mPDF` : pdf  

[http://www.mpdf1.com/mpdf/index.php](http://www.mpdf1.com/mpdf/index.php)

`Haru PDF extension` : pdf  

[http://www.php.net/manual/en/book.haru.php](http://www.php.net/manual/en/book.haru.php)

`PDF extension (PDFlib)` : pdf  

[http://www.php.net/manual/en/book.pdf.php](http://www.php.net/manual/en/book.pdf.php)

`FDF extension` : fdf  

[http://www.php.net/manual/en/book.fdf.php](http://www.php.net/manual/en/book.fdf.php)

`DOM extension` : htm, html  

[http://www.php.net/manual/en/book.dom.php](http://www.php.net/manual/en/book.dom.php)

`Contact_Vcard` : vcf, vcard  

[http://pear.php.net/manual/en/package.fileformats.contact-vcard.php](http://pear.php.net/manual/en/package.fileformats.contact-vcard.php)

`File_MARC` : mrc, marc  

[http://pear.php.net/manual/en/package.fileformats.file-marc.php](http://pear.php.net/manual/en/package.fileformats.file-marc.php)

## 压缩、归档 & 加密

`File_Archive` : tar, gz, gzip, bz2, tgz, tar.gz, tbz, tar.bz2, zip, ar, deb  

[http://pear.php.net/manual/en/package.fileformats.file-archive.php](http://pear.php.net/manual/en/package.fileformats.file-archive.php)

`Zlib extension` : gz, gzip  

[http://www.php.net/manual/en/intro.zlib.php](http://www.php.net/manual/en/intro.zlib.php)

`BZip2 extension` : bz2  

[http://www.php.net/manual/en/book.bzip2.php](http://www.php.net/manual/en/book.bzip2.php)

`RAR extension` : rar  

[http://www.php.net/manual/en/book.rar.php](http://www.php.net/manual/en/book.rar.php)

`Zip extension` : zip  

[http://www.php.net/manual/en/book.zip.php](http://www.php.net/manual/en/book.zip.php)

`RPM extension` : rpm  

[http://www.php.net/manual/en/book.rpmreader.php](http://www.php.net/manual/en/book.rpmreader.php)

`LZF compression` : lzf  

[http://www.php.net/manual/en/book.lzf.php](http://www.php.net/manual/en/book.lzf.php)

`File_cabinet` : cab  

[http://pear.php.net/manual/en/package.fileformats.file-cabinet.php](http://pear.php.net/manual/en/package.fileformats.file-cabinet.php)

`Phar extension` : phar, tar, zip  

[http://www.php.net/manual/en/book.phar.php](http://www.php.net/manual/en/book.phar.php)

`GNU Privacy Guard extension` : gpg, pgp  

[http://www.php.net/manual/en/book.gnupg.php](http://www.php.net/manual/en/book.gnupg.php)

## 图形

`Gmagick extension` : art, avi, avs, bmp, cals, cin, cgm, cmyk, cur, cut, dcm, dcx, dib, dpx, emf, epdf, epi, eps, eps2, eps3, epsf, epsi, ept, fax, fig, fits, fpx, gif, gplt, gray, hpgl, html, ico, jbig, jng, jp2, jpc, jpeg, man, mat, miff, mono, mng, mpeg, m2v, mpc, msl, mtv, mvg, otb, p7, palm, pam, pbm, pcd, pcds, pcl, pcx, pdb, pdf, pfa, pfb, pgm, picon, pict, pix, png, pnm, ppm, ps, ps2, ps3, psd, ptif, pwp, ras, rad, rgb, rgba, rla, rle, sct, sfw, sgi, shtml, sun, svg, tga, tiff, tim, ttf, txt, uil, uyvy, vicar, viff, wbmp, wmf, wpg, xbm, xcf, xpm, xwd, yuv  

[http://www.php.net/manual/en/book.gmagick.php](http://www.php.net/manual/en/book.gmagick.php)

`ImageMagick extension` : aai, art, arw, avi, avs, bmp,bmp2,bmp3, cals, cgm, cin, cmyk, cmyka, cr2, crw, cur, cut, dcm, dcr, dcx, dds, dib, djvu, dng, dot, dpx, emf, epdf, epi, eps, eps2, eps3, epsf, epsi, ept, exr, fax, fig, fits, fpx, gif, gplt, gray, hdr, hpgl, hrz, html, ico, info, inline, jbig, jng, jp2, jpc, jpeg, jxr, man, mat, miff, mono, mng, m2v, mpeg, mpc, mpr, mrw, msl, mtv, mvg, nef, orf, otb, p7, palm, pam, clipboard, pbm, pcd, pcds, pcl, pcx, pdb, pdf, pef, pfa, pfb, pfm, pgm, picon, pict, pix, png, png8, png00, png24, png32, png48, png64, pnm, ppm, ps, ps2, ps3, psb, psd, ptif, pwp, rad, raf, rgb, rgba, rfg, rla, rle, sct, sfw, sgi, shtml, sid,mrsid, sparse-color, sun, svg, tga, tiff, tim, ttf, txt, uil, uyvy, vicar, viff, wbmp, wdp, webp, wmf, wpg, x, xbm, xcf, xpm, xwd, x3f, ycbcr, ycbcra, yuv  

[http://www.php.net/manual/en/book.imagick.php](http://www.php.net/manual/en/book.imagick.php)

`File_DICOM` : dcm  

[http://pear.php.net/manual/en/package.fileformats.file-dicom.php](http://pear.php.net/manual/en/package.fileformats.file-dicom.php)

`Ming extension` : swf, flash  

[http://www.php.net/manual/en/book.ming.php](http://www.php.net/manual/en/book.ming.php)

`Cairo extension` : pdf, svg, ps  

[http://www.php.net/manual/en/book.cairo.php](http://www.php.net/manual/en/book.cairo.php)

`EXIF extension` : exif  

[http://www.php.net/manual/en/book.exif.php](http://www.php.net/manual/en/book.exif.php)

## 音频

`MP3_id` : mp3  

[http://pear.php.net/manual/en/package.fileformats.mp3-id.php](http://pear.php.net/manual/en/package.fileformats.mp3-id.php)

`OGG/Vorbis extension` : ogg, oga, ogv, spx  

[http://www.php.net/manual/en/book.oggvorbis.php](http://www.php.net/manual/en/book.oggvorbis.php)

`php-reader` : mp3, asf, wma, wmv flac, 3gp, 3gpp, avc, dcf, m21, m4a, m4b, m4p, m4v, maf, mj2, mjp, mov, mp4, odf, sdv,qt, abs, mp1, mp2, mpg, mpeg, vob, evo, ogg, oga, ogv, spx  

[http://code.google.com/p/php-reader/](http://code.google.com/p/php-reader/)

`ID3 extension` : mp3  

[http://www.php.net/manual/en/book.id3.php](http://www.php.net/manual/en/book.id3.php)

`ktaglib extension` : mp3  

[http://www.php.net/manual/en/book.ktaglib.php](http://www.php.net/manual/en/book.ktaglib.php)

## 多媒体 & 视频

