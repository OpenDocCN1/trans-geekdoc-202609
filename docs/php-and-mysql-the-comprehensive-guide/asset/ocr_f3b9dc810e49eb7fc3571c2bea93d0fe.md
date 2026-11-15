```
$start = $end;
}

$pdf->Output('output.pdf', 'I');
```

# Listing 31.4 A Pie Chart in PDF ("tcpdf_draw_diagram.php")

![](bbox=[0.143, 0.215, 0.855, 0.625])

Figure 31.4 A Pie Chart

# 31.2.5 Write HTML

The strength of TCPDF in dealing with HTML, which you saw in the last section, is also the reason that HTML2PDF uses this PDF library as a basis.

TCPDF itself has methods for writing HTML. However, HTML2PDF is even more convenient and functionally comprehensive. To do this, simply import the HTML2PDF library and instantiate an object of the Html2Pdf class:

```
require __DIR__.'./vendor/autoload.php';
use Spipu\Html2Pdf\Html2Pdf;
$html2pdf = new Html2Pdf();
```