
$Q\left( \mathbf{\Xi},\mathbf{P};\mathbf{\Xi}^{(j)},\mathbf{P}^{(j)} \right) = \sum\limits_{n = 1}^{N}\sum\limits_{k = 1}^{K}\gamma_{nk}\left( \ln P_{k} + y_{n}\ln s_{nk} + (1 - y_{n})\ln(1 - s_{nk}) \right),$

![Equation](images/B9780443292385000184/si421.png)(12.110)

where

$\gamma_{nk} = \mathbb{E}\lbrack z_{nk}\rbrack = P\left( k|y_{n},\mathbf{\Xi}^{(j)},\mathbf{P}^{(j)} \right) = \frac{P_{k}^{(j)}s_{nk}^{y_{n}}{(1 - s_{nk})}^{1 - y_{n}}}{\sum_{i = 1}^{K}P_{i}^{(j)}s_{ni}^{y_{n}}{(1 - s_{ni})}^{1 - y_{n}}}.$

![Equation](images/B9780443292385000184/si422.png)(12.111)

Note that in Eq. [(12.111)](#Chp012_583-634_B9780443292385000184.xhtml#deq154), the notation $s_{nk}^{(j)},\ s_{ni}^{(j)}$ should have been used, but we tried to unclutter it slightly.

In the M-step, maximization with respect to $P_{k}$ is of the same form as it was for the regression task, and it leads to
