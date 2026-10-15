
Incorporating actual intelligence into the machines and making them think and perform like humans is impossible. In this chapter, a new kind of machine called the EDLM (exact deep learning machine) is introduced. Such EDLMs can achieve the target with probability one and could be the best alternative for originally designed artificial intelligence models of the mid-20th century by Alan Turing and others that have so far not seen reality. In the current context, achieving a target is defined as detecting a given object accurately.

### Keywords

Artificial intelligence; Probability one; Object detection

### MSC

68T07; 68T05

## 1: Introduction

It is impossible to train human-made computational machines to think and perform like humans. Training of computational machines involves making the machine read the data and understand logical rule-based instructions. A machine could be designed such that it can construct further rules from a combination of finite rules provided to the machine. Such a design involves the programming of algorithms that can instruct a machine to construct newer rules of performance. Whether or not a machine can come up with a newer rule without any specific instructions to perform from a list of rules already provided to it is still questionable. This is because the so-called advanced machines to date have not shown any signs of self-thinking capabilities without being told to them in some or other forms of machine training algorithms. Human intelligence is so far not shown evidence to transfer or implant human-like intelligence into computational machines.

There have been advancements in statistical machine learning ([Angelino et al., 2017](#Ch001_1-8_S0169716122000554.xhtml#bb0010); [Fokoué and Titterington, 2003](#Ch001_1-8_S0169716122000554.xhtml#bb0060); [Matsui, 2010](#Ch001_1-8_S0169716122000554.xhtml#bb0075); [Tadaki, 2012](#Ch001_1-8_S0169716122000554.xhtml#bb0125); [Tollenaar and van der Heijden, 2013](#Ch001_1-8_S0169716122000554.xhtml#bb0135)), well-defined mathematical structures in machine learning ([Blum et al., 1989](#Ch001_1-8_S0169716122000554.xhtml#bb0025); [Cucker and Smale, 2002](#Ch001_1-8_S0169716122000554.xhtml#bb0050); [Govindaraju and Rao, 2013](#Ch001_1-8_S0169716122000554.xhtml#bb0065); [Niyogi et al., 2011](#Ch001_1-8_S0169716122000554.xhtml#bb0090); [Smale and Zhou, 2007](#Ch001_1-8_S0169716122000554.xhtml#bb0100); [Van Messem, 2020](#Ch001_1-8_S0169716122000554.xhtml#bb0140)), advancements in data science aspects ([Baladram et al., 2020](#Ch001_1-8_S0169716122000554.xhtml#bb0020); [Brunton and Kutz, 2022](#Ch001_1-8_S0169716122000554.xhtml#bb0030); [Chen, 2015](#Ch001_1-8_S0169716122000554.xhtml#bb0040); [Nazarathy and Klok, 2021](#Ch001_1-8_S0169716122000554.xhtml#bb0085); [Yeturu, 2020](#Ch001_1-8_S0169716122000554.xhtml#bb0145)), and improvisations in understanding data structures within machine learning ([Calma et al., 2018](#Ch001_1-8_S0169716122000554.xhtml#bb0035); [Ferraz et al., 2021](#Ch001_1-8_S0169716122000554.xhtml#bb0055); [Poggio and Smale, 2003](#Ch001_1-8_S0169716122000554.xhtml#bb0095); [Srinivasa Rao and Diamond, 2020](#Ch001_1-8_S0169716122000554.xhtml#bb0110); [Srinivasa Rao and Vazquez, 2020](#Ch001_1-8_S0169716122000554.xhtml#bb0115), [2022](#Ch001_1-8_S0169716122000554.xhtml#bb0120). Training machines with exact deep learning (introduced here) could be the closest possible alternatives to artificial intelligence (AI) models. So far, researchers were not successful in seeing self-thinking machines that were originally thought possible by Alan Turing and others ([COE, n.d](#Ch001_1-8_S0169716122000554.xhtml#bb0045).).

Deep learning machines with information on all possible distinct objects whose data is relevant are critical for successful machine learning. Only partial information on complete subjects or complete information on partial distinct subjects would not be sufficient for accurate machine learning, and performances of machines to attain given targets. In this chapter, we demonstrate a novel machine called the EDLM (exact deep learning machine) which can achieve the target suggested to the machine with the probability one. We provide one case scenario here, and EDLM can be extended to many situations under the assumptions and limitations provided. The central idea of EDLM is explained through a theorem in the next section.

## 2: EDLM constructions

Theorem 1: EDLM theorem

Suppose an object can be described within a finite number of distinct attributes and these attributes are not dynamic over time. Then, machines trained with attribute information can detect the object with probability one.

Proof

Let *O* be the object that is to be detected accurately by a machine. Suppose *O* is uniquely described by exactly *a*‑attributes, say, *y*[1], *y*[2], … *y*[*a*]![si2_e](images/S0169716122000554/si2_e.png) which are distinct. It is given that the attributes to describe *O* do not change with time or these attributes are not dynamic over time. Here attributes can be treated as the description of an object that is enough to define that particular object. That means *a*‑attributes are enough to describe the object *O*. Suppose the machine is trained with a triplet of information, say, {*O*, *A*(*y*), *Y* (*c*)}, where *O* is the object to be detected by the machine, *A*(*y*) is the set of attributes that completely describe *O*, and *Y* (*c*) is the set of values that each attribute can pick. The object *O* is described based on the set of predecided finite numerical values. The set *A*(*y*) = {*y*[1], *y*[2], … *y*[*a*]}![si3_e](images/S0169716122000554/si3_e.png). The set *Y* (*c*) consists of all possible values of each of the attribute *y*[*j*] for *j* = 1, 2, … , *a*![si4_e](images/S0169716122000554/si4_e.png). The attribute *y*[*j*] can choose any one of the *c*[*c*[*j*]*j*]![si5_e](images/S0169716122000554/si5_e.png) possibilities for *j* = 1, 2, …, *a*![si6_e](images/S0169716122000554/si6_e.png). That is,

``` 
$\\begin{matrix} {Y(c) = \\begin{Bmatrix} {y\\_{1} = \\lbrack c\\_{11},c\\_{21},\\ldots,c\\_{c\\_{1}1}\\rbrack} \\\\ {y\\_{2} = \\lbrack c\\_{12},c\\_{22},\\ldots,c\\_{c\\_{2}2}\\rbrack} \\\\ \\vdots \\\\ {y\\_{a} = \\lbrack c\\_{1a},c\\_{2a},\\ldots,c\\_{c\\_{a}a}\\rbrack} \\\\ \\end{Bmatrix}} \\\\ \\end{matrix}
``` 
```

![si7_e](images/S0169716122000554/si7_e.png)  (1)

In Eq. ([1](#Ch001_1-8_S0169716122000554.xhtml#fo0010)) the quantities *c*[*c*[*j*]*j*]![si5_e](images/S0169716122000554/si5_e.png) for *j* = 1, 2, …, *a*![si6_e](images/S0169716122000554/si6_e.png) need not be identical. This implies that the number of possible values for *y*[1], *y*[2,]… *y*[*a*]![si10_e](images/S0169716122000554/si10_e.png) need not be the same. The object *O* will be described by {*O*, *A*(*y*), *Y* (*c*)} with each *y*[*j*] choosing only one of the values \[*c*[1*j*], *c*[2*j*], …, *c*[*c*[*j*]*j*]\]![si11_e](images/S0169716122000554/si11_e.png) for *j* = 1, 2, …, *a*![si6_e](images/S0169716122000554/si6_e.png). Suppose “0” indicates the absence of *c*[*c*[*j*]*j*]![si5_e](images/S0169716122000554/si5_e.png) and “1” indicates the presence *c*[*c*[*j*]*j*]![si5_e](images/S0169716122000554/si5_e.png) in *y*[*j*]. All the attributes of *Y* (*c*) can be listed for the absence or presence of values of each attribute as follows:

``` 
$\\begin{aligned} {y\\_{1} =} & {\\lbrack c\\_{11}(0,1),c\\_{21}(0,1),\\ldots,c\\_{c\\_{1}1}(0,1)\\rbrack} \\\\ {y\\_{2} =} & {\\lbrack c\\_{12}(0,1),c\\_{22}(0,1),\\ldots,c\\_{c\\_{2}2}(0,1)\\rbrack} \\\\ & \\vdots \\\\ {y\\_{a} =} & {\\lbrack c\\_{1a}(0,1),c\\_{2a}(0,1),\\ldots,c\\_{c\\_{a}a}(0,1)\\rbrack} \\\\ \\end{aligned}
``` 
```

![si15_e](images/S0169716122000554/si15_e.png)  (2)
