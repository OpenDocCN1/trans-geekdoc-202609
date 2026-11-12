We analyze the performance of embedding-based pooling and instance-based pooling using synthetic bags on four benchmark datasets. Specifically, we evaluate four commonly used attention modules and two feature aggregators. Two strategies for generating bag labels from instance labels are examined. While our primary focus is instance-level classification, we also conduct additional experiments on bag-level tasks to assess the generality of the pooling models. The main experimental findings are summarized as follows: (1) instance-based pooling is more effective in instance classification tasks under the standard MIL assumption; (2) both pooling strategies exhibit comparable performance for instance classification under the collective MIL assumption; (3) for bag classification under the standard MIL assumption, embedding-based pooling is more effective.

In summary, our contributions are as follows:

+   - We introduce the instance-level graph multiple instance learning task for the first time, providing a deep exploration of the role of graph pooling in node-level tasks.
+   - We propose a straightforward and general transformation rule that converts embedding-based pooling models into instance-based models.
+   - We systematically analyze the key theoretical properties of embedding-based and instance-based models, including their permutation invariance, expressiveness and interpretability.
+   - We conduct extensive experiments on standard graph datasets across various MIL tasks, which offer valuable insights into the selection of pooling methods when handling graph structures at different levels.

# ## 2 Problem Formulation and Notations

Let \(\mathcal{G} = (\mathcal{V}, \mathcal{E})\) denote the input graph with node set \(\mathcal{V}\) and edge set \(\mathcal{E}\). \(\mathcal{V} = \{v_1, v_2, ..., v_n\}\), where \(n\) is the number of nodes. \(k\) denotes the number of classes. Nodes (called instances) are arranged in sets (called bags). Only bag labels are available during model training.

Let \(\mathcal{X}\) denote a bag consisting of \(m\) instances \(\{v_1, v_2, ..., v_m\}\). In MIL, bag label \(\mathcal{Y}\) is determined by unknown instance labels \(\{y_1, y_2, ..., y_m\}\) based on different assumptions. In this paper, the standard assumption [8] is mainly focused. Given a trigger class \(t \in \{1, 2, ..., k\}\), we refer to the nodes that belong to \(t\) as positive instances, and the other nodes as negative instances. The standard MIL assumption states that positive bags contain at least one positive instance, and negative bags contain only negative instances. Formally, \(\mathcal{Y}\) is determined by:

```
\(\mathcal{Y} = \left\{\begin{array}{ll} +1 & if \quad \exists y \in \{y_1, y_2, ..., y_m\}, y = t \\ -1 & if \quad \forall y \in \{y_1, y_2, ..., y_m\}, y \neq t \end{array}\right.\) (1)
```

Our target is then to learn an instance-level binary classifier to predict the label of nodes within the bags. Our work is useful in many real-world scenarios where it is desirable to detect instances that trigger the bag label, such as automating cancer diagnosis and grading.