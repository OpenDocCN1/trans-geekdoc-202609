
```
if __name__ == "__main__":

    #LDA parameters
    num_features = 1000  #vocabulary size
    num_topics = 4       #fixed for LD

    #20 newsgroups dataset
    categories = ['sci.crypt', 'comp.graphics', 'sci.space',
     'talk.religion.misc']

    newsgroups = fetch_20newsgroups(shuffle=True, random_state=42,
     subset='train',
                     remove=('headers', 'footers', 'quotes'),
                     categories=categories)

    vectorizer = TfidfVectorizer(max_features = num_features, max_df=0.95,
     min_df=2, stop_words = 'english')
    dataset = vectorizer.fit_transform(newsgroups.data)
    A = np.transpose(dataset.toarray())  #term-document matrix

    lda = LDA(A=A, K=num_topics)
    llh = lda.variational_inference(var_iter=10)
    id2word = {v:k for k,v in vectorizer.vocabulary_.items()}

    #display topics
    for k in range(num_topics):
        print("topic: ", k)
        print("----------")
        topic_words = ""
        top_words = np.argsort(lda.lambda[k,:])[-10:]
        for i in range(len(top_words)):
            topic_words += id2word[top_words[i]] + " "
            print(id2word[top_words[i]])

        wordcloud = WordCloud(width = 800, height = 800,
                        background_color ='white',
                        min_font_size = 10).generate(topic_words)

        plt.figure()
        plt.imshow(wordcloud)
        plt.axis("off")
        plt.tight_layout(pad = 0)
        plt.show()
```

Figure 9.3 shows the increase in ELBO as the number of mean-field iterations increases. Figure 9.4 shows the inferred topic distributions visualized as word clouds.

![](img/325742126d3ff007c6c385f4ffb5c3be_215_0.png)

Figure 9.3  Increase in ELBO vs. the number of mean-field iterations

![](img/325742126d3ff007c6c385f4ffb5c3be_215_1.png)

Figure 9.4  Inferred topic distributions via LDA mean-field variational inference

As we can see from the output, the top-K words for each topic match the categories in the 20 newsgroups dataset. In the following section, we will explore several methods to model the probability density of data for computational biology and finance.

## 9.2  *Density estimators*

The goal of *density estimation* is to model the probability density of data. In this section, we will discuss kernel density estimators applied to computational biology and look at how we can optimize a portfolio of stocks using tangent portfolio theory.

### 9.2.1  *Kernel density estimator*

An alternative approach to a K-component mixture model is a *kernel density estimator* (KDE) that allocates one cluster center per data point. KDEs are an application of

kernel smoothing for probability density estimation that use kernels as weights. In the case of a Gaussian kernel, we have the following.

$$p(x|D) = \frac{1}{N} \sum_{i=1}^{N} \mathcal{N}(x|x_i, \sigma^2 I)\tag{9.10}$$

Notice that we are averaging N Gaussians, with each Gaussian centered at the data point x_i. We can generalize the expression in equation 9.10 to any kernel κ(x).

$$p(x|D) = \frac{1}{N} \sum_{i=1}^{N} \kappa_h(x - x_i)\tag{9.11}$$

The advantage of KDEs over parametric models, such as density mixtures, is that no model fitting is required (except for fine-tuning the bandwidth parameter h) and there is no need to pick the number of mixtures K. The disadvantage is that the model takes a lot of memory to store as well as time to evaluate. In other words, KDE is suitable when an accurate density estimate is required for a relatively small dataset (small number of points N). Let's look at an example that analyzes RNA-seq data to estimate the flux of a T7 promoter.

### Listing 9.2 Kernel density estimate

```
import numpy as np
import matplotlib.pyplot as plt

class KDE():
    def __init__(self):
        #Histogram and Gaussian Kernel Estimator used to
        #analyze RNA-seq data for flux estimation of a T7 promoter
        self.G = 1e9
        self.C = 1e3
        self.L = 100
        self.N = 1e6
        self.M = 1e4
        self.LN = 1000
        self.FDR = 0.05

        #uniform sampling (poisson model)
        self.lambda = (self.N * self.L) / self.G
        self.C_est = self.M/(1-np.exp(-self.lambda))
        self.C_cvrg = self.G - self.G * np.exp(-self.lambda)
        self.N_gaps = self.N * np.exp(-self.lambda)

        #gamma prior sampling (negative binomial model)
        #X = "number of failures before rth success"
```

Dispersion parameter
(fit to data)

Success probability

Number of successes

Smoothing parameter

Standard deviation

Dimension of x

```
```python
self.k = 0.5
self.p = self.lmbda/(self.lmbda + 1/self.k)
self.r = 1/self.k

#RNAP binding data (RNA-seq)
self.data = np.random.negative_binomial(self.r, self.p, size=self.LN)

def histogram(self):
    self.bin_delta = 1
    self.bin_range = np.arange(1, np.max(self.data), self.bin_delta)
    self.bin_counts, _ = np.histogram(self.data, bins=self.bin_range)

    #histogram density estimation
    #P = integral R p(x) dx, where X is in R^3
    #p(x) = K/(N x V), where K-number of points in region R
    #N=total number of points, V=volume of region R

    rnap_density_est = self.bin_counts/(sum(self.bin_counts) *
        self.bin_delta)
    return rnap_density_est

def kernel(self):
    #Gaussian kernel density estimator with smoothing parameter h
    #sum N Guassians centered at each data point, parameterized by
    # common std dev h

    x_dim = 1
    h = 10

    rnap_density_support = np.arange(np.max(self.data))
    rnap_density_est = 0
    for i in range(np.sum(self.bin_counts)):
        rnap_density_est += (1/(2*np.pi*h**2))**((x_dim/2.0))*np.exp(-
            (rnap_density_support - self.data[i])**2 / (2.0*h**2))
    #end for

    rnap_density_est = rnap_density_est / np.sum(rnap_density_est)
    return rnap_density_est

if __name__ == "__main__":

    kde = KDE()
    est1 = kde.histogram()
    est2 = kde.kernel()

    plt.figure()
    plt.plot(est1, c='b', label='histogram')
    plt.plot(est2, c='r', label='gaussian kernel')
    plt.title("RNA-seq density estimate based on negative binomial sampling model")
    plt.xlabel("read length, [base pairs]"); plt.ylabel("density");
    plt.legend()
    plt.show()
```

Figure 9.5 shows the RNA-seq density estimate based on the negative binomial model. It shows two density estimates—one based on a histogram and the other based on Gaussian Kernel Density Estimator. We can see that the Gaussian density is much smoother and that we can further fine-tune bin size smoothing parameter in the histogram estimator.

![](img/325742126d3ff007c6c385f4ffb5c3be_218_0.png)

Figure 9.5  RNA-seq density estimate via histogram and Gaussian KDE

### 9.2.2  Tangent portfolio optimization

The objective of mean-variance analysis is to maximize the expected return of a portfolio for a given level of risk, as measured by the standard deviation of past returns. By varying the mixing proportions of each asset, we can achieve different risk–return tradeoffs.

In listing 9.3, we first retrieve a data frame of closing prices for a list of stocks. We then examine stock price correlations via a scatter matrix plot. We then create a randomized portfolio and compute the portfolio risk. Next, we generate 1,000 randomly weighted portfolios and compute their value and risk. Finally, we choose the nearest neighbor portfolio weights in a way that minimizes standard deviation and maximizes portfolio value.

### Listing 9.3  Tangent portfolio optimization

```
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.neighbors import KDTree
from pandas.plotting import scatter_matrix
from scipy.spatial import ConvexHull
```

```
import pandas_datareader.data as web
from datetime import datetime
import pytz

STOCKS = ['SPY','LQD','TIP','GLD','MSFT']

np.random.seed(42)

if __name__ == "__main__":

    plt.close("all")

    #load data
    #year, month, day, hour, minute, second, microsecond
    start = datetime(2012, 1, 1, 0, 0, 0, 0, pytz.utc)
    end = datetime(2017, 1, 1, 0, 0, 0, 0, pytz.utc)

    data = pd.DataFrame()
    series = []
    for ticker in STOCKS:
        price = web.DataReader(ticker, 'stooq',
            start, end)
        series.append(price['Close'])

    data = pd.concat(series, axis=1)
    data.columns = STOCKS
    data = data.dropna()

    scatter_matrix(data, alpha=0.2, diagonal='kde')
    plt.show()

    cash = 10000
    num_assets = np.size(STOCKS)
    cur_value = (1e4-5e3)*np.random.rand(num_assets,1) + 5e3
    tot_value = np.sum(cur_value)
    weights = cur_value.ravel()/float(tot_value)

    Sigma = data.cov().values
    Corr = data.corr().values
    volatility = np.sqrt(np.dot(weights.T,
        np.dot(Sigma, weights)))

    plt.figure()
    plt.title('Correlation Matrix')
    plt.imshow(Corr, cmap='gray')
    plt.xticks(range(len(STOCKS)),data.columns)
    plt.yticks(range(len(STOCKS)),data.columns)
    plt.colorbar()
    plt.show()

    num_trials = 1000
    W = np.random.rand(num_trials, np.size(weights))
    W = W/np.sum(W,axis=1).reshape(num_trials,1)
```
