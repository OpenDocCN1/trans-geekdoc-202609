
![upper V a r left-parenthesis bold x right-parenthesis equals double-struck upper E left-parenthesis left-parenthesis bold x minus double-struck upper E left-parenthesis bold x right-parenthesis right-parenthesis left-parenthesis bold x minus double-struck upper E left-parenthesis bold x right-parenthesis right-parenthesis Superscript down-tack Baseline right-parenthesis equals colon bold upper Sigma equals Start 3 By 3 Matrix 1st Row 1st Column sigma 11 2nd Column midline-horizontal-ellipsis 3rd Column sigma Subscript 1 p Baseline 2nd Row 1st Column vertical-ellipsis 2nd Column down-right-diagonal-ellipsis 3rd Column vertical-ellipsis 3rd Row 1st Column sigma Subscript p Baseline 1 Baseline 2nd Column midline-horizontal-ellipsis 3rd Column sigma Subscript p p Baseline EndMatrix equals colon left-parenthesis sigma Subscript i j Baseline right-parenthesis Subscript i comma j equals 1 comma ellipsis comma p Baseline comma](images/c01-math-0004.png)

<math display="block" overflow="scroll">
<mi mathvariant="normal">Var</mi>
<mo stretchy="false">(</mo>
<mi mathvariant="bold">x</mi>
<mo stretchy="false">)</mo>
<mo>=</mo>
<mi mathvariant="double-struck">E</mi>
<mfenced open="(" close=")" separators="">
<mrow>
<mo stretchy="false">(</mo>
<mi mathvariant="bold">x</mi>
<mo>&#8722;</mo>
<mi mathvariant="double-struck">E</mi>
<mo stretchy="false">(</mo>
<mi mathvariant="bold">x</mi>
<mo stretchy="false">)</mo>
<mo stretchy="false">)</mo>
<msup>
<mrow>
<mo stretchy="false">(</mo>
<mi mathvariant="bold">x</mi>
<mo>&#8722;</mo>
<mi mathvariant="double-struck">E</mi>
<mo stretchy="false">(</mo>
<mi mathvariant="bold">x</mi>
<mo stretchy="false">)</mo>
<mo stretchy="false">)</mo>
</mrow>
<mo>&#8868;</mo>
</msup>
</mrow>
</mfenced>
<mo>=</mo>
<mo>:</mo>
<mi mathvariant="bold">&#931;</mi>
<mo>=</mo>
<mfenced open="(" close=")" separators="">
<mrow>
<mtable>
<mtr>
<mtd class="array"><msub><mi>&#963;</mi><mn>11</mn></msub></mtd>
<mtd class="array"><mi>&#8943;</mi></mtd>
<mtd class="array"><msub><mi>&#963;</mi><mrow><mn>1</mn><mi>p</mi></mrow></msub></mtd>
</mtr>
<mtr>
<mtd class="array"><mo>&#8942;</mo></mtd>
<mtd class="array"><mo>&#8945;</mo></mtd>
<mtd class="array"><mo>&#8942;</mo></mtd>
</mtr>
<mtr>
<mtd class="array"><msub><mi>&#963;</mi><mrow><mi>p</mi><mn>1</mn></mrow></msub></mtd>
<mtd class="array"><mi>&#8943;</mi></mtd>
<mtd class="array"><msub><mi>&#963;</mi><mrow><mi>p</mi><mi>p</mi></mrow></msub></mtd>
</mtr>
</mtable>
</mrow>
</mfenced>
<mo>=</mo>
<mo>:</mo>
<msub>
<mrow>
<mo stretchy="false">(</mo>
<msub><mi>&#963;</mi><mrow><mi>i</mi><mi>j</mi></mrow></msub>
<mo stretchy="false">)</mo>
</mrow>
<mrow><mi>i</mi><mo>,</mo><mi>j</mi><mo>=</mo><mn>1</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>p</mi></mrow>
</msub>
<mo>,</mo>
</math>

or ![left-parenthesis sigma Subscript i j Baseline right-parenthesis](images/c01-i0029.png)

<math display="inline" overflow="scroll">
<mo stretchy="false">(</mo>
<msub><mi>&#963;</mi><mrow><mi>i</mi><mi>j</mi></mrow></msub>
<mo stretchy="false">)</mo>
</math>

in shortened form if there is no cause for ambiguity; the correlation matrix of ![bold x](images/c01-i0030.png)

<math display="inline" overflow="scroll">
<mrow><mi mathvariant="bold">x</mi></mrow>
</math>

is another symmetric and positive definite ![p times p](images/c01-i0031.png)

<math display="inline" overflow="scroll">
<mi>p</mi>
<mo>&#215;</mo>
<mi>p</mi>
</math>

matrix:

![Corr left-parenthesis bold x right-parenthesis equals colon bold-italic upper R equals Start 4 By 4 Matrix 1st Row 1st Column 1 2nd Column rho 12 3rd Column midline-horizontal-ellipsis 4th Column rho Subscript 1 p Baseline 2nd Row 1st Column rho 21 2nd Column 1 3rd Column midline-horizontal-ellipsis 4th Column vertical-ellipsis 3rd Row 1st Column vertical-ellipsis 2nd Column vertical-ellipsis 3rd Column down-right-diagonal-ellipsis 4th Column vertical-ellipsis 4th Row 1st Column rho Subscript p Baseline 1 Baseline 2nd Column midline-horizontal-ellipsis 3rd Column midline-horizontal-ellipsis 4th Column 1 EndMatrix equals colon left-parenthesis rho Subscript i j Baseline right-parenthesis Subscript i comma j equals 1 comma ellipsis comma p Baseline comma](images/c01-math-0005.png)

<math display="block" overflow="scroll">
<mtext>Corr</mtext>
<mo stretchy="false">(</mo>
<mi mathvariant="bold">x</mi>
<mo stretchy="false">)</mo>
<mo>=</mo>
<mo>:</mo>
<mi mathvariant="bold-italic">R</mi>
<mo>=</mo>
<mfenced open="(" close=")" separators="">
<mrow>
<mtable>
<mtr>
<mtd class="array"><mn>1</mn></mtd>
<mtd class="array"><msub><mi>&#961;</mi><mn>12</mn></msub></mtd>
<mtd class="array"><mi>&#8943;</mi></mtd>
<mtd class="array"><msub><mi>&#961;</mi><mrow><mn>1</mn><mi>p</mi></mrow></msub></mtd>
</mtr>
<mtr>
<mtd class="array"><msub><mi>&#961;</mi><mn>21</mn></msub></mtd>
<mtd class="array"><mn>1</mn></mtd>
<mtd class="array"><mi>&#8943;</mi></mtd>
<mtd class="array"><mo>&#8942;</mo></mtd>
</mtr>
<mtr>
<mtd class="array"><mo>&#8942;</mo></mtd>
<mtd class="array"><mo>&#8942;</mo></mtd>
<mtd class="array"><mo>&#8945;</mo></mtd>
<mtd class="array"><mo>&#8942;</mo></mtd>
</mtr>
<mtr>
<mtd class="array"><msub><mi>&#961;</mi><mrow><mi>p</mi><mn>1</mn></mrow></msub></mtd>
<mtd class="array"><mi>&#8943;</mi></mtd>
<mtd class="array"><mi>&#8943;</mi></mtd>
<mtd class="array"><mn>1</mn></mtd>
</mtr>
</mtable>
</mrow>
</mfenced>
<mo>=</mo>
<mo>:</mo>
<msub>
<mrow>
<mo stretchy="false">(</mo>
<msub><mi>&#961;</mi><mrow><mi>i</mi><mi>j</mi></mrow></msub>
<mo stretchy="false">)</mo>
</mrow>
<mrow><mi>i</mi><mo>,</mo><mi>j</mi><mo>=</mo><mn>1</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>p</mi></mrow>
</msub>
<mo>,</mo>
</math>

where ![rho Subscript i j Baseline colon equals StartFraction sigma Subscript i j Baseline Over StartRoot sigma Subscript i i Baseline EndRoot StartRoot sigma Subscript j j Baseline EndRoot EndFraction](images/c01-i0032.png)

<math display="inline" overflow="scroll">
<msub><mi>&#961;</mi><mrow><mi>i</mi><mi>j</mi></mrow></msub>
<mo>:</mo>
<mo>=</mo>
<mfrac>
<mrow><msub><mi>&#963;</mi><mrow><mi>i</mi><mi>j</mi></mrow></msub></mrow>
<mrow>
<msqrt><mrow><msub><mi>&#963;</mi><mrow><mi>i</mi><mi>i</mi></mrow></msub></mrow></msqrt>
<msqrt><mrow><msub><mi>&#963;</mi><mrow><mi>j</mi><mi>j</mi></mrow></msub></mrow></msqrt>
</mrow>
</mfrac>
</math>

is the correlation coefficient between ![normal x Subscript i](images/c01-i0033.png)

<math display="inline" overflow="scroll">
<msub><mi mathvariant="normal">x</mi><mi>i</mi></msub>
</math>

and ![normal x Subscript j](images/c01-i0034.png)

<math display="inline" overflow="scroll">
<msub><mi mathvariant="normal">x</mi><mi>j</mi></msub>
</math>

. The following are some important properties that we shall use later:
