
interactions quantum behavior to improve molecules and materials.

from a dataset of bulk crystals and formation energies. Most importantly, we have performed an empirical molecular dynamics study on the fullerene C60 at PBE+dW level of theory that had not been compatible with common DFT approaches. The ensuing results guide future work such as larger molecules and periodic systems as well as further developments toward deep learning architectures to assist chemistry research.

## IV. CONCLUSIONS

Instead of painstakingly designing mechanical forces or machine learning descriptors, deep learning allows us to learn from first principles what adapts to the task and scale, and from hand, property prediction across chemical compound space to force theのである space of single molecules. The design challenge has been shifted to modeling quantum neural architecture. This gives rise to the possibility to encode quantum constraints and symmetries within the model without losing locality of a neural network. It is crucial to be able to capture e.g., the full potential-energy surface, and in particular, its anharmonic behavior,

## ACKNOWLEDGMENTS

This work was supported by the Federal Ministry of Education and Research (BMBF) for the Berlin Big Data Center (BIDC) (No.01510134). Additional support was provided by the DG (No. MU 98/2021), from the European Union's 2020 research program or under the Sklodowska-Curie Grant Agreement No 65769, the BKI program funded by the Korean Research Foundation (No.2014-05741) and the Institute for Information & Communications Promotion (ITEP) funded by the Korea government (No. 2017-0-00451). AT acknowledges support from the European Research Council (ERC-CoG grant.

We have presented the deep learning SchNet which has been applied to a variety of applications ranging from the prediction of chemical properties for diverse datasets of molecules and materials to highly accurate predictions of potential energy surfaces and energy-conserving forces. As a variant of DNNs, SchNet follows rotational, translational, and permutational invariances by design and, is able to model periodic boundary conditions. Not only does SchNet yield fast and accurate predictions, but it also allows us to learn the learned representation using local chemical potentials. We have found that fundamental chemical knowledge has been recovered

## APPENDIX A: ERROR 9 AND 10

In Figs 9 and 10, we show the histograms of the predicted properties of the QM9 and Materials Project dataset, respectively. The histograms include all test errors across three repetitions.

![](img/8414c867baf7c2cb6823215231b56027_9_0.png)

FIG. 9. Histograms of absolute errors for all predicted properties of QM9. The histograms are plotted on a logarithmic scale to visualize the distribution of the.

![](img/8414c867baf7c2cb6823215231b56027_10_0.png)

![](img/8414c867baf7c2cb6823215231b56027_10_1.png)

FIG. 10. Histogram of absolute errors for the predictions of formation energies/atom for the Materials Project dataset. The histogram is plotted on a logarithmic scale to visualize the tails of the distribution.

FIG. 11. Histogram of absolute errors for all predicted properties of QM9. The histograms are plotted on a logarithmic scale to visualize the tails of the distribution.

## APPENDIX B: SIMULATION DETAILS

The reference data for $C_{20}$ were generated using classical molecular dynamics in the NVE environment at 500 K using the Nose-Hoover thermostat with a time step of 1 fs. The forces and energies were computed using DFT with the non-empirical exchange-correlation functional (GGA) level of theory of PBE$^{39}$ and the Tkatchenko-Scheffler method (TS$^{40}$) to account for van der Waals interactions. The calculations were done using all-electrons with a plane wave basis set implemented in QE.

The quantum nature is introduced through imaginary molecular dynamics (PIMD) via Feynman's path integral. The PIMD simulations were done using the SchNet model implemented in C. Integration time step was set to 5 fs to ensure energy conservation within the NVE ensemble with a ring quantum approximation (RQA)$^{41}$. In PIMD, the treatment of nuclei is controlled by the number of beads. In our example for $C_{20}$, we see that using eight beads gives a converged radial distribution function $g(r)$ as shown in Fig. 11.

$^{39}$M. Rupp, V. Gobre, R. Müller, and A. von Llihenfeld, Phys. Rev. Lett. 108, 056301 (2012).
$^{40}$ G. Montavon, V. Rupp, R. Gobre, A. Vazduelez-Mayazaga, K. Ramirez, A. Tkatchenko, R. Müller, and O. von Llihenfeld, New J. Phys. 15, 093015 (2013).
$^{41}$ K. Hamann, G. Footmay, B. Siegler, S. Pauli, R. Rupp, M. Scheffler, A. von Llihenfeld, A. Tkatchenko, and R.-K. Müller, J. Chem. Theory Comp 9, 34013 (2015).
$^{42}$ F. Faber, A. Lindholm, O. von Llihenfeld, and R. Amiri, Int. J. Quantum Chem. 115, 10944 (2019).
$^{43}$R. Ramakrishnan, P. D. Real, M. Rupp, and O. von Llihenfeld, J. Chem. Theory Comp. 11, 1297 (2010).
$^{44}$K. Sato, F. Biegler, R. Ramakrishnan, W. Prombis, O. A. von Llihenfeld, J. Chem. Phys. 148, 6322 (2015).
$^{45}$F. Faber, A. Lindholm, O. von Llihenfeld, and R. Amiri, Phys. Rev. Lett. 98, 17601 (2007).
$^{46}$E. von Pydkin and A. Vachkov, Multiscale Science. 15, 827 (2017).
$^{47}$I. A. Fabian, S. Coker, T. Bohner, B. Jlinger, S. Scheelho, A. Adil, O. Vymos, K. Kramers, F. Riley, and O. von Llihenfeld, J. Chem. Phys. 131, 5525–5536 (2014).
$^{48}$H. Mao and M. Rupp, arXiv:1706.0694 (2017).
$^{49}$K. Ryu, M. Ilcik, J. Tkatchenko, and I. Horn, Phys. Rev. B 97, 11414 (prep.).
$^{50}$Y. Zhang, K. Ryu, and A. Iannelli, arXiv:1708.0316 (2017).
$^{51}$J. Behler and M. Parrini, Phys. Rev. Lett. 98, 14641 (2007).
$^{52}$A. Bartók, M. Cyni, and G. Colnei, Phys. Rev. Lett. 104, 19641 (2010).
$^{53}$R. Kun, M. Rynor, and G. Colnei, Phys. Rev. B 87, 18415 (2013).
$^{54}$A. Vachkov, Multiscale Science. 22, 313 (2016).
$^{55}$S. Chimiela, A. Tkatchenko, I. Polytov, T. Schütt, and K. Küh, Phys. Rev. Lett. 94, 17611 (2005).
$^{56}$F. Brockenberg, L. Joi, R. Burke, and A. Müller, Nature. 438, 772 (2005).
$^{57}$D. E. Jackson, and A. Reinen, Science. 319, 3912 (2007).
$^{58}$P. Rowe, G. Albrecht, and D. Michaels, Phys. Rev. B 95, 075103 (2017).
$^{59}$T. Henschel, D. Maclain, R. Burchell, T. Hirzel, and A. Aspruti, in Conference on Neural Processing Systems, vol. 28, 2222–2229 (2015).
$^{60}$S. Sezneans, R. McLockey, M. Berndt, V. Bande, and P. Riley, J. Chem. Angew. Mol. 30, 595 (2016).

28K. Schott, F. Farbazad, S. Chmiela, K.-R. Müller, and A. Tatchenko, Nat. Chem., 8, 1390 (2017).
29G. Silver, S. Goodman, P. F. Riley, O. Vinyals, and G. E. Dahl, in Proceedings of the 34th International Conference on Machine Learning (ICML 2017), pp. 1263–1272.
30S. Schott, T. J. K. Chmiela, S. Siedenska, and A. Tatchenko, in Advances in Neural Processing Systems, 30, 7765 (2017).
31B. Bachbauer, S. Schott, M. Harveland, M. Kanazawa, and K. Horn, in Advances in Neural Processing Systems, 30, 9912–9922 (2017).
32S. Simonyan, A. Davidev, G. Montanari, F. Kolesnik, K.-R. Müller, and A. Zisserman, in arXiv:1409.15534 (2014).
33B. Bach, J. Binder, K.-R. Müller, and A. Zisserman, J. Chem. Phys. 5, 708 (2016).
34L. Zintelman, T. S. Cohen, T. Adler, and M. Welling, in International Conference on Learning Representations (2017).
35G. Montanari, S. Lapuschnik, A. Binder, M. Saibel, and K.-R. Müller, Pattern Recognition, 115, 102698 (2019).
36S. Chmiela, A. Tatchenko, and K.-R. Müller, Digital Signal Processing, 73, 1 (2018).
37K. Wang, J. Ba, R. Kim, K. Cho, A. V, Salakhnikov, R. Zemel, and Y. Bengio, in International Conference on Machine Learning (ICML 2015), pp. 2048–2057.
38P. Perdew, K. Burke, and M. Ernzerhof, Phys. Rev. Lett. 77, 3885 (1996).
39A. Tatchenko and M. Schaefer, Phys. Rev. Lett. 102, 075305 (2009).
$^{40}$W. Wang and A. Tatchenko, J. Chem. Phys. 136, 0641 (2017).
$^{41}$H. Hamann and G. Tkatchenko, in funded by the Korean Research Foundation (No.2014-05741).
$^{42}$Y. Zhang and F. Footmay, Data Science, 21, 388 (2013).
$^{43}$R. Ramakrishnan, P. D. Real, M. Rupp, and O. von Llihenfeld, J. Chem. Theory Comp. 11, 1297 (2010).
$^{44}$K. Sato, F. Biegler, R. Ramakrishnan, W. Prombis, O. A. von Llihenfeld, J. Chem. Phys. 148, 6322 (2015).
$^{45}$F. Faber, A. Lindholm, O. von Llihenfeld, and R. Amiri, Phys. Rev. Lett. 98, 17601 (2007).
$^{46}$E. von Pydkin and A. Vachkov, Multiscale Science. 15, 827 (2017).
$^{47}$I. A. Fabian, S. Coker, T. Bohner, B. Jlinger, S. Scheelho, A. Adil, O. Vymos, K. Kramers, F. Riley, and O. von Llihenfeld, J. Chem. Phys. 131, 5525–5536 (2014).
$^{48}$H. Mao and M. Rupp, arXiv:1706.0694 (2017).
$^{49}$K. Ryu, M. Ilcik, J. Tkatchenko, and I. Horn, Phys. Rev. B 97, 11414 (prep.).
$^{50}$Y. Zhang, K. Ryu, and A. Iannelli, arXiv:1708.0316 (2017).
$^{51}$J. Behler and M. Parrini, Phys. Rev. Lett. 98, 14641 (2007).
$^{52}$A. Bartók, M. Cyni, and G. Colnei, Phys. Rev. Lett. 104, 19641 (2010).
$^{53}$R. Kun, M. Rynor, and G. Colnei, Phys. Rev. B 87, 18415 (2013).
$^{54}$A. Vachkov, Multiscale Science. 22, 313 (2016).
$^{55}$S. Chimiela, A. Tkatchenko, I. Polytov, T. Schütt, and K. Küh, Phys. Rev. Lett. 94, 17611 (2005).
$^{56}$F. Brockenberg, L. Joi, R. Burke, and A. Müller, Nature. 438, 772 (2005).
$^{57}$D. E. Jackson, and A. Reinen, Science. 319, 3912 (2007).
$^{58}$P. Rowe, G. Albrecht, and D. Michaels, Phys. Rev. B 95, 075103 (2017).
$^{59}$T. Henschel, D. Maclain, R. Burchell, T. Hirzel, and A. Aspruti, in Conference on Neural Processing Systems, vol. 28, 2222–2229 (2015).
$^{60}$S. Sezneans, R. McLockey, M. Berndt, V. Bande, and P. Riley, J. Chem. Angew. Mol. 30, 595 (2016).
