Finally, output the whole thing using the `Output()` method. Listing 31.6 shows the complete example, and you can see its output in Figure 31.6.

```
<?php
define("FPDF_FONTPATH", "font/");
require "fpdf/fpdf.php";

$pdf=new FPDF("P", "pt", "A5");
$pdf->AddPage();
$pdf->SetFont("Helvetica", "", 48);
$pdf->Cell(20,10, "Your statement!");
$datn = $pdf->Output();
header("Content-type: application/pdf");
header("Content-disposition:inline;filename=output.pdf");
print $datn;
?>
```

# Listing 31.6 A First Document with FPDF ("fpdf_basics.php")

![](bbox=[0.14, 0.425, 0.86, 0.675])

# Figure 31.6 The First Document

> **Note**
> 
> FPDF has some special features. For example, as with most graphics programs, the origin is in the top-left-hand corner by default. You can also select the unit very flexibly.

# 31.3.2 Drawing

Drawing with FPDF is also very simple. The two lines of the following listing are sufficient for a creating filled rectangle in the background (see Figure 31.7).