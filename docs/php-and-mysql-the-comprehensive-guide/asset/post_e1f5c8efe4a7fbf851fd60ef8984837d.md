
$start = $end;
}

$pdf->Output('output.pdf', 'I');

## Listing 31.4 A Pie Chart in PDF ("tcpdf_draw_diagram.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_855_0.png)

## Figure 31.4 A Pie Chart

### 31.2.5 Write HTML

The strength of TCPDF in dealing with HTML, which you saw in the last section, is also the reason that HTML2PDF uses this PDF library as a basis.

TCPDF itself has methods for writing HTML. However, HTML2PDF is even more convenient and functionally comprehensive. To do this, simply import the HTML2PDF library and instantiate an object of the Html2Pdf class:

```
require __DIR__.'./vendor/autoload.php';
use Spipu\Html2Pdf\Html2Pdf;
$html2pdf = new Html2Pdf();
```

Everything else is then taken care of by the writeHTML(HTML) method. It takes a string with HTML code as the central parameter. This can even contain CSS and complex elements such as tables.

Listing 31.5 and Figure 31.5 show an overview of some possibilities.

```
$html2pdf = new HTML2Pdf();
$html2pdf->writeHTML('<
<style type="text/css">
table {
    border-collapse: collapse;
}
th, td {
    width: 200px;
    border: 1px solid gray;
    padding: 5px;
}
</style>
<h1>Heading</h1>
<p>An output in a paragraph with a little text and even more text. A
output in a paragraph with a little text and <strong>even</strong> more text. A
output in a paragraph with a little text and even more text. An
output in a paragraph with a little text and even more text. </p>
<hr/>
<h2 style="color: red">Heading 2</h2>
<p>An output in a paragraph with a little text and even more text. One
output in a paragraph with a little text and <strong>even</strong> more text.
more text. An output in a paragraph with a little text and even more text. An
output in a paragraph with a little text and even more text. </p>
<table>
<tr>
<th>cell heading1</th>
<th>cell heading2</th>
</tr>
<tr>
<td>Cell 1</td>
<td>Cell 2</td>
</tr>
</table>');
$html2pdf->output();
```

## **Listing 31.5 HTML Output with HTML2PDF ("html2pdf.php")**

![](img/ae7820c36e8f24c1623d26668b28e80e_857_0.png)

## Figure 31.5 HTML Output Is Converted to PDF

## 31.3 FPDF

The first "F" in FPDF stands for free. This is also the real incentive of this library—because let's be honest, most web projects are commercial. Even a hobby site often has one or two advertising banners and would therefore fall outside the definition of a noncommercial website. However, smaller sites in particular will be reluctant to spend money on a PDF library. That's reason enough to take a closer look at FPDF.

> **Note**
> At www.fpdf.org, you will not only find FPDF itself, but also a helpful manual.

### 31.3.1 Basics

As FPDF is based on PHP, you simply integrate the corresponding class. The operation is object-oriented and very simple. You define the PDF document with the FPDF object, and you specify the format as a parameter:

```
$pdf = new FPDF("P", "pt", "A5");
```

You then continue to use the methods of this object:

```
$pdf->AddPage();
$pdf->SetFont("Helvetica", "", 48);
$pdf->Cell(20,10, "Your statement!");
```

Finally, output the whole thing using the `Output()` method. Listing 31.6 shows the complete example, and you can see its output in Figure 31.6.

```
<?php
define("FPDF_FONTPATH", "font/");
require "fpdf/fpdf.php";

$pdf=new FPDF("P", "pt", "A5");
$pdf->AddPage();
$pdf->SetFont("Helvetica", "", 48);
$pdf->Cell(20,10, "Your statement!");
$data = $pdf->Output();
header("Content-type: application/pdf");
header("Content-disposition:inline;filename=output.pdf");
print $data;
?>
```

## Listing 31.6 A First Document with FPDF ("fpdf_basics.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_858_0.png)

## Figure 31.6 The First Document

> **Note**
>
> FPDF has some special features. For example, as with most graphics programs, the origin is in the top-left-hand corner by default. You can also select the unit very flexibly.

### 31.3.2 Drawing

Drawing with FPDF is also very simple. The two lines of the following listing are sufficient for a creating filled rectangle in the background (see Figure 31.7).

```
$pdf->SetFillColor(51, 0, 255);
$pdf->Rect(0, 0, 421, 70, "F");
```

## Listing 31.7 Drawing a Rectangle (Excerpt from "fpdf_draw.php")

It is also important here to set the fill color in the first step, which is used for the subsequent operations. In the second step, the rectangle is created with the coordinates, width, and height.

> **Note**
> You can find helpful examples and scripts for many other drawing-related tasks on the FPDF website at www.fpdf.org/en/script/index.php.

![](img/ae7820c36e8f24c1623d26668b28e80e_859_0.png)

## Figure 31.7 A Background Rectangle with FPDF

## 31.4 Conclusion

The generation of PDF documents can be very complex, because you need to draw the elements and objects manually. But the basics are easy and similar in different libraries. So it is a matter of taste which library you prefer. Out of the open source based libraries we mainly use TCPDF, because it is connected to HTML2PDF and this option makes it very easy to create output fast.

## PART VII

## Administration and Security

## Chapter 32

### Security

Nine out of ten websites (allegedly) have security vulnerabilities. This chapter helps you to avoid security gaps as much as possible.

A common opinion says that the biggest uncertainty factor for a web application is the operating system or the web server software (or the server-side technology). Unfortunately, this is wrong. Web servers and operating systems are maintained by their manufacturers, and security vulnerabilities are closed—sometimes faster, sometimes slower. New versions of server technologies, especially PHP, are also released regularly. For example, around four weeks after PHP 8.3.0, a bug-fixed version 8.3.1 was released, followed by PHP 8.3.2 around four weeks later. At the end of November 2024, new releases with security-related corrections were made for PHP versions from 8.1 to 8.3. It is definitely the duty of the administration team to stay on the ball and keep the system secure.

However, the main problem is neither the administrator nor the software provider. The problem usually lies with the development team behind the web application itself. The same mistakes are always made, and most of them could be avoided without much effort.

The topic of security with PHP could fill half a compendium, so we will only cover the most important points here. But rest assured: if you follow the advice in this chapter, your website will be much more secure and immune to most attacks. However, there is no such thing as a "completely secure website". Check your code constantly and analyze the log files of your web server to be informed about the attack methods of your enemies (or script kiddies).

First, it's worth visiting the webpage for the Open Web Application Security Project (OWASP). Behind this project is a group of volunteers who deal with the topic of web security. OWASP is known for its list of the top 10 security vulnerabilities on websites, published regularly (i.e., approximately every three to four years; see Figure 32.1).

You can view this list at https://owasp.org/Top10. The 2021 list (which is still the latest version as of the beginning of 2025, but plans for a successor later that year are already underway) contains the following items:

- 1. Insufficient access protection
- 2. Cryptographic errors
- 3. Injections and cross-site scripting (XSS)
- 4. Unsafe design
- 5. Insecure configuration
- 6. Use of obsolete or unsafe components
- 7. Insecure identification and authentication
- 8. Insufficient software and data integrity
- 9. Insufficient logging and monitoring
- 10. Server-Side Request Forgery (SSRF)

![](img/ae7820c36e8f24c1623d26668b28e80e_864_0.png)

## Figure 32.1 The Top 10 of OWASP

We turn to the more interesting points of this list ahead, but the list itself is already very informative. Almost all the points on the list relate primarily to sloppy programming. No matter how well a server has been secured by the administrator, it is possible to ruin the whole concept through sloppy programming. A server may be configured in such a way that outsiders have no rights. But what if an attacker takes over a website? A web application may have enough rights to misuse the server for sinister purposes. So, program carefully, expect the worst—and read on!

### 32.1 User Input

Almost all security vulnerabilities are related to the fact that information is transferred to the web application from outside, which massively disrupts it. This can be done in a
