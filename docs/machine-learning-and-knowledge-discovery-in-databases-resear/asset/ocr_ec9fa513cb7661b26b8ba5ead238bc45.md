# Table 2. Top-3 subgroups per dataset maximizing $\varphi_{rauls}$. 

| \(\Omega_i\) | Most certain subgroups S | \(\varphi_{rauls}(S)\) |
|---|---|---|
| \(\Omega_1\) | free sulfur dioxide > 130.444 and alcohol > 10.756 | 1.471 |
| | free sulfur dioxide > 130.444 and sulphates \(\le\) 0.507 | 1.471 |
| | free sulfur dioxide > 130.444 and sulphates \(\le\) 0.411 | 1.471 |
| \(\Omega_2\) | self reference max shares > 562200.000 | 7.082 |
| | and self reference avg shares \(\le\) 76711.111 | |
| | self reference max shares > 749600.000 | 6.532 |
| | and min negative polarity \(\le\) -0.667 | |
| | self reference max shares > 562200.000 | 6.282 |
| | and num self hrefs > 25.778 | |
| \(\Omega_3\) | V12 > 226.693 and V10 \(\le\) 170.078 | 30.025 |
| | V21 \(\le\) -14.767 and V12 > 198.388 | 29.809 |
| | V21 \(\le\) -14.767 and V19 > 77.927 | 29.612 |
| \(\Omega_4\) | Hillshade Noon \(\le\) 56.444 | 0.085 |
| | and Horizontal Distance To Fire Points \(\le\) 7 173.000 | |
| | Hillshade Noon \(\le\) 56.444 | 0.085 |
| | and Horizontal Distance To Fire Points \(\le\) 6 376.000 | |
| | Hillshade Noon \(\le\) 56.444 | 0.085 |
| | and Horizontal Distance To Fire Points \(\le\) 5 579.000 | |
| \(\Omega_5\) | GLUCOSE > 538.333 and SODIUM \(\le\) 135.667 | 136.275 |
| | GLUCOSE > 538.333 and ALBUMIN > 3.133 | 133.106 |
| | GLUCOSE > 538.333 and CHLORIDE \(\le\) 106.000 | 132.774 |
| \(\Omega_6\) | population > 3 967.333 and households \(\le\) 1 352.333 | 51 232.926 |
| | population > 3 967.333 and total rooms \(\le\) 8 432.000 | 51 137.378 |
| | longitude > -115.426 and median income \(\le\) 2.111 | 49 965.760 |
| \(\Omega_7\) | V35 \(\le\) -342.419 and V6 \(\le\) -1.723 | 10.106 |
| | V35 \(\le\) -342.419 and V1 > 41.529 | 9.671 |
| | V3 \(\le\) -94.950 and V35 \(\le\) -201.227 | 9.655 |

On the other hand, when comparing the final columns of Tables 1 and 3, the values for the datasets Wine Quality (\(\Omega_1\)) and News Popularity (\(\Omega_2\)) stand out. For the subgroups found on these datasets, we see that \(\varphi_{rauls}\) is smaller than \(AUL(\Omega_i)\), which implies that the average uncertainty loss of the top-ranked subgroups is just larger than average uncertainty loss on the entire dataset. I.e.: Conformalized EMM discovered subgroups for which classifiers are highly unconfident about their prediction set. We notice that for News Popularity dataset, the discovered subgroups demonstrate an uncertainty set of size 10, which is the largest set we encountered within our experiments: Conformalized EMM identified the prediction that contains all the possible labels in the prediction set, which shows the most uncertain performance.