

[(11.2)](#c11.xhtml#R_c11-disp-0004)

![upper L left-parenthesis bold-italic omega right-parenthesis equals minus sigma-summation Underscript i element-of upper I Subscript n Baseline Endscripts y Subscript i Baseline bold-italic omega Superscript down-tack Baseline bold-italic x Subscript i Baseline equals sigma-summation Underscript i equals 1 Overscript n Endscripts max left-parenthesis 0 comma minus y Subscript i Baseline bold-italic omega Superscript down-tack Baseline bold-italic x Subscript i Baseline right-parenthesis comma](images/c11-math-0004.png)

<math display="block" overflow="scroll">
<mi>L</mi><mo stretchy="false">(</mo><mi mathvariant="bold-italic">&#969;</mi><mo stretchy="false">)</mo><mo>=</mo><mo>&#8722;</mo><munder><mo>&#8721;</mo><mrow><mi>i</mi><mo>&#8712;</mo><msub><mi>I</mi><mi>n</mi></msub></mrow></munder><msub><mi>y</mi><mi>i</mi></msub><msup><mi mathvariant="bold-italic">&#969;</mi><mo>&#8868;</mo></msup><msub><mi mathvariant="bold-italic">x</mi><mi>i</mi></msub><mo>=</mo><munderover><mrow><mo stretchy="false" movablelimits="false">&#8721;</mo></mrow><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mrow><mi>n</mi></mrow></munderover><mi mathvariant="normal">max</mi><mo stretchy="false">(</mo><mn>0</mn><mo>,</mo><mo>&#8722;</mo><msub><mi>y</mi><mi>i</mi></msub><msup><mi mathvariant="bold-italic">&#969;</mi><mo>&#8868;</mo></msup><msub><mi mathvariant="bold-italic">x</mi><mi>i</mi></msub><mo stretchy="false">)</mo><mo>,</mo>
</math>

and our goal now is to find the parameter ![bold-italic omega equals left-parenthesis omega 0 comma omega 1 comma ellipsis comma omega Subscript p Baseline right-parenthesis Superscript down-tack](images/c11-i0062.png)

<math display="inline" overflow="scroll">
<mi mathvariant="bold-italic">&#969;</mi><mo>=</mo><msup><mrow><mo stretchy="false">(</mo><msub><mi>&#969;</mi><mn>0</mn></msub><mo>,</mo><msub><mi>&#969;</mi><mn>1</mn></msub><mo>,</mo><mo>&#8230;</mo><mo>,</mo><msub><mi>&#969;</mi><mi>p</mi></msub><mo stretchy="false">)</mo></mrow><mo>&#8868;</mo></msup>
</math>

, that minimizes the loss function ![upper L](images/c11-i0063.png)

<math display="inline" overflow="scroll">
<mrow><mi>L</mi></mrow>
</math>

. One of the difficulties involved in this optimization problem is the implicit dependence of ![upper L](images/c11-i0064.png)

<math display="inline" overflow="scroll">
<mrow><mi>L</mi></mrow>
</math>

on the parameter ![bold-italic omega](images/c11-i0065.png)

<math display="inline" overflow="scroll">
<mrow><mi mathvariant="bold-italic">&#969;</mi></mrow>
</math>

through the index set ![upper I Subscript n](images/c11-i0066.png)

<math display="inline" overflow="scroll">
<msub><mi>I</mi><mi>n</mi></msub>
</math>

. We shall employ the `gradient descent` method, which can effectively refine the parameter values iteratively; also see Appendix `11.A.1` for an overview of the gradient descent method.

To this end, we first initialize ![bold-italic omega Superscript left-parenthesis 0 right-parenthesis](images/c11-i0067.png)

<math display="inline" overflow="scroll">
<msup><mi mathvariant="bold-italic">&#969;</mi><mrow><mo stretchy="false">(</mo><mn>0</mn><mo stretchy="false">)</mo></mrow></msup>
</math>

, and then a sequence of estimates ![left-brace bold-italic omega Superscript left-parenthesis t right-parenthesis Baseline right-brace Subscript t equals 1 Superscript infinity](images/c11-i0068.png)

<math display="inline" overflow="scroll">
<msubsup><mrow><mo stretchy="false">&#123;</mo><msup><mi mathvariant="bold-italic">&#969;</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msup><mo stretchy="false">&#125;</mo></mrow><mrow><mi>t</mi><mo>=</mo><mn>1</mn></mrow><mrow><mi>&#8734;</mi></mrow></msubsup>
</math>

is constructed as follows. For ![t element-of double-struck upper N](images/c11-i0069.png)

<math display="inline" overflow="scroll">
<mi>t</mi><mo>&#8712;</mo><mi mathvariant="double-struck">N</mi>
</math>

, we define ![upper I Subscript n Superscript left-parenthesis t right-parenthesis](images/c11-i0070.png)

<math display="inline" overflow="scroll">
<msubsup><mrow><mi>I</mi></mrow><mrow><mi>n</mi></mrow><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msubsup>
</math>

to be the set of indexes of misclassified data given the current linear function ![f Superscript left-parenthesis t right-parenthesis Baseline left-parenthesis bold-italic x right-parenthesis equals bold-italic x Superscript down-tack Baseline bold-italic omega Superscript left-parenthesis t right-parenthesis](images/c11-i0071.png)

<math display="inline" overflow="scroll">
<msup><mi>f</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msup><mo stretchy="false">(</mo><mi mathvariant="bold-italic">x</mi><mo stretchy="false">)</mo><mo>=</mo><msup><mi mathvariant="bold-italic">x</mi><mo>&#8868;</mo></msup><msup><mi mathvariant="bold-italic">&#969;</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msup>
</math>

based on ![bold-italic omega Superscript left-parenthesis t right-parenthesis](images/c11-i0072.png)

<math display="inline" overflow="scroll">
<msup><mi mathvariant="bold-italic">&#969;</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msup>
</math>

, and we also recursively define

![upper L Superscript left-parenthesis t right-parenthesis Baseline left-parenthesis bold-italic omega right-parenthesis colon equals sigma-summation Underscript i element-of upper I Subscript n Superscript left-parenthesis t right-parenthesis Baseline Endscripts StartAbsoluteValue bold-italic omega Superscript down-tack Baseline bold-italic x Subscript i Baseline EndAbsoluteValue equals minus sigma-summation Underscript i element-of upper I Subscript n Superscript left-parenthesis t right-parenthesis Baseline Endscripts y Subscript i Baseline bold-italic omega Superscript down-tack Baseline bold-italic x Subscript i Baseline comma](images/c11-math-0005.png)

<math display="block" overflow="scroll">
<msup><mi>L</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msup><mo stretchy="false">(</mo><mi mathvariant="bold-italic">&#969;</mi><mo stretchy="false">)</mo><mo>:</mo><mo>=</mo><munder><mo>&#8721;</mo><mrow><mi>i</mi><mo>&#8712;</mo><msubsup><mi>I</mi><mi>n</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msubsup></mrow></munder><mfenced open="|" close="|" separators=""><mrow><msup><mi mathvariant="bold-italic">&#969;</mi><mo>&#8868;</mo></msup></mrow><msub><mi mathvariant="bold-italic">x</mi><mi>i</mi></msub></mfenced><mo>=</mo><mo>&#8722;</mo><munder><mo>&#8721;</mo><mrow><mi>i</mi><mo>&#8712;</mo><msubsup><mi>I</mi><mi>n</mi><mrow><mo stretchy="false">(</mo><mi>t</mi><mo stretchy="false">)</mo></mrow></msubsup></mrow></munder><msub><mi>y</mi><mi>i</mi></msub><msup><mi mathvariant="bold-italic">&#969;</mi><mrow><mo>&#8868;</mo></mrow></msup><msub><mi mathvariant="bold-italic">x</mi><mi>i</mi></msub><mo>,</mo>
</math>

such that the new iterated estimate is given by

