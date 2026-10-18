

[(12.2)](#c12.xhtml#R_c12-disp-0003)

![ModifyingAbove t left-parenthesis bold x right-parenthesis With Ì‚ colon equals double-struck upper E left-parenthesis mu left-parenthesis normal upper Theta right-parenthesis bar bold x right-parenthesis equals arg min Underscript t left-parenthesis dot right-parenthesis Endscripts upper R left-parenthesis t left-parenthesis bold x right-parenthesis right-parenthesis comma](images/c12-math-0003.png)

<math display="block" overflow="scroll">
<mover accent="true">
<mrow><mi>t</mi><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo></mrow>
<mo>&#770;</mo>
</mover>
<mo>:</mo><mo>=</mo><mi mathvariant="double-struck">E</mi>
<mfenced open="(" close=")" separators="">
<mrow><mi>&#956;</mi><mo stretchy="false">(</mo><mi mathvariant="normal">&#920;</mi><mo stretchy="false">)</mo><mo>&#8739;</mo><mi mathvariant="bold">x</mi></mrow>
</mfenced>
<mo>=</mo>
<munder><mtext>arg&#8201;min&#8201;</mtext><mrow><mi>t</mi><mo stretchy="false">(</mo><mo>&#183;</mo><mo stretchy="false">)</mo></mrow></munder>
<mi>R</mi><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><mo stretchy="false">)</mo><mo>,</mo>
</math>

which is also known as the `Bayesian premium`.

Next we illustrate the calculation of the Bayesian premium via a simple example. Suppose that ![normal x Subscript i Baseline bar normal upper Theta equals theta tilde Overscript i i d Endscripts script upper N left-parenthesis theta comma sigma squared right-parenthesis](images/c12-i0027.png)

<math display="inline" overflow="scroll">
<msub><mi mathvariant="normal">x</mi><mi>i</mi></msub><mo>&#8739;</mo><mi mathvariant="normal">&#920;</mi><mo>=</mo><mi>&#952;</mi>
<mover class="overset"><mo>&#8764;</mo><mrow><mi>i</mi><mi>i</mi><mi>d</mi></mrow></mover>
<mi mathvariant="script">N</mi>
<mfenced open="(" close=")" separators=""><mrow><mi>&#952;</mi><mo>,</mo><msup><mi>&#963;</mi><mn>2</mn></msup></mrow></mfenced>
</math>

for ![i equals 1 comma 2 comma ellipsis](images/c12-i0028.png)

<math display="inline" overflow="scroll"><mi>i</mi><mo>=</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mo>&#8230;</mo></math>

, and the prior distribution of ![normal upper Theta](images/c12-i0029.png)

<math display="inline" overflow="scroll"><mrow><mi mathvariant="normal">&#920;</mi></mrow></math>

is ![script upper N left-parenthesis mu comma tau squared right-parenthesis](images/c12-i0030.png)

<math display="inline" overflow="scroll"><mi mathvariant="script">N</mi><mfenced open="(" close=")" separators=""><mrow><mi>&#956;</mi><mo>,</mo><msup><mi>&#964;</mi><mn>2</mn></msup></mrow></mfenced></math>

, where ![sigma squared](images/c12-i0031.png)

<math display="inline" overflow="scroll"><msup><mi>&#963;</mi><mn>2</mn></msup></math>

, ![mu](images/c12-i0032.png)

<math display="inline" overflow="scroll"><mrow><mi>&#956;</mi></mrow></math>

and ![tau squared](images/c12-i0033.png)

<math display="inline" overflow="scroll"><msup><mi>&#964;</mi><mn>2</mn></msup></math>

are known constants. To determine the Bayesian premium for the ![left-parenthesis n plus 1 right-parenthesis](images/c12-i0034.png)

<math display="inline" overflow="scroll"><mo stretchy="false">(</mo><mi>n</mi><mo>+</mo><mn>1</mn><mo stretchy="false">)</mo></math>

‐th period based on the historical losses ![bold x equals left-parenthesis normal x 1 comma ellipsis comma normal x Subscript n Baseline right-parenthesis Superscript down-tack](images/c12-i0035.png)

<math display="inline" overflow="scroll">
<mi mathvariant="bold">x</mi><mo>=</mo>
<msup>
<mrow><mfenced open="(" close=")" separators=""><mrow><msub><mi mathvariant="normal">x</mi><mn>1</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi mathvariant="normal">x</mi><mi>n</mi></msub></mrow></mfenced></mrow>
<mo>&#8868;</mo>
</msup>
</math>

, we need to derive the posterior distribution of ![normal upper Theta](images/c12-i0036.png)

<math display="inline" overflow="scroll"><mrow><mi mathvariant="normal">&#920;</mi></mrow></math>

given ![bold x](images/c12-i0037.png)

<math display="inline" overflow="scroll"><mrow><mi mathvariant="bold">x</mi></mrow></math>

. By precisely the same derivations as in [第 1.5 节](#c01.xhtml#c01-sec-0015), we have:

![normal upper Theta bar bold x equals bold-italic x tilde script upper N left-parenthesis mu Subscript n Baseline comma beta Subscript n Superscript negative 1 Baseline right-parenthesis comma](images/c12-math-0004.png)

<math display="block" overflow="scroll">
<mi mathvariant="normal">&#920;</mi><mo>&#8739;</mo><mi mathvariant="bold">x</mi><mo>=</mo><mi mathvariant="bold-italic">x</mi><mo>&#8764;</mo><mi mathvariant="script">N</mi>
<mfenced open="(" close=")" separators=""><mrow><msub><mi>&#956;</mi><mi>n</mi></msub><mo>,</mo><msubsup><mi>&#946;</mi><mi>n</mi><mrow><mo>&#8722;</mo><mn>1</mn></mrow></msubsup></mrow></mfenced><mtext>,</mtext>
</math>

where ![mu Subscript n Baseline equals StartStartFraction StartFraction 1 Over sigma squared EndFraction sigma-summation Underscript i equals 1 Overscript n Endscripts x Subscript i Baseline plus StartFraction 1 Over tau squared EndFraction mu OverOver StartFraction n Over sigma squared EndFraction plus StartFraction 1 Over tau squared EndFraction EndEndFraction equals StartFraction n tau squared x overbar plus sigma squared mu Over n tau squared plus sigma squared EndFraction](images/c12-i0038.png)

<math display="inline" overflow="scroll">
<msub><mi>&#956;</mi><mi>n</mi></msub><mo>=</mo>
<mfrac>
<mrow>
<mfrac><mn>1</mn><mrow><msup><mi>&#963;</mi><mn>2</mn></msup></mrow></mfrac>
<msubsup><mrow><mo>&#8721;</mo></mrow><mrow><mi>i</mi><mo>&#8201;=&#8201;</mo><mn>1</mn></mrow><mrow><mi>n</mi></mrow></msubsup><msub><mi>x</mi><mi>i</mi></msub><mo>&#8201;+&#8201;</mo>
<mfrac><mn>1</mn><mrow><msup><mi>&#964;</mi><mn>2</mn></msup></mrow></mfrac><mi>&#956;</mi>
</mrow>
<mrow>
<mfrac><mi>n</mi><mrow><msup><mi>&#963;</mi><mn>2</mn></msup></mrow></mfrac><mo>+</mo>
<mfrac><mn>1</mn><mrow><msup><mi>&#964;</mi><mn>2</mn></msup></mrow></mfrac>
</mrow>
</mfrac>
<mo>=</mo>
<mfrac>
<mrow><mi>n</mi><msup><mi>&#964;</mi><mn>2</mn></msup><mover accent="true"><mi>x</mi><mo>&#175;</mo></mover><mo>&#8201;+&#8201;</mo><msup><mi>&#963;</mi><mn>2</mn></msup><mi>&#956;</mi></mrow>
<mrow><mi>n</mi><msup><mi>&#964;</mi><mn>2</mn></msup><mo>&#8201;+&#8201;</mo><msup><mi>&#963;</mi><mn>2</mn></msup></mrow>
</mfrac>
</math>

and ![beta Subscript n Baseline equals StartFraction n Over sigma squared EndFraction plus StartFraction 1 Over tau squared EndFraction](images/c12-i0039.png)

<math display="inline" overflow="scroll">
<msub><mi>&#946;</mi><mi>n</mi></msub><mo>=</mo>
<mfrac><mi>n</mi><mrow><msup><mi>&#963;</mi><mn>2</mn></msup></mrow></mfrac><mo>+</mo><mfrac><mn>1</mn><mrow><msup><mi>&#964;</mi><mn>2</mn></msup></mrow></mfrac>
</math>

. Therefore, together with the fact that ![mu left-parenthesis theta right-parenthesis equals double-struck upper E left-parenthesis bold x bar normal upper Theta equals theta right-parenthesis equals theta](images/c12-i0040.png)

<math display="inline" overflow="scroll">
<mi>&#956;</mi><mo stretchy="false">(</mo><mi>&#952;</mi><mo stretchy="false">)</mo><mo>=</mo>
<mi mathvariant="double-struck">E</mi><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo>&#8739;</mo><mi mathvariant="normal">&#920;</mi><mo>=</mo><mi>&#952;</mi><mo stretchy="false">)</mo><mo>=</mo><mi>&#952;</mi>
</math>

, the Bayesian premium is simply equal to:

