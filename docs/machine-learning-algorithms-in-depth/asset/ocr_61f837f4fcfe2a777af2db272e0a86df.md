```
class naive_bayes:
    def __init__(self, K, D):
        self.K = K
        self.D = D
        self.pi = np.ones(K)
        self.theta = np.ones((self.D, self.K))

    def fit(self, X_train, y_train):
        num_docs = X_train.shape[0]
        for doc in range(num_docs):
            label = y_train[doc]
            self.pi[label] += 1
            for word in range(self.D):
                if (X_train[doc][word] > 0):
                    self.theta[word][label] += 1
                #end if
            #end for
        #end for
        #normalize pi and theta
        self.pi = self.pi/np.sum(self.pi)
        self.theta = self.theta/np.sum(self.theta, axis=0)

    def predict(self, X_test):
        num_docs = X_test.shape[0]
        logp = np.zeros((num_docs, self.K))
        for doc in range(num_docs):
            for kk in range(self.K):
                logp[doc][kk] = np.log(self.pi[kk])
                for word in range(self.D):
                    if (X_test[doc][word] > 0):
                        logp[doc][kk] += np.log(self.theta[word][kk])
                    else:
                        logp[doc][kk] += np.log(1-self.theta[word][kk])
                    #end if
                #end for
            #end for
        return np.argmax(logp, axis=1)

if __name__ == "__main__":
    import nltk
    nltk.download('stopwords')
    #load data
    print("loading 20 newsgroups dataset...")
    tic = time()
    classes = ['sci.space', 'comp.graphics', 'rec.autos', 'rec.sport.hockey']
```

Class priors

Number of classes

Dictionary size

Bernoulli parameters