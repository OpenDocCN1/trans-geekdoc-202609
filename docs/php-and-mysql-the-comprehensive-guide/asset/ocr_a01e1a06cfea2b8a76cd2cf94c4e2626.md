```
require __DIR__ . '/vendor/autoload.php';
use Com\Tecnick\Pdf;

$pdf = new TCPDF('P', 'mm', 'A4', true, 'UTF-8', false);

$pdf->SetTitle('TCPDF Tart');

$pdf->setPrintHeader(false);
$pdf->setPrintFooter(false);

$pdf->SetMargins(0, 0, 0);
$pdf->SetAutoPageBreak(true, 0);

$pdf->AddPage();

//Title
$output = 'Who should be kicked out?';
$pdf->SetFillColor(100, 100, 255);
$pdf->SetFont('Helvetica', '', 36);
$pdf->Cell(0, 50, $output, 1, 0, 'C', 1);
$pdf->LN();

//Legend
$pdf->SetFont('Helvetica', '', 12);
$pdf->MultiCell(100, 8, 'Legend:', 0, 'L', 0, 1, 5, 55);

//start angle
$start = 0;
foreach ($sim->answer as $answer) {
    $r_random = mt_rand(50, 220);
    $g_random = mt_rand(50, 220);
    $b_random = mt_rand(50, 220);
    $pdf->SetFillColor($r_random, $g_random, $b_random);
    $pdf->SetLineStyle(['width' => 1, 'color' => [100, 100, 100],
    'join' => 'bevel']);
    $end = $start + 360 * intval($answer) / $ans_max;
    $pdf->PieSector($pdf->getPageWidth() / 2, 140,
    $pdf->getPageWidth() / 3, $start, $end);
    //Label answers:
    $pdf->SetTextColor($r_random, $g_random, $b_random);
    $pdf->MultiCell(100, 5,
    $answer["text"] . ": " . $answer, 0, 'L', 0, 1, 5);
}

//Increment
```