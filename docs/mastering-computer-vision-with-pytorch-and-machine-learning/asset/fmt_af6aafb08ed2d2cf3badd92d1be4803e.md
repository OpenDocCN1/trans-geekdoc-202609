
### B Expectation-maximization algorithm

$$L = - \ln \left( {P\left( X \right)} \right) = - \ln \prod\limits_{j = 1}^{n}{p\left( x_{j} \right)} = - \sum\limits_{j = 1}^{n}{\ln \left( {\sum\limits_{i = 1}^{3}{p\left( x_{j}\mid z_{i} \right)}p\left( z_{i} \right)} \right)}$$

$$ \frac{\partial L}{\partial \mu_{1}} = - \frac{\partial}{\partial \mu_{1}}\sum\limits_{j = 1}^{n}{\ln \left( { p\left( x_{j} \right)} \right)} = - \sum\limits_{j = 1}^{n}{\frac{1}{p\left( x_{j} \right)}\frac{\partial p\left( x_{j} \right)}{\partial \mu_{1}}} = - \sum\limits_{j = 1}^{n}{\frac{1}{p\left( x_{j} \right)}\frac{\partial}{\partial \mu_{1}}}\sum\limits_{i = 1}^{3}{p\left( x_{j}\mid z_{i} \right)}p\left( z_{i} \right)$$

$$ \frac{\partial L}{\partial \mu_{1}} = - \sum\limits_{j = 1}^{n}{\frac{1}{p\left( x_{j} \right)}\frac{\partial}{\partial \mu_{1}}}\sum\limits_{i = 1}^{3}{\frac{1}{\sqrt{2\pi \sigma_{i}^{2}}}}e^{- \frac{1}{2}{(\frac{x_{j} - \mu_{i}}{\sigma_{i}})}^{2}}p\left( z_{i} \right) = - \sum\limits_{j = 1}^{n}{\frac{1}{p\left( x_{j} \right)}\frac{p\left( z_{1} \right)}{\sqrt{2\pi \sigma_{1}^{2}}}}e^{- \frac{1}{2}{(\frac{x_{j} - \mu_{1}}{\sigma_{1}})}^{2}}\frac{x_{j} - \mu_{1}}{\sigma_{1}^{2}}$$

$$ \frac{\partial L}{\partial \mu_{1}} = - \frac{1}{\sigma_{1}^{2}}\sum\limits_{j = 1}^{n}{\frac{p\left( x_{j},z_{1} \right)}{p\left( x_{j} \right)}(x_{j} - \mu_{1})} = - \frac{1}{\sigma_{1}^{2}}\sum\limits_{j = 1}^{n}{p\left( z_{1}\mid x_{j} \right)}(x_{j} - \mu_{1}) = 0$$

$$ \mu_{1} = \frac{\sum\limits_{j = 1}^{n}{x_{j}p\left( z_{1}\mid x_{j} \right)}}{\sum\limits_{j = 1}^{n}{p\left( z_{1}\mid x_{j} \right)}}$$

$$ \mu_{i} = \frac{\sum\limits_{j = 1}^{n}{x_{j}p\left( z_{i}\mid x_{j} \right)}}{\sum\limits_{j = 1}^{n}{p\left( z_{i}\mid x_{j} \right)}}$$

$$ \frac{\partial L}{\partial v_{1}} = - \frac{\partial}{\partial v_{1}}\sum\limits_{j = 1}^{n}{\ln \left( { p\left( x_{j} \right)} \right)} = - \sum\limits_{j = 1}^{n}{\frac{1}{p\left( x_{j} \right)}\frac{\partial p\left( x_{j} \right)}{\partial v_{1}}} = - \sum\limits_{j = 1}^{n}{\frac{1}{p\left( x_{j} \right)}\frac{\partial}{\partial v_{1}}}\sum\limits_{i = 1}^{3}{p\left( x_{j}\mid z_{i} \right)}p\left( z_{i} \right)$$

$$ \frac{\partial L}{\partial v_{1}} = - \sum\limits_{j = 1}^{n}{\frac{1}{p\left( x_{j} \right)}\frac{\partial}{\partial v_{1}}}\sum\limits_{i = 1}^{3}{\frac{1}{\sqrt{2\pi v_{i}}}}e^{- \frac{1}{2v_{i}}{(x_{j} - \mu_{i})}^{2}}p\left( z_{i} \right) = - \sum\limits_{j = 1}^{n}{\frac{1}{p\left( x_{j} \right)}\frac{\partial}{\partial v_{1}}}\left( {\frac{1}{\sqrt{2\pi v_{1}}}}e^{- \frac{1}{2v_{1}}{(x_{j} - \mu_{1})}^{2}} \right)p\left( z_{1} \right)$$

$$ \frac{\partial L}{\partial v_{1}} = - \sum\limits_{j = 1}^{n}{\frac{p\left( z_{1} \right)}{p\left( x_{j} \right)}\left\lbrack {\frac{- 1}{2v_{1}^{3/2}\sqrt{2\pi}}e^{- \frac{1}{2v_{1}}{(x_{j} - \mu_{1})}^{2}} + \frac{1}{\sqrt{2\pi v_{1}}}}e^{- \frac{1}{2v_{1}}{(x_{j} - \mu_{1})}^{2}}\frac{1}{2v_{1}^{2}}\left( x_{j} - \mu_{1} \right)^{2}} \right\rbrack}$$

$$ \frac{\partial L}{\partial v_{1}} = - \sum\limits_{j = 1}^{n}{\frac{p\left( z_{1} \right)}{p\left( x_{j} \right)}\left\lbrack {\frac{- 1}{2v_{1}}p(x_{j}\mid z_{1}) + p(x_{j}\mid z_{1})\frac{1}{2v_{1}^{2}}\left( x_{j} - \mu_{1} \right)^{2}} \right\rbrack}$$

$$ \frac{\partial L}{\partial v_{1}} = - \sum\limits_{j = 1}^{n}{\frac{p\left( x_{j}\mid z_{1} \right)p\left( z_{1} \right)}{p\left( x_{j} \right)}\left\lbrack {\frac{- 1}{2v_{1}} + \frac{1}{2v_{1}^{2}}\left( x_{j} - \mu_{1} \right)^{2}} \right\rbrack}$$
