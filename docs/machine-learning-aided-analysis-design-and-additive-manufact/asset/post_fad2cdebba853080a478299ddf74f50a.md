
346

FG porous composite structures

- [99] Nguyen BD, Cho JS, Kang K. Optimal design of "Shellar", a micro-architected material with ultralow density. Mater Des 2016;19:495–500.
- [100] Bobbert F, et al. Additively manufactured metallic porous biomaterials on mini-mall surfaces: a unique combination of topological, mechanical, and transport properties. Acta Materia 2017;53:572–84.
- [101] Al-Ketan O, Abu-Rub RK. Functional mechanical metamaterials based on triperiodic minimal surfaces. Adv Eng Mater 2019;21(10). Available from: https://doi.org/10.1016/j.adeng.2019.106863
- [102] Smith PE. Types of marine structures. In: Inander MG, editor. Marine structures. Wood Publishing; 2016. p. 17–64.
- [103] Rosson BT, Tedesco JW. Dynamic response of armor units to test impact loads. Ocean Eng 1992;19:573–99. Available from: https://doi.org/10.1016/0029-458X(92)90053-X
- [104] Timco JW. On the structural integrity of armor units under dynamic loading conditions. Cost Eng 1983;7(1):99–7. Available from: https://doi.org/10.1016/0317-3839(83)90029-7
- [105] Tedesco JW, Rosson BT, Betty MJ. Static stresses in dressed concrete armor units. Comp Struct 1992;45(4):733–43. Available from: https://doi.org/10.1016/0164-1481(92)90045-5
- [106] Rosson BT, Tedesco JW. Dynamic response of armor units to impact loads. Comp Struct 1993;79(4):641–52. Available from: https://doi.org/10.1016/0164-1481(93)90348-8
- [107] Zhao C, Wang P, Wang L. Reducing railway noise with porous sound-absorbing concrete slabs. Adv Mater Sci 2016;206459. Available from: https://doi.org/10.1155/2016/206459
- [108] Wang P, Zhao C. Study on reducing railway noise by porous sound-absorbing panel. Mater Res In 2015;19(9):09005. Available from: https://doi.org/10.1179/14382917/1100000269
- [109] Park SB, Seo DS, Lee J. Study on the use of recycled aggregate and void ratio. Cen Con Res 2005;369:2801–54. Available from: https://doi.org/10.1016/j.jconconres.2004.12.069
- [110] Zhang Y, Li H, Alahdari A, De Li H. Laboratory investigation into sound absorption property of concrete with different mixtures. Con Build Mat 2020;209:120414. Available from: https://doi.org/10.1016/j.conbuildmat.2020.120414
- [111] Mena C, et al. Opportunities and challenges for structural engineering of geopolymer fabricated concrete. Cement Constr 2020;133:106079. Available from: https://doi.org/10.1016/j.con.2020.106079
- [112] Saleh T.A.M., Ahmed Z.Y., Bos F.P., Hahlund L.M. 3D printed concrete bridge. In: Proceedings of the third international conference on progress in advance manufacturing (Pro-Am 2018). Singapore: 2018.
- [113] Saleh T.A.M, Ahmed Z.Y., Bos F P, Hahlund L.M. Design of a 3D printed concrete bridge by testing. Virtual Phys Prototyp 2018;13(3):222–36. Available from: https://doi.org/10.1080/17452759.2018.147604
- [114] Wang NP. Zurich’s 3D printed foam uses 70% less concrete than traditional formworks. Available: https://archiveconnect.com/article/1502397/zurich-3d-printed-foam-uses-70-less-concrete-than.

## Design and fabrication of additively manufactured functionally graded structures

Yu Duan$^{1,2,3}$, Xiaopeng Shi$^{1,2}$, Xian Zhao$^{1,2}$, Bing Hou$^{1,2}$, Yulong Li$^{1,2}$
$^{1}$School of Aeronautics, Northwestern Polytechnical University, Xi'an, Shaanxi, P.R. China
$^{2}$Joint International Laboratory of Impact Dynamics, Northwestern Polytechnical University, Xi'an, Shaanxi, P.R. China
$^{3}$Center of Mechanics, Zhejiang University, Hangzhou, Zhejiang, P.R. China
$^{4}$School of Safety and Engineering, Civil Aviation University, Tianjin, P.R. China

### 14.1 Introduction

Vehicles inevitably suffer from unpredictable impact loads, as fragments in aerospace [1], on aircraft [2], and on vehicles [3]. Despite plenty of work being done, accidents caused by impact loads continue to occur, which can be solved by impact-resistant and energy-absorbing structures. This structure can effectively compensate for the load of transports and significantly increase the survival rate of occupants. The energy-absorbing materials play a key role. 

They became popular recently because of their specific strength, high stiffness, and high energy absorption affinity and have been widely used in various fields, including aerospace, transportation, and so on.

Terms, cellular material and porous material are both used in academic papers. These two materials share features of a large number of holes [5]. Generally, materials fail to cause stress concentration, which lead to crack propagation and failure. However, when the proportion of holes reaches a certain level, the ratio of total hole volume to total material volume is defined as porosity $\phi$. To better the relative density as $\bar{\rho} = 1 - \phi$, indicating the ratio of the density of materials with holes to the density of their base material (the corresponding dense material). In porous materials correspond to $\bar{\rho} < 0.7$ while dense materials correspond to $\rho > 0.3$. As shown in [14], different porosity correspond to different applications, In practice, a wide range of porosity is involved, where the exact criterion of porosity is difficult to cover in all situations. Therefore in the following sections, this chapter does not distinguish between porous materials and cellular materials. Instead, following the classic work of Gibson and Ashby [8], both of them are called cellular solids, referring to materials with a large number of holes.

As shown in Fig.14.2, cellular solids can be classified into disordered foams and ordered lattice structures. Materials can be open-cell and closed foams. Open foams are connected by edges, and there is no cell filling between the edges [12]. Closed-cell foam refers to cellular solids with holes separated by cell walls [13]. A lattice structure is a kind of structural material composed of one or more structural units. According to its macro dimension, it can be divided into one-dimensional (1D) lattice (like architecture [14]), two-dimensional (2D) lattice (like honeycomb architecture [15]), and three-dimensional (3D) lattice (like oct-truss architecture [16]).

The above discussions are limited to uniform cellular solids, which physical properties are uniformly distributed. However, uniform cellular solids lack design flexibility. To improve the mechanical properties of uniform cellular solids, many studies have focused on graded solids. Graded cellular solids lie at the intersection between gradient materials [17,18] and cellular solids [19,20]. It not only has design of gradient materials but also more complete deformation and excellent energy absorption capability than uniform cellular solids.

So, far most of the studies have focused on numerical simulation, including two methods to build a graded cellular solid. On one hand, a discrete gradient is

![](img/90ed165a39fa708ec43fcfc79319c25_350_0.png)

**Fig 14.1** Applications of cellular structures [9,10].
Source: Reproduced with permission from Bahart J. Manufacture, characterisation of cellular materials and metal foams. Prog Mater Sci 2001;46:559–632; Nazir A, Abate KM, Kumar A, Jeng-J.Y. A state-of-the-art review on types, design, optimization, and additive manufacturing of cellular structures. Int J Adv Man Technol 2019;104:3489–510. Copyright 2001, Elsevier.
