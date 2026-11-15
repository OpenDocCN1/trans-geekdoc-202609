
## 3.6 Conclusion

Five basic designs were selected in this study which had good compressive strength compared to the amount of water and cement used. In this study, six design variables, the amount of aggregate with different sizes, have been taken into account. Based on the results obtained from the Taguchi method and five basic designs, an artificial neural network was trained based on the results obtained from the Taguchi method and the five basic designs. Upon comparing the laboratory results with the results obtained from the ANN, it was found that the used ANN produced appropriate and acceptable results. The trained artificial neural network and the EVPS and SA-EVPS metaheuristic algorithms were then used to define an optimization problem in order to determine a design with the highest compressive strength, and the results of the optimization were also analyzed in the laboratory, which demonstrated that the results met the target in a satisfactory manner. For further research, it is recommended that the process used in this article be used.

## References

- 1. Hosseini P, Kaveh A, & Naghian A. (2023) The use of artificial neural networks and metaheuristic algorithms to optimize the compressive strength of concrete, Int J Optim Civil Eng, 13(3):327–338
- 2. Habert G, J.B d’Espinose de Lacaillerie, & Roussel N. (2011) An environmental evaluation of geopolymer based concrete production: reviewing current research trends. J Cleaner Product, 19(11): 1229–38
- 3. Imbabi M.S, Carrigan C, & McKenna S. (2012) Trends and developments in green cement and concrete technology. Int J Sustain Built Environ 1(2): 194–216
- 4. Sabbaghian M, & Kheyroddin A. (2023) The relationship between compressive strength and splitting tensile strength of high-performance fiber-reinforced cementitious composites. J Rehab Civil Eng 11(4): 1–21
- 5. Palavar O, Özyürek D, & Kalyon A. (2015) Artificial neural network prediction of aging effects on the wear behavior of IN706 superalloy. Mater Des 82: 164–72
- 6. Laguna M, & Martí.R. (2002) Neural network prediction in a system for optimizing simulations. IIE Trans 34(3): 273–82
- 7. Lu, C, Li S, & Lu Z. (2022) Building energy prediction using artificial neural networks: A literature survey. Ener Build 262: p. 111718
- 8. Zou J, Han YI & So S-S. (2009) Overview of artificial neural networks. Artificial Neural Networks Methods Applic 14–22
- 9. Chen WH, Urubie MC, Kwon EE, Lin KYA, Park YK, Ding L, & Saw LHA. (2022) Comprehensive review of thermoelectric generation optimization by statistical approach: Taguchi method, analysis of variance (ANOVA), and response surface methodology (RSM). Renew Sustain Ener Rev 169: 112917
- 10. Lv B, & Cai J. (2023) Simulation and analysis of geometric parameters based on Taguchi method in Y-Y microfluidic device for circulating tumor cell separation by alternating current dielectrophoresis. J Chromato A; 1693: 463894

## Chapter 4
Design of Double Layer Grids Using Backpropagation Neural Networks

**Abstract** In this chapter an efficient neural networks are trained for design of double layer grids. Square diagonal-on-diagonal grids with spans varying between 26.5 and 75 m are considered. Backpropagation algorithm is employed for training efficient neural networks for evaluation of the maximum deflection, weight, and design of double layer grids. A special method is developed for data ordering to reduce the nonlinearity of the data and to increase the speed of training.

### 4.1 Introduction

In this chapter efficient neural networks are trained for design of double layer grids based on Kaveh and Servati [1]. Square diagonal-on-diagonal grids with spans varying between 26.5 and 75 m are considered. Backpropagation algorithm is employed for training efficient neural networks for evaluation of the maximum deflection, weight, and design of double layer grids. A special method is developed for data ordering to reduce the nonlinearity of the data and to increase the speed of training. This approach also provides the necessary stability. Additional neural nets are trained and tested for design of grids using the developed data ordering.

Double layer grids are one of the most popular types of space structures. Analysis and design of such structures are normally time consuming since a large number of nodes and members is involved. The problem becomes more involved when nonlinear analysis or optimization is performed, where numerous analyses should be carried out.

Space structures are often used for covering large spans. Sport stadiums, assembly halls, exhibition centers, swimming pools, shopping arcades and industrial buildings are typical examples of structures where large unobstructed areas are essential and where minimum interference from internal support is required. Space structures are often classified as grids, domes and barrel vaults, Makowski [2].

Double layer grids are typical examples of prefabricated space structures and also one of the most popular forms which are frequently used nowadays. These structures have proved to be very economic in terms of the height and ease in construction.

### 4.2 Structural Models and Element Grouping

The model considered in this chapter is a double layer grid with bar elements, connected by MERO type of joints. Each span contains 11 bays of equal length in both directions. The structure is assumed to be supported at corners on three nodes, i.e. it is connected to the columns at 12 nodes. The length of the spans, L, is varied between 26.5 and 75.0 m with the steps of 5 m. The height is varied between 0.035 and 0.095 L with the step of 20 cm.

In order to simplify the design, the 1808 elements of the structure are put into 16 groups, and the structure is assumed to comprise of 16 types of cross-sections. Due to the symmetry, and positioning of the supports at the corners, the elements with equal distance from the center node are put in groups and the cross-sections of each group are taken to be the same. Five such groups are constructed. The elements at top, bottom layers and diagonal elements can have different cross-sections. Thus a total of 15 groups of elements are identified and hatched differently. An additional group is associated with the boundary elements at the top layer, increasing the number of element groups to 16, Fig. 4.1. A simple program “Groupype” is developed for this grouping and associating the numbers 1–16 to the elements of the structure. Another program “Finaltype” uses the output of the “Groupype” and the input of SAP90 and selects the largest cross-section for the element of the same type, and associates this type to all the elements of the same group.

A total number of 219 structures are generated and analyzed from which the results of 179 structures are used for training and 40 are employed for testing the networks.

In the analysis and design of double layer grids a large number of nodes and members are involved, making them time consuming. Configuration processing and data generation for these structures is also a problem, which can be simplified using the concepts for formex configuration processing [3]. For large-scale problems the analysis is usually time consuming due to a large number of equations being involved. Therefore approximate methods are needed in the process of nonlinear analysis, design and optimization.

Neural networks provide a powerful tool for approximate analysis of space structures. Such networks are trained using backpropagation [4] and counter propagation networks [5]. In this chapter efficient neural networks are trained for various aspects of analysis and design of double layer grids. A particular type of grid, namely square diagonal-on-diagonal, is selected for this study and the spans are chosen from 26.5 to 75 m. Backpropagation algorithm is employed for training efficient neural networks for evaluation of the maximum deflection, weight, and design of double layer grids. A special method is developed for data ordering to reduce the nonlinearity of the data and to increase the speed of training. This approach also provides the necessary stability. Additional neural nets are trained and tested for design of grids using the developed data ordering.
