

[(6.11)](#c06.xhtml#R_c06-disp-0016)

![StartLayout 1st Row 1st Column p Subscript m i Superscript left-parenthesis t right-parenthesis 2nd Column equals double-struck upper P left-parenthesis the m hyphen th parameter vector is used bar bold-italic x Subscript i Baseline is realized right-parenthesis 2nd Row 1st Column Blank 2nd Column equals StartFraction pi Subscript m Superscript left-parenthesis t right-parenthesis Baseline f left-parenthesis bold-italic x Subscript i Baseline vertical-bar bold z equals bold-italic mu Subscript m Superscript left-parenthesis t right-parenthesis Baseline semicolon bold-italic theta Superscript left-parenthesis t right-parenthesis Baseline right-parenthesis Over sigma-summation Underscript r equals 1 Overscript upper M Endscripts pi Subscript r Superscript left-parenthesis t right-parenthesis Baseline f left-parenthesis bold-italic x Subscript i Baseline vertical-bar bold z equals bold-italic mu Subscript r Superscript left-parenthesis t right-parenthesis Baseline semicolon bold-italic theta Superscript left-parenthesis t right-parenthesis Baseline right-parenthesis EndFraction comma i equals 1 comma ellipsis comma n comma and m equals 1 comma ellipsis comma upper M period EndLayout](images/c06-math-0016.png)

<math display="block" overflow="scroll">
<mtable>
<mtr>
<mtd columnalign="right">
<msubsup><mi>p</mi><mrow><mi>m</mi><mi>i</mi></mrow><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msubsup>
</mtd>
<mtd columnalign="left">
<mo>=</mo><mi mathvariant="double-struck">P</mi><mo stretchy="false">(</mo><mtext>the</mtext><mspace width="0.15em"/><mi>m</mi><mtext>-th parameter vector is used</mtext><mo>&#8739;</mo><mspace width="0.15em"/><msub><mi mathvariant="bold-italic">x</mi><mi>i</mi></msub><mtext> is realized</mtext><mo stretchy="false">)</mo>
</mtd>
</mtr>
<mtr>
<mtd columnalign="right"/>
<mtd columnalign="left">
<mo>=</mo>
<mfrac>
<mrow>
<msubsup><mi>&#960;</mi><mi>m</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msubsup>
<mi>f</mi>
<mo stretchy="false">(</mo>
<msub><mi mathvariant="bold-italic">x</mi><mi>i</mi></msub>
<mo stretchy="false">&#124;</mo>
<mi mathvariant="bold">z</mi>
<mo>=</mo>
<msubsup><mi mathvariant="bold-italic">&#956;</mi><mi>m</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msubsup>
<mo>;</mo>
<msup><mi mathvariant="bold-italic">&#952;</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msup>
<mo stretchy="false">)</mo>
</mrow>
<mrow>
<msubsup><mo>&#8721;</mo><mrow><mi>r</mi><mo>=</mo><mn>1</mn></mrow><mi>M</mi></msubsup>
<msubsup><mi>&#960;</mi><mi>r</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msubsup>
<mi>f</mi>
<mo stretchy="false">(</mo>
<msub><mi mathvariant="bold-italic">x</mi><mi>i</mi></msub>
<mo stretchy="false">&#124;</mo>
<mi mathvariant="bold">z</mi>
<mo>=</mo>
<msubsup><mi mathvariant="bold-italic">&#956;</mi><mi>r</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msubsup>
<mo>;</mo>
<msup><mi mathvariant="bold-italic">&#952;</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msup>
<mo stretchy="false">)</mo>
</mrow>
</mfrac>
<mo>,</mo>
<mspace width="1em"/>
<mi>i</mi>
<mo>=</mo>
<mn>1</mn>
<mo>,</mo>
<mo>&#8230;</mo>
<mo>,</mo>
<mi>n</mi>
<mo>,</mo>
<mspace width="0.2em"/>
<mtext>and</mtext>
<mspace width="0.2em"/>
<mi>m</mi>
<mo>=</mo>
<mn>1</mn>
<mo>,</mo>
<mo>&#8230;</mo>
<mo>,</mo>
<mi>M</mi>
<mo>.</mo>
</mtd>
</mtr>
</mtable>
</math>

基于这些计算出的后验概率，我们接着计算期望对数似然 (6.2)（注意，某些积分被近似替换为求和，以对应离散形式）：

[(6.12)](#c06.xhtml#R_c06-disp-0017)

![StartLayout 1st Row 1st Column Blank 2nd Column upper Q left-parenthesis bold-italic theta bar bold-italic theta Superscript left-parenthesis t right-parenthesis Baseline right-parenthesis 2nd Row 1st Column Blank 2nd Column equals sigma-summation Underscript m equals 1 Overscript upper M Endscripts sigma-summation Underscript i equals 1 Overscript n Endscripts p Subscript m i Superscript left-parenthesis t right-parenthesis Baseline ln left-parenthesis pi Subscript m Baseline f left-parenthesis bold-italic x Subscript i Baseline vertical-bar bold z equals bold-italic mu Subscript m Baseline semicolon bold-italic theta right-parenthesis right-parenthesis 3rd Row 1st Column Blank 2nd Column equals sigma-summation Underscript m equals 1 Overscript upper M Endscripts sigma-summation Underscript i equals 1 Overscript n Endscripts p Subscript m i Superscript left-parenthesis t right-parenthesis Baseline left-brace ln pi Subscript m Baseline plus sigma-summation Underscript k equals 1 Overscript upper K Endscripts left-parenthesis x Subscript i k Baseline ln mu Subscript m k Baseline plus left-parenthesis 1 minus x Subscript i k Baseline right-parenthesis ln left-parenthesis 1 minus mu Subscript m k Baseline right-parenthesis right-parenthesis right-brace period EndLayout](images/c06-math-0017.png)

<math display="block" overflow="scroll">
<mtable>
<mtr>
<mtd columnalign="right"/>
<mtd columnalign="left">
<mi>Q</mi>
<mo stretchy="false">(</mo>
<mi mathvariant="bold-italic">&#952;</mi>
<mo>&#8739;</mo>
<msup><mi mathvariant="bold-italic">&#952;</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msup>
<mo stretchy="false">)</mo>
</mtd>
</mtr>
<mtr>
<mtd columnalign="right"/>
<mtd columnalign="left">
<mspace width="1em"/>
<mo>=</mo>
<munderover><mo stretchy="false" movablelimits="false">&#8721;</mo><mrow><mi>m</mi><mo>=</mo><mn>1</mn></mrow><mi>M</mi></munderover>
<munderover><mo stretchy="false" movablelimits="false">&#8721;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover>
<msubsup><mi>p</mi><mrow><mi>m</mi><mi>i</mi></mrow><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msubsup>
<mi mathvariant="normal">ln</mi>
<mfenced open="(" close=")" separators="">
<mrow>
<msub><mi>&#960;</mi><mi>m</mi></msub>
<mi>f</mi>
<mo stretchy="false">(</mo>
<msub><mi mathvariant="bold-italic">x</mi><mi>i</mi></msub>
<mo stretchy="false">&#124;</mo>
<mi mathvariant="bold">z</mi>
<mo>=</mo>
<msub><mi mathvariant="bold-italic">&#956;</mi><mi>m</mi></msub>
<mo>;</mo>
<mi mathvariant="bold-italic">&#952;</mi>
<mo stretchy="false">)</mo>
</mrow>
</mfenced>
</mtd>
</mtr>
<mtr>
<mtd columnalign="right"/>
<mtd columnalign="left">
<mspace width="1em"/>
<mo>=</mo>
<munderover><mo stretchy="false" movablelimits="false">&#8721;</mo><mrow><mi>m</mi><mo>=</mo><mn>1</mn></mrow><mi>M</mi></munderover>
<munderover><mo stretchy="false" movablelimits="false">&#8721;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover>
<msubsup><mi>p</mi><mrow><mi>m</mi><mi>i</mi></mrow><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msubsup>
<mfenced open="{" close="}" separators="">
<mrow>
<mi mathvariant="normal">ln</mi>
<msub><mi>&#960;</mi><mi>m</mi></msub>
<mo>+</mo>
<munderover><mo stretchy="false" movablelimits="false">&#8721;</mo><mrow><mi>k</mi><mo>=</mo><mn>1</mn></mrow><mi>K</mi></munderover>
<mfenced open="(" close=")" separators="">
<mrow>
<msub><mi>x</mi><mrow><mi>i</mi><mi>k</mi></mrow></msub>
<mi mathvariant="normal">ln</mi>
<msub><mi>&#956;</mi><mrow><mi>m</mi><mi>k</mi></mrow></msub>
<mo>+</mo>
<mo stretchy="false">(</mo>
<mn>1</mn>
<mo>&#8722;</mo>
<msub><mi>x</mi><mrow><mi>i</mi><mi>k</mi></mrow></msub>
<mo stretchy="false">)</mo>
<mi mathvariant="normal">ln</mi>
<mo stretchy="false">(</mo>
<mn>1</mn>
<mo>&#8722;</mo>
<msub><mi>&#956;</mi><mrow><mi>m</mi><mi>k</mi></mrow></msub>
<mo stretchy="false">)</mo>
</mrow>
</mfenced>
</mrow>
</mfenced>
<mo>.</mo>
</mtd>
</mtr>
</mtable>
</math>

