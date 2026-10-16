
The polyline distance metric (PDM) is used for computing the stenosis and LD error bias. Let the LI far and LI near borders be denoted as `*C*[1]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn126.gif"/` and `*C*[2]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn127.gif"/`, respectively. Let the reference point on `*C*[1]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn128.gif"/` be vertex `*R*[1]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch8ieqn129.gif"/` and the segment in `*C*[2]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn130.gif"/` be defined by vertices `*R*[2]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch8ieqn131.gif"/` and `*R*[3]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn132.gif"/`. Let the distance between `*R*[1]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch8ieqn133.gif"/` and `*R*[2]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch8ieqn134.gif"/` be `*d*[1]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn135.gif"/` and the distance between `*R*[1]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch8ieqn136.gif"/` and `*R*[3]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn137.gif"/` be denoted as `*d*[2]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn138.gif"/`. Let `D(*R*[1], *L*)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-2244-7ch8ieqn139.gif"/` be the PD between vertex `*R*[1]` : (*x*[1], *y*[1])inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-2244-7ch8ieqn140.gif"/ on `*C*[1]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn141.gif"/` and line segment `*L*`inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-2244-7ch8ieqn142.gif"/` formed by two points `*R*[2]` : (*x*[2], *y*[2])inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-2244-7ch8ieqn143.gif"/` and `*R*[3]` : (*x*[3], *y*[3]).inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-2244-7ch8ieqn144.gif"/. Let `δ` (`*δ*inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-2244-7ch8ieqn145.gif"/`) be the distance of the reference point `*R*[1]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch8ieqn146.gif"/` towards the line segment `*L*`inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-2244-7ch8ieqn147.gif"/`. The perpendicular distance between the line segment `*L*`inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-2244-7ch8ieqn148.gif"/` and the reference point, `*R*[1]inline-graphic style="height:1.0625em;" xlink:href="bk978-0-7503-2244-7ch8ieqn149.gif"/`, is specified by `*d*[*p*]inline-graphic style="height:1.3125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn150.gif"/`. Then, the polyline distance `D(*R*[1], *L*)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-2244-7ch8ieqn151.gif"/` can be defined as  

``` 
$$D(R\_{1},L) = \\left\\{ \\begin{array}{l} \\begin{array}{lc} {\\mid d\_{p}\\mid} & {0 < \\delta < 1} \\\\ \\end{array} \\\\ \\begin{array}{lc} {\\min(d\_{1},d\_{2})} & {\\delta < 0,\\delta > 1} \\\\ \\end{array} \\\\ \\end{array} \\right.,$$  
```  

(8.5) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch8eqn152.gif" position="float"/  

where  

``` 
$$d\_{1} = \\sqrt{\\left( {x\_{1} - x\_{2}} \\right)^{2} + \\left( {y\_{1} - y\_{2}} \\right)^{2}}$$  
```  

(8.6) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch8eqn153.gif" position="float"/  

``` 
$$d\_{2} = \\sqrt{\\left( {x\_{1} - x\_{3}} \\right)^{2} + \\left( {y\_{1} - y\_{3}} \\right)^{2}}$$  
```  

(8.7) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch8eqn154.gif" position="float"/  

``` 
$$\\delta = \\frac{\\left( {y\_{3} - y\_{2}} \\right)\\left( {y\_{1} - y\_{2}} \\right) + (x\_{3} - x\_{2})(x\_{1} - x\_{2})}{\\left( {x\_{3} - x\_{2}} \\right)^{2} + \\left( {y\_{3} - y\_{2}} \\right)^{2}}$$  
```  

(8.8) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch8eqn155.gif" position="float"/  

and  

``` 
$$d\_{p} = \\frac{\\left( {y\_{3} - y\_{2}} \\right)\\left( {x\_{2} - x\_{1}} \\right) + (x\_{3} - x\_{2})(y\_{1} - y\_{2})}{\\sqrt{\\left( {x\_{3} - x\_{2}} \\right)^{2} + \\left( {y\_{3} - y\_{2}} \\right)^{2}}}.$$  
```  

(8.9) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch8eqn156.gif" position="float"/  

The process to obtain `D(*R*[1], *L*)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-2244-7ch8ieqn157.gif"/` is repeated for the remaining points of the outline `*C*[*j*]inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-2244-7ch8ieqn158.gif"/` and is specified by  

``` 
$$D\\left( {C\_{1},C\_{2}} \\right) = \\sum\\limits\_{i = 1}^{N}{D(R\_{i},S\_{C\_{2}}),}$$  
```  

(8.10) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch8eqn159.gif" position="float"/  

where `*N*inline-graphic style="height:0.9375em;" xlink:href="bk978-0-7503-2244-7ch8ieqn160.gif"/` represents all points on `*C*[1]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn161.gif"/` and `*S*[*C*[2]]inline-graphic style="height:1.25em;" xlink:href="bk978-0-7503-2244-7ch8ieqn162.gif"/` is the section on outline of `*C*[2]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn163.gif"/`. This algorithm is recurring in reverse, where `*C*[2]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn164.gif"/` becomes the reference outline and `*C*[1]inline-graphic style="height:1.125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn165.gif"/` becomes the segment outline. The reverse is symbolized as `*D*(*C*[2], *C*[1])inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-2244-7ch8ieqn166.gif"/`. Finally, by combining both `*D*(*C*[1],*C*[2])inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-2244-7ch8ieqn167.gif"/` and `*D*(*C*[2], *C*[1])inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-2244-7ch8ieqn168.gif"/`, we obtain the PDM which is specified by  

``` 
$$\\quad D\_{PDM}\\left( {C\_{1}:C\_{2}} \\right) = \\frac{D\\left( {C\_{1},C\_{2}} \\right) + D(C\_{2},C\_{1})}{(\\#{points} \\in C\_{1} + \\#{points} \\in C\_{2})}.$$  
```  

(8.11) graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch8eqn169.gif" position="float"/  

*Results for LD*  

For the first DL1, the corresponding PoMs for stenosis and the LD error bias are specified in tables [8.2](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8t2) and [8.3](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8t3), respectively. Similarly, the stenosis and LD error bias tables for DL2 and DL3 are shown in tables [8.4](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8t4) and [8.5](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8t5) and tables [8.6](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8t6) and [8.7](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8t7), respectively. The corresponding plots for DL1, DL2, and DL3 are shown in figures [8.6](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8fig6), [8.7](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8fig7), and [8.8](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8fig8), respectively. Each of the DL systems was trained for 4000 iterations.  

**Table 8.2.** Mean PoM stenosis (%) of DL1 w.r.t. GT1. (Reproduced with permission from \[[66](#Chapter_8.xhtml#bk978-0-7503-2244-7ch8bib66)\].)  

| \# Images || Mean DL1 stenosis (%) || Mean GT1 stenosis (%) || Mean PoM1 (stenosis) (%) |
| --- | --- | --- | --- |
| 10 || 57.2 || 57.2 || 93.7 |
| 50 || 42.1 || 40.8 || 94.6 |
| 100 || 35.2 || 33.1 || 95.6 |
| 150 || 31.2 || 28.9 || 96.1 |
| 200 || 28.4 || 26.0 || 96.3 |
| 250 || 26.1 || 23.8 || 96.2 |
| 300 || 24.2 || 21.9 || 96.4 |
| 350 || 22.5 || 20.3 || 96.5 |
| 407 || 20.5 || 18.6 || 96.7 |
