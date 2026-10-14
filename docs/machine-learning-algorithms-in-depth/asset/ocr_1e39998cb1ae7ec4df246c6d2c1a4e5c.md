```
```
self.theta = self.theta + eta *
    y_train[idx] * X_train[idx, :]
self.theta0 = self.theta0 + eta *
    y_train[idx]
#end if

print("epoch: ", epoch)
print("theta: ", self.theta)
print("theta0: ", self.theta0)
#end for
#end for

def predict(self, X_test):
    n = X_test.shape[0]
    dim = X_test.shape[1]

    y_pred = np.zeros(n)
    for idx in range(n):
        y_pred[idx] = np.sign(np.dot(self.theta, X_test[idx, :]) +
            self.theta0)
    #end for
    return y_pred

if __name__ == "__main__":
    iris = load_iris()
    X = iris.data[:100,:]
    y = 2*iris.target[:100] - 1
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2,
        random_state=42)

    #perceptron (binary) classifier
    clf = perceptron(num_epochs=5, dim=X.shape[1])
    clf.fit(X_train, y_train)
    y_pred = clf.predict(X_test)

    cmt = confusion_matrix(y_test, y_pred)
    acc = np.trace(cmt)/np.sum(np.sum(cmt))
    print("perceptron accuracy: ", acc)

    #generate plots
    plt.figure()
    sns.heatmap(cmt, annot=True, fmt="d")
    plt.title("Confusion Matrix"); plt.xlabel("predicted");
    plt.ylabel("actual")
    plt.savefig("./figures/perceptron_acc.png")
    plt.show()
```
```

Updates theta and theta0

Loads dataset

Maps to {+1,-1} labels

After running the algorithm, we get the classification accuracy results on the test dataset shown in figure 5.6.