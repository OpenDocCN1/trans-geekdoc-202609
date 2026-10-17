
```
display="block" overflow="scroll"
<<table>
  <mtr>
    <td columnalign="right"><mi>f</mi><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><msub><mrow><mo stretchy="false">&#124;</mo></mrow><mrow><msub><mrow><mi>x</mi></mrow><mrow><mi>i</mi></mrow></msub><mo>=</mo><msub><mrow><mi>a</mi></mrow><mrow><mn>2</mn></mrow></msub><mo>,</mo><msub><mrow><mi>x</mi></mrow><mrow><mi>j</mi></mrow></msub><mo>=</mo><msub><mrow><mi>b</mi></mrow><mrow><mn>1</mn></mrow></msub></mrow></msub></td>
    <td columnalign="center"><mo>&#60;</mo></td>
    <td columnalign="left"><mi>f</mi><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><msub><mrow><mo stretchy="false">&#124;</mo></mrow><mrow><msub><mrow><mi>x</mi></mrow><mrow><mi>i</mi></mrow></msub><mo>=</mo><msub><mrow><mi>a</mi></mrow><mrow><mn>1</mn></mrow></msub><mo>,</mo><msub><mrow><mi>x</mi></mrow><mrow><mi>j</mi></mrow></msub><mo>=</mo><msub><mrow><mi>b</mi></mrow><mrow><mn>1</mn></mrow></msub></mrow></msub><mo>&#8743;</mo></td>
  </mtr>
  <mtr>
    <td class="eqnarray-1"><mi>f</mi><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><msub><mrow><mo stretchy="false">&#124;</mo></mrow><mrow><msub><mrow><mi>x</mi></mrow><mrow><mi>i</mi></mrow></msub><mo>=</mo><msub><mrow><mi>a</mi></mrow><mrow><mn>2</mn></mrow></msub><mo>,</mo><msub><mrow><mi>x</mi></mrow><mrow><mi>j</mi></mrow></msub><mo>=</mo><msub><mrow><mi>b</mi></mrow><mrow><mn>2</mn></mrow></msub></mrow></msub></td>
    <td class="eqnarray-2"><mo>&#62;</mo></td>
    <td class="eqnarray-3"><mi>f</mi><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><msub><mrow><mo stretchy="false">&#124;</mo></mrow><mrow><msub><mrow><mi>x</mi></mrow><mrow><mi>i</mi></mrow></msub><mo>=</mo><msub><mrow><mi>a</mi></mrow><mrow><mn>1</mn></mrow></msub><mo>,</mo><msub><mrow><mi>x</mi></mrow><mrow><mi>j</mi></mrow></msub><mo>=</mo><msub><mrow><mi>b</mi></mrow><mrow><mn>2</mn></mrow></msub></mrow></msub><mo>,</mo><mtext> with</mtext><mspace width="0.15em"/></td>
  </mtr>
</<table>>
```

![StartLayout 1st Row 1st Column f left-parenthesis bold x right-parenthesis vertical-bar Subscript x Sub Subscript i Subscript equals a 2 comma, x Sub Subscript j Subscript equals b 1 Baseline delta-equals f left-parenthesis x 1 comma, ellipsis comma x Subscript i minus 1 Baseline, a 2 comma, ellipsis comma x Subscript j minus 1 Baseline, b 1 comma, ellipsis, x Subscript d Baseline right-parenthesis comma, 2nd Column Blank 3rd Column Blank EndLayout](img/c01-math-0010.png)

```math
display="block" overflow="scroll"
<<table>
  <mtr>
    <td columnalign="right"><mi>f</mi><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><msub><mrow><mo stretchy="false">&#124;</mo></mrow><mrow><msub><mrow><mi>x</mi></mrow><mrow><mi>i</mi></mrow></msub><mo>=</mo><msub><mrow><mi>a</mi></mrow><mrow><mn>2</mn></mrow></msub><mo>,</mo><msub><mrow><mi>x</mi></mrow><mrow><mi>j</mi></mrow></msub><mo>=</mo><msub><mrow><mi>b</mi></mrow><mrow><mn>1</mn></mrow></msub></mrow></msub></td>
    <td columnalign="left"><mi>f</mi><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><msub><mrow><mo stretchy="false">&#124;</mo></mrow><mrow><msub><mrow><mi>x</mi></mrow><mrow><mi>i</mi></mrow></msub><mo>=</mo><msub><mrow><mi>a</mi></mrow><mrow><mn>2</mn></mrow></msub><mo>,</mo><msub><mrow><mi>x</mi></mrow><mrow><mi>j</mi></mrow></msub><mo>=</mo><msub><mrow><mi>b</mi></mrow><mrow><mn>1</mn></varepsilon></msub></mrow></msub><mo>&#8743;</mo></td>
  </mtr>
</<table>>
```

在优化阶段，每个非分离组中的决策变量（即 `![script í’¢ Subscript kappa](img/c01-i0122.png)<math display="inline" overflow="scroll"><msub><mrow><mi mathvariant="script">&#54434;</mi></mrow><mrow><mi>&#9544;</mi></mrow></msub></math>`）以协同演化的方式进行迭代优化，其中优化器可以是任何支持决策向量`variable‐wise`（变量级）更新的无导优化算法。换句话之，CC 框架要求优化算法能够灵活地确定哪些决策变量需要独立更新。作为一个代表性例子，粒子群算法（PSO）已被证明其`pseudo‐gradient`（伪梯度）特性非常适合作为 CC 框架中的嵌入式优化器 [72]。

PSO 是 Kennedy 和 Eberhart 在 1995 年引入的一种强大且广泛使用的群体智能范式 [73]，最初用于模拟鸟群聚集等社会行为，后来被简化为适用于求解优化问题。PSO 迭代地维护一个粒子群，每个粒子都有一对位置和速度。在 PSO 中，假设每个粒子都能记住历史上找到的最优位置，即整个群体找到过的最佳位置，称为 `global best`（全局最优），以及每个粒子找到过的最佳位置，被称为 `personal best`（个体最优）。为了找到优化问题的全局最优解，粒子从个体最优位置和全局最优位置中学习学习。具体而言，标准 PSO 中的学习机制可以总结如下：

```
(1.10)![StartLayout 1st Row 1st Column bold v Subscript i Superscript t plus 1 2nd Column equals omega bold v Subscript i Superscript t Baseline plus c 1 bold r 1 Superscript t Baseline white circle left-parenthesis bold pbest Subscript i Superscript t Baseline minus bold x Subscript i Superscript t Baseline right-parenthesis 2nd Row 1st Column Blank 2nd Column plus c 2 bold r 2 Superscript t Baseline white circle left-parenthesis bold gbest Superscript t Baseline minus bold x Subscript i Superscript t Baseline right-parenthesis comma, EndLayout](img/c01-math-0011.png)

<math display="block" overflow="scroll"><mtable columnalign="right left" class="aligned"><mtr><mtd><msubsup><mrow><mi mathvariant="bold">v</mi></mrow><mrow><mi>i</mi></mrow><mrow><mi>t</mi><momo><mn>1</mn></></></mtext></mtd></td><td><mo><>=</><mo><mi9996mi><mi><><><><><="="="bold</mi</mi></><><><><mi>i</mi><><><mi><mi</t></t></></></><><omo><msub><mrow><mi>mi>c</mi</mrow><mn><1>1</mn></msub><msub><><><><><mi="="="rmimimi><mrow><mn>1</1</</><mrow><mi>mi</mi</></></></mtext><mspace width="0.15em"/><mo>&#9675;</mo><mspace width="0.15em"/><mo stretchy="false">(</mo><><><mrow><mtext mathvariant="bold">pbest</mtext></mrow><mrow><mi>i</mi></mrow><mrow><mi>t</mi></mrow></msubsup><mo>&#8722;</mo><msubsup><mrow><mi mathvariant="bold">x</mi></mrow><mrow><mi>i</mi></mrow><mrow><mi>t</mi></mrow></msubsup><mo stretchy="false">)</mo></td></mtr><mtr><mtd></mtd><td><mspace width="1em"/><mo>+</mo><msub><mrow><mi>c</mi></mrow><mrow><mn>2</mn></></></msub><><><mrow><mi="="bold">r</mi></mrow><><><><mn>2</></></></><><><mitt</</></></></><>< width width0.115emmomoomo&#9675momo><mspace width="0.15em"/><mo stretchy="false">(</mo><msup><mrow><mtext mathvariant="bold">gbest</mtext></mrow><mrow><mi>t</mi></mrow></msup><mo>&#8722;</mo><msubsup><mrow><mi mathvariant="bold">x</mi></mrow><mrow><mi>i</mi></mrow><mrow><mi>t</mi></mrow></msubsup><mo stretchy="false">)</mo><mo,mo></td></mtr><//table>></math> (1.11)
```
