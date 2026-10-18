
[(11.6)](#c11.xhtml#R_c11-disp-0011)

![d left-parenthesis bold-italic x right-parenthesis equals double-vertical-bar proj Subscript bold-italic omega Baseline left-parenthesis bold-italic x 0 minus bold-italic x right-parenthesis double-vertical-bar Subscript 2 Baseline equals double-vertical-bar StartFraction bold-italic x 0 Superscript down-tack Baseline bold-italic omega minus bold-italic x Superscript down-tack Baseline bold-italic omega Over double-vertical-bar bold-italic omega double-vertical-bar Subscript 2 Superscript 2 Baseline EndFraction bold-italic omega double-vertical-bar Subscript 2 Baseline equals StartFraction StartAbsoluteValue bold-italic x Superscript down-tack Baseline bold-italic omega plus b EndAbsoluteValue Over double-vertical-bar bold-italic omega double-vertical-bar Subscript 2 Baseline EndFraction period](images/c11-math-0011.png)

<math display="block" overflow="scroll">
<mi>d</mi><mo stretchy="false">(</mo><mi mathvariant="bold-italic">x</mi><mo stretchy="false">)</mo><mo>=</mo><mo stretchy="false">&#8214;</mo><msub><mtext>proj</mtext><mi mathvariant="bold-italic">&#969;</mi></msub><mo stretchy="false">(</mo><msub><mi mathvariant="bold-italic">x</mi><mn>0</mn></msub><mo>&#8722;</mo><mi mathvariant="bold-italic">x</mi><mo stretchy="false">)</mo><msub><mo stretchy="false">&#8214;</mo><mn>2</mn></msub><mo>=</mo><msub><mrow><mfenced open="&#8214;" close="&#8214;" separators=""><mrow><mfrac><mrow><msubsup><mi mathvariant="bold-italic">x</mi><mn>0</mn><mo>&#8868;</mo></msubsup><mi mathvariant="bold-italic">&#969;</mi><mo>&#8722;</mo><msup><mi mathvariant="bold-italic">x</mi><mo>&#8868;</mo></msup><mi mathvariant="bold-italic">&#969;</mi></mrow><mrow><mo stretchy="false">&#8214;</mo><mi mathvariant="bold-italic">&#969;</mi><msubsup><mo stretchy="false">&#8214;</mo><mn>2</mn><mn>2</mn></msubsup></mrow></mfrac><mi mathvariant="bold-italic">&#969;</mi></mrow></mfenced></mrow><mrow><mn>2</mn></mrow></msub><mo>=</mo><mfrac><mrow><mo stretchy="false">&#124;</mo><msup><mi mathvariant="bold-italic">x</mi><mo>&#8868;</mo></msup><mi mathvariant="bold-italic">&#969;</mi><mo>+</mo><mi>b</mi><mo stretchy="false">&#124;</mo></mrow><mrow><mo stretchy="false">&#8214;</mo><mi mathvariant="bold-italic">&#969;</mi><msub><mo stretchy="false">&#8214;</mo><mn>2</mn></msub></mrow></mfrac><mo>.</mo>
</math>

If `x` is correctly classified by the plane, ([11.6](#c11.xhtml#c11-disp-0011)) can be further written as

![d left-parenthesis bold-italic x right-parenthesis equals StartFraction StartAbsoluteValue bold-italic x Superscript down-tack Baseline bold-italic omega plus b EndAbsoluteValue Over double-vertical-bar bold-italic omega double-vertical-bar Subscript 2 Baseline EndFraction equals y dot StartFraction bold-italic x Superscript down-tack Baseline bold-italic omega plus b Over double-vertical-bar bold-italic omega double-vertical-bar Subscript 2 Baseline EndFraction comma](images/c11-math-0012.png)

<math display="block" overflow="scroll">
<mi>d</mi><mo stretchy="false">(</mo><mi mathvariant="bold-italic">x</mi><mo stretchy="false">)</mo><mo>=</mo><mfrac><mrow><mo stretchy="false">&#124;</mo><msup><mi mathvariant="bold-italic">x</mi><mo>&#8868;</mo></msup><mi mathvariant="bold-italic">&#969;</mi><mo>+</mo><mi>b</mi><mo stretchy="false">&#124;</mo></mrow><mrow><mo stretchy="false">&#8214;</mo><mi mathvariant="bold-italic">&#969;</mi><msub><mo stretchy="false">&#8214;</mo><mn>2</mn></msub></mrow></mfrac><mo>=</mo><mi>y</mi><mo>&#183;</mo><mfrac><mrow><msup><mi mathvariant="bold-italic">x</mi><mo>&#8868;</mo></msup><mi mathvariant="bold-italic">&#969;</mi><mo>+</mo><mi>b</mi></mrow><mrow><mo stretchy="false">&#8214;</mo><mi mathvariant="bold-italic">&#969;</mi><msub><mo stretchy="false">&#8214;</mo><mn>2</mn></msub></mrow></mfrac><mo>,</mo>
</math>

where `y ∈ {-1, 1}` is the actual label of `x`. Now, for a given dataset `{(x_i, y_i)}_{i=1}^n`, define

![gamma Subscript i Baseline colon equals StartLayout Enlarged left-brace 1st Row 1st Column d left-parenthesis bold-italic x Subscript i Baseline right-parenthesis comma 2nd Column if bold-italic x Subscript i Baseline is correctly classified semicolon 2nd Row 1st Column minus d left-parenthesis bold-italic x Subscript i Baseline right-parenthesis comma 2nd Column if bold-italic x Subscript i Baseline is misclassified period EndLayout](images/c11-math-0013.png)

<math display="block" overflow="scroll">
<msub><mi>&#947;</mi><mi>i</mi></msub><mo>:</mo><mo>=</mo><mfenced open="{" close="" separators=""><mrow><mtable><mtr><mtd columnalign="left"><mi>d</mi><mo stretchy="false">(</mo><msub><mi mathvariant="bold-italic">x</mi><mi>i</mi></msub><mo stretchy="false">)</mo><mo>,</mo><mspace width="1em"/></mtd><mtd columnalign="left"><mtext>if </mtext><mspace width="0.15em"/><msub><mi mathvariant="bold-italic">x</mi><mi>i</mi></msub><mtext> is correctly classified;</mtext></mtd></mtr><mtr><mtd columnalign="left"><mo>&#8722;</mo><mi>d</mi><mo stretchy="false">(</mo><msub><mi mathvariant="bold-italic">x</mi><mi>i</mi></msub><mo stretchy="false">)</mo><mo>,</mo><mspace width="1em"/></mtd><mtd columnalign="left"><mtext>if </mtext><mspace width="0.15em"/><msub><mi mathvariant="bold-italic">x</mi><mi>i</mi></msub><mtext> is misclassified.</mtext></mtd></mtr></mtable></mrow></mfenced>
</math>

The *geometric margin* is then defined by

![gamma colon equals min Underscript i equals 1 comma ellipsis comma n Endscripts gamma Subscript i Baseline period](images/c11-math-0014.png)

<math display="block" overflow="scroll">
<mi>&#947;</mi><mo>:</mo><mo>=</mo><munder><mi mathvariant="normal">min</mi><mrow><mi>i</mi><mo>=</mo><mn>1</mn><mo>,</mo><mo>&#8230;</mo><mo>,</mo><mi>n</mi></mrow></munder><msub><mi>&#947;</mi><mi>i</mi></msub><mo>.</mo>
</math>

Suppose that the dataset is linearly separable, then there exists `(ω, b)` such that all the data are correctly classified by the hyperplane `x⊥ω + b = 0`. Our goal is to look for `(ω, b)` such that this separating hyperplane is as far as possible from the two groups of points. In other words, we aim to find the optimal hyperplane that solves the following optimization problem:
