

```python
plot2.set_title('ROC Curve of ' + name, fontsize=12)
plot2.grid(True)
figure.tight_layout()
canvas.draw()
```

### 绘制真实值与预测值对比图及学习曲线

```python
def plot_real_pred_val_learning_curve(self, model, X_train, y_train, X_test, y_test, ypred, name, figure, canvas):
    figure.clear()

    # 绘制真实值与预测值对比图
    plot1 = figure.add_subplot(2, 1, 1)
    acc = accuracy_score(y_test, ypred)
    plot1.scatter(range(len(ypred)), ypred, color="blue", lw=3, label="Predicted")
    plot1.scatter(range(len(y_test)), y_test, color="red", label="Actual")
    plot1.set_title("Predicted Values vs True Values of " + name, fontsize=12)
    plot1.set_xlabel("Accuracy: " + str(round((acc * 100), 3)) + "%")
    plot1.legend()
    plot1.grid(True, alpha=0.75, lw=1, ls='-.')

    # 绘制学习曲线
    train_sizes = np.linspace(.1, 1.0, 5)
    train_sizes, train_scores, test_scores, fit_times, _ = learning_curve(
        model, X_train, y_train, cv=None, n_jobs=None, train_sizes=train_sizes, return_times=True
    )
    train_scores_mean = np.mean(train_scores, axis=1)
    train_scores_std = np.std(train_scores, axis=1)
    test_scores_mean = np.mean(test_scores, axis=1)
    test_scores_std = np.std(test_scores, axis=1)

    plot2 = figure.add_subplot(2, 1, 2)
    plot2.fill_between(train_sizes, train_scores_mean - train_scores_std,
                       train_scores_mean + train_scores_std, alpha=0.1, color="r")
    plot2.fill_between(train_sizes, test_scores_mean - test_scores_std,
                       test_scores_mean + test_scores_std, alpha=0.1, color="g")
    plot2.plot(train_sizes, train_scores_mean, 'o-', color="r", label="Training score")
    plot2.plot(train_sizes, test_scores_mean, 'o-', color="g", label="Cross-validation score")
    plot2.legend(loc="best")
    plot2.set_title("Learning curve of " + name, fontsize=12)
    plot2.set_xlabel("fit_times")
    plot2.set_ylabel("Score")
    plot2.grid(True, alpha=0.75, lw=1, ls='-.')

    figure.tight_layout()
    canvas.draw()
```

### 根据选择的模型绘制相关图表并显示结果表格

```python
def choose_plot_ML(self, root, chosen, X_train, X_test, y_train, y_test, figure1, canvas1, figure2, canvas2):
    if chosen == "Logistic Regression":
        best_model, y_pred = self.obj_ml.implement_LR(chosen, X_train, X_test, y_train, y_test)
        # 绘制混淆矩阵和 ROC 曲线
        self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
        # 绘制真实值与预测值对比图及学习曲线
        self.plot_real_pred_val_learning_curve(best_model, X_train, y_train, X_test, y_test, y_pred, chosen, figure2, canvas2)
        # 显示结果表格
        df_lr = self.obj_data.read_dataset("results_LR.csv")
        self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of Logistic Regression")

    elif chosen == "Random Forest":
        best_model, y_pred = self.obj_ml.implement_RF(chosen, X_train, X_test, y_train, y_test)
        self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
        self.plot_real_pred_val_learning_curve(best_model, X_train, y_train, X_test, y_test, y_pred, chosen, figure2, canvas2)
        df_lr = self.obj_data.read_dataset("results_RF.csv")
        self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of Random Forest")

    elif chosen == "K-Nearest Neighbors":
        best_model, y_pred = self.obj_ml.implement_KNN(chosen, X_train, X_test, y_train, y_test)
        self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
        self.plot_real_pred_val_learning_curve(best_model, X_train, y_train, X_test, y_test, y_pred, chosen, figure2, canvas2)
        df_lr = self.obj_data.read_dataset("results_KNN.csv")
        self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of KNN")

    elif chosen == "Decision Trees":
        best_model, y_pred = self.obj_ml.implement_DT(chosen, X_train, X_test, y_train, y_test)
        self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
        self.plot_real_pred_val_learning_curve(best_model, X_train, y_train, X_test, y_test, y_pred, chosen, figure2, canvas2)
        df_lr = self.obj_data.read_dataset("results_DT.csv")
        self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of Decision Trees")

    elif chosen == "Gradient Boosting":
        best_model, y_pred = self.obj_ml.implement_GB(chosen, X_train, X_test, y_train, y_test)
        self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
        self.plot_real_pred_val_learning_curve(best_model, X_train, y_train, X_test, y_test, y_pred, chosen, figure2, canvas2)
        df_lr = self.obj_data.read_dataset("results_GB.csv")
        self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of Gradient Boosting")

    elif chosen == "Extreme Gradient Boosting":
        best_model, y_pred = self.obj_ml.implement_XGB(chosen, X_train, X_test, y_train, y_test)
        self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
        self.plot_real_pred_val_learning_curve(best_model, X_train, y_train, X_test, y_test, y_pred, chosen, figure2, canvas2)
        df_lr = self.obj_data.read_dataset("results_XGB.csv")
        self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of Extreme Gradient Boosting")

    elif chosen == "Multi-Layer Perceptron":
        best_model, y_pred = self.obj_ml.implement_MLP(chosen, X_train, X_test, y_train, y_test)
        self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
        self.plot_real_pred_val_learning_curve(best_model, X_train, y_train, X_test, y_test, y_pred, chosen, figure2, canvas2)
        df_lr = self.obj_data.read_dataset("results_MLP.csv")
        self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of Multi-Layer Perceptron")

    elif chosen == "Support Vector Classifier":
        best_model, y_pred = self.obj_ml.implement_SVC(chosen, X_train, X_test, y_train, y_test)
        self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
        self.plot_real_pred_val_learning_curve(best_model, X_train, y_train, X_test, y_test, y_pred, chosen, figure2, canvas2)
        df_lr = self.obj_data.read_dataset("results_SVC.csv")
        self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of Support Vector Classifier")

    elif chosen == "AdaBoost":
        best_model, y_pred = self.obj_ml.implement_ADA(chosen, X_train, X_test, y_train, y_test)
        self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
        self.plot_real_pred_val_learning_curve(best_model, X_train, y_train, X_test, y_test, y_pred, chosen, figure2, canvas2)
        df_lr = self.obj_data.read_dataset("results_ADA.csv")
        self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of AdaBoost Classifier")
```

