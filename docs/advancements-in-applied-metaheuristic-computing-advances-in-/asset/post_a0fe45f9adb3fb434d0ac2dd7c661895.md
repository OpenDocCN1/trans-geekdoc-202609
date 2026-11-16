
## Optimized Crossover JumpX in Genetic Algorithm for General Routing Problems

### Figure 9. Simulations results on TSPLIB instances

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_241_0.png)

### Figure 10. Evolution during the GA of mean min max objective function (ch130, JMPX)

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_242_0.png)

For the Moroccan context, Figure 13 shows a simulation of our algorithm, on a real instance with a real data set of the Moroccan road network. The concept of Volunteered Geographic Information has recently emerged with the new Web 2.0 technologies. The OpenStreetMap project is currently the most significant example of a VGI-based system (Girres & Touya, 2010). It aims to produce free geographic databases using the contributions of Internet users.

We cleaned the data and organized it for use, and then transformed it into a road graph in QGIS (Tsou & Smith, 2011).

We choose 128 of the important and largest cities in Morocco, in terms of population, and therefore the most demanding in terms of goods. Then we run a Dijkstra algorithm to find the shortest paths between each of the selected cities on the road graph, and then we have launched the genetic algorithm with that input data to optimize the overall path.

## CONCLUSION

This paper presented a new genetic crossover operator for solving the TSP using GAs. The new method is tested and compared to other conventional crossover operators and methods: Partially matched crossover (PMX), Edge recombination Crossover (ERX) and r-opt Heuristic. To conclude on the overall performance of

### Figure 11. Comparative convergence (eil76)

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_243_0.png)

it, simulations study shows the remarkable performance of the proposed method of crossing (jump crossover).

Thus, we evaluate and compare the proposed JMPX with the three different methods for one TSP objective function namely, minimizing total travel distance. The benchmarking was performed using TSPLIB. The experimental results show that in most cases the JMPX operator enables the GA to produce high solution quality in less time than the existing crossover operators.

The crossover method proposed is simple to implement, it should help to solve other difficult problems quickly, reliably and accurately.

Our future work will focus on two main areas: Firstly, studying the contribution of classic mutation operators such as Inversion, Displacement, Insertion and Exchange

### Figure 12. Multi-level approach to freight modeling (adapted from Xu, Hancock, & Southworth, 2003)

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_244_0.png)

### Figure 13. Simulation on 128 Moroccan cities

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_244_1.png)

mutation used with the just studied crossovers and then, applying genetic algorithm to optimize design and management of a global supply chain. Secondly, since many practical problems can be modeled by the multi objective TSP (MTSP), we will use the JMPX operator into our existing GA for solving a large multi objective TSP problem in green supply chain management including minimizing greenhouse gas into objective functions.

## REFERENCES

Abdoun, O., & Abouchabaka, J. (2011). A Comparative Study of Adaptive Crossover Operators for Genetic Algorithms to Resolve the Traveling Salesman Problem. International Journal of Computers and Applications, 31(11), 49–57.

Ahmed Hamza, A., Ahmad Taher, A., & Aboul Ella, H. (2014). A New Heuristic Function of Ant Colony System for Retinal Vessel Segmentation. International Journal of Rough Sets and Data Analysis, 1(2), 15–30. doi:10.4018/ijrsda.2014070102

Amal Mahmoud, A., & Sawsan, A. (2015). Hybridizing Artificial Bee Colony Algorithm with Multi-Parent Crossover Operator. International Journal of Applied Metaheuristic Computing, 6(2), 18–32. doi:10.4018/IJAMC.2015040102

Ashour, A. S., Samanta, S., Dey, N., Kausar, N., Abdessalemkaraa, W. B., & Hassanien, A. E. (2015). Computed tomography image enhancement using cuckoo search: A log transform based approach. Journal of Signal and Information Processing, 6(03), 244–257. doi:10.4236/jsip.2015.63023

Binh, H. T. T., Hanh, N. T., Van Quan, L., & Dey, N. (2016). Improved Cuckoo Search and Chaotic Flower Pollination optimization algorithm for maximizing area coverage in Wireless Sensor Networks. Neural Computing & Applications, 1–13. doi:10.1007/s00521-016-2823-5

Bontoux, B., Artigues, C., & Feillet, D. (2010). A Memetic Algorithm with a large neighborhood crossover operator for the Generalized Traveling Salesman Problem. Computers & Operations Research, 37(11), 1844–1852. doi:10.1016/j.cor.2009.05.004

Bouttier, C., Babando, O., Gadat, S., Gerchinovitz, S., Laporte, S., & Nicol, F. (2017). Adaptive Simulated Annealing with Homogenization for Aircraft Trajectory Optimization. In K. Doerner, I. Ljubic, G. Pflug, & G. Tragler (Eds.), Operations Research Proceedings 2015: Selected Papers of the International Conference of the German, Austrian and Swiss Operations Research Societies (GOR, ÖGOR, SVOR/ASRO) (pp. 569-574). Cham: Springer International Publishing. doi:10.1007/978-3-319-42902-1_77

Cicirello, V. A., & Smith, S. F. (2000). Modeling GA Performance for Control Parameter Optimization. Paper presented at the GECCO.

Davis, L. (1985). Applying Adaptive Algorithms to Epistatic Domains. San Francisco, CA: Academic Press.

Davis, L. D. (1991). Handbook Of Genetic Algorithms. Van Nostrand Reinhold.

Deep, K., & Mehrahtu, H. (2011). New Variations of Order Crossover for Travelling Salesman Problem. International Journal of Combinatorial Optimization Problems and Informatics, 2(1), 2–13.

Deep, K., & Mehrahtu, H. (2012). Variant of partially mapped crossover for the Travelling Salesman problems. International Journal of Combinatorial Optimization Problems and Informatics, 3(1), 47–69.

Dey, N., Chakraborty, S., & Samanta, S. (2014). Optimization of Watermarking in Biomedical Signal: Lambert Publication. Heinrich-Böcking-Straße, 6, 66121.

Dey, N., Samanta, S., Chakraborty, S., Das, A., Chaudhuri, S. S., & Suri, J. S. (2014). Firefly Algorithm for Optimization of Scaling Factors During Embedding of Manifold Medical Information: An Application in Ophthalmology Imaging. Journal of Medical Imaging and Health Informatics, 4(3), 384–394. doi:10.1166/jmihi.2014.1265

Dey, N., Samanta, S., Yang, X.-S., Das, A., & Chaudhuri, S. S. (2013). Optimisation of scaling factors in electrocardiogram signal watermarking using cuckoo search. International Journal of Bio-inspired Computation, 5(5), 315–326. doi:10.1504/IJBIC.2013.057193

Dwivedi, V., Chauhan, T., Saxena, S., & Agrawal, P. (2012). Travelling Salesman Problem using Genetic Algorithm. Paper presented at the National Conference on Development of Reliable Information Systems, Techniques and Related Issues.

Eiben, A. E., Hinterding, R., & Michalewicz, Z. (1999). Parameter control in evolutionary algorithms. IEEE Transactions on Evolutionary Computation, 3(2), 124–141. doi:10.1109/4235.771166

Farahani, R. Z., Rezapour, S., Drezner, T., & Fallah, S. (2014). Competitive supply chain network design: An overview of classifications, models, solution techniques and applications. Omega, 45, 92–118. doi:10.1016/j.omega.2013.08.006

Freisleben, B., & Merz, P. (1996). New genetic local search operators for the traveling salesman problem. In Parallel Problem Solving from Nature—PPSN IV (pp. 890–899). Springer. doi:10.1007/3-540-61723-X_1052

Girres, J.-F., & Touya, G. (2010). Quality Assessment of the French OpenStreetMap Dataset. Transactions in GIS, 14(4), 435–459. doi:10.1111/j.1467-9671.2010.01203.x

Goel, S., & Wadhwa, V. (2013). A comparative analysis of PMX, POS and OX crossover operators for solving. International Journal of Latest Research in Science and Technology, 2(2), 80–83.

Goldberg, D. E. (1989). Genetic Algorithms in Search, Optimization, and Machine Learning. Addison-Wesley Longman Publishing Co.

Goldberg, D. E., & Lingle, R. (1985). Alleles, loci, and the traveling salesman problem. Proceedings of the First International Conference on Genetic Algorithms and Their Applications, 154-159.

Grefenstette, J., Gopal, R., Rosmaita, B., & Van Gucht, D. (1985). Genetic algorithms for the traveling salesman problem. Proceedings of the first International Conference on Genetic Algorithms and their Applications.

Holland, J. H. (1975). Adaptation in Natural and Artificial Systems. The University of Michigan Press.

Hore, S., Chatterjee, S., Santhi, V., Dey, N., Ashour, A. S., Balas, V. E., & Shi, F. (2017). Indian Sign Language Recognition Using Optimized Neural Networks. In V. E. Balas, L. C. Jain, & X. Zhao (Eds.), Information Technology and Intelligent Transportation Systems: Vol. 2. Proceedings of the 2015 International Conference on Information Technology and Intelligent Transportation Systems ITITS 2015 (pp.553–563). Cham: Springer International Publishing. doi:10.1007/978-3-319-38771-0_54

Iyad Abu, D., Faisal, A., Eslam Al, M., Mohammed Azmi, A.-B., & Basima Hani, F. H. (2013). Hybridizing Harmony Search Algorithm with Multi-Parent Crossover to Solve Real World Optimization Problems. International Journal of Applied Metaheuristic Computing, 4(3), 1–14. doi:10.4018/ijamc.2013070101

Jog, P., Suh, J. Y., & Gucht, D. v. (1989). The effects of population size, heuristic crossover and local improvement on a genetic algorithm for the traveling salesman problem. Proceedings of the Third International Conference on Genetic Algorithms.

Johnson, D. S., & McGeoch, L. A. (2002). Experimental analysis of heuristics for the STSP. In The traveling salesman problem and its variations (pp. 369–443). Springer.

Kanungo, D. P., Janmenjoy, N., Bighnaraj, N., & Behera, H. S. (2016). Hybrid Clustering using Elitist Teaching Learning-Based Optimization: An Improved Hybrid Approach of TLBO. International Journal of Rough Sets and Data Analysis, 3(1), 1–19. doi:10.4018/IJRSDA.2016010101
