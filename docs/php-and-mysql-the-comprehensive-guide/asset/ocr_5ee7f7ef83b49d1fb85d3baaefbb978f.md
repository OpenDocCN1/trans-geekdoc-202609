+   Alignment controls the text alignment within the cell with the values L for left (default), C for centered, and R for right-aligned.

+   Filling specifies whether there is a filling (value 1) or not (default value 0).
+   
+   You control the fill color itself using SetFillColor(). The method expects the RGB color values as parameters. The following example creates a blue fill, for example:
+   
+   $pdf->SetFillColor(0, 0, 255);

+   Link optionally contains a URL for a link.

+   Scaling controls how the text in the cell is scaled horizontally. By default, scaling is deactivated (default value 0). The parameter therefore also controls the spacing between the letters. The value 2, for example, scales the letters to the entire cell width by default.

> **Note**
> 
> The MultiCell() method also creates a cell, but with dynamic text wrapping. You can see this method in action in Section 31.2.4.

The following example creates a cell with a blue background and a large text; Figure 31.2 shows the output.

```
require __DIR__ . '/vendor/autoload.php';
use Com\Tecnick\Pdf;

$pdf = new TCPDF('P', 'mm', 'A4', true, 'UTF-8', false);

$pdf->SetTitle('TCPDF Output');

$pdf->setPrintHeader(false);
$pdf->setPrintFooter(false);

$pdf->SetMargins(0, 0, 0);
$pdf->SetAutoPageBreak(true, 0);

$pdf->SetFont('Helvetica', '', 48);
$pdf->AddPage();

$output = 'Your statement!';

$pdf->SetFillColor(0, 0, 255);
$pdf->Cell(0, 50, $output, 1, 0, 'C', 1, '', 0);

$pdf->Output('output.pdf', 'I');
```

# Listing 31.2 A Simple Text Box ("tcpdf_draw.php")