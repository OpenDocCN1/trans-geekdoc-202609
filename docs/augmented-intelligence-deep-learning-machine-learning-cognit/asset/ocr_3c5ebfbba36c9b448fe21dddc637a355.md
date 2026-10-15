# 3.4. EXPERIMENTS

For the discussion of sections 3.5.1.3 and 3.6, we used the spectra provided by Dr. Kalivas [27]. This data set contains 60 different gasoline samples with different compositions and octane numbers (ON). The samples were analyzed by near-infrared spectroscopy (NIR) and measured using diffuse reflectance, between 900 and 1700 nm, with a spacing of 2 nm.

For the discussion of section 3.7, we used the spectra obtained experimentally in a recently published work [28]. The data set consists of 144 samples of pure and tylosin-spiked milk. The samples were analyzed by Attenuated total reflectance-Fourier transform infrared spectroscopy (ATR-FTIR) between 3000 and 1000 cm⁻¹ using DairySpec FT equipment (Bentley Instruments, Chaska, USA).

All chemometric analyzes were performed in software R (R Foundation, Austria) version 4.0.0, together with the packages randomForest v. 4.6, ranger v. 0.12.1, rpart v. 3.0.9, pls v. 2.7, neuralnet v. 1.44.2, brglm 0.6.2, gbm v. 2.1.5, through the caret aggregator package (classification and regression training) version 6.0.

# 3.5. DIMENSIONALITY REDUCTION IN RAW SPECTROSCOPIC SPACE

A typical Fourier transform infrared spectroscopy analysis is usually performed between 4000 and 400 cm⁻¹, with a spectral step of 2 cm⁻¹. A chemometric analysis that considers each wave number obtained in the scan as an independent variable to be analyzed would come across a high-dimensional space containing 1801 potential variables.

Naturally, the number of cases experimentally observed using this instrumental technique is much lesser than the total number of attributes that can be extracted. In such cases, even if wrongly, the parametric machine learning algorithms are preferably used for model fitting. Models based on this type of algorithm summarize data with a set of supervised statistic parameters of fixed size in class estimation. In other words, in the training step, the functional extracts parameters are based on strong statistical assumptions and use some method to estimate the input data. Some examples of parametric machine learning algorithms include linear regression, logistic regression, partial least squares regression (PLS), main components regression (PCR), simple neural networks, among others. These algorithms are also called linear machine learning algorithms [29].