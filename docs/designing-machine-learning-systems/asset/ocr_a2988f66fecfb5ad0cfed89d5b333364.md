With regression tasks, label schema change could happen because of changes in the possible range of label values. Imagine you’re building a model to predict someone’s credit score. Originally, you used a credit score system that ranged from 300 to 850, but you switched to a new system that ranges from 250 to 900.

With classification tasks, label schema change could happen because you have new classes. For example, suppose you are building a model to diagnose diseases and there’s a new disease to diagnose. Classes can also become outdated or more fine-grained. Imagine that you’re in charge of a sentiment analysis model for tweets that mention your brand. Originally, your model predicted only three classes: POSITIVE, NEGATIVE, and NEUTRAL. However, your marketing department realized the most damaging tweets are the angry ones, so they wanted to break the NEGATIVE class into two classes: SAD and ANGRY. Instead of having three classes, your task now has four classes. When the number of classes changes, your model’s structure might change,29 and you might need to both relabel your data and retrain your model from scratch. Label schema change is especially common with high-cardinality tasks—tasks with a high number of classes—such as product or documentation categorization.

There’s no rule that says that only one type of shift should happen at one time. A model might suffer from multiple types of drift, which makes handling them a lot more difficult.

# Detecting Data Distribution Shifts

Data distribution shifts are only a problem if they cause your model’s performance to degrade. So the first idea might be to monitor your model’s accuracy-related metrics—accuracy, F1 score, recall, AUC-ROC, etc.—in production to see whether they have changed. “Change” here usually means “decrease,” but if my model’s accuracy suddenly goes up or fluctuates significantly for no reason that I’m aware of, I’d want to investigate.

Accuracy-related metrics work by comparing the model’s predictions to ground truth labels.30 During model development, you have access to labels, but in production, you don’t always have access to labels, and even if you do, labels will be delayed, as discussed in the section “Natural Labels” on page 91. Having access to labels within a reasonable time window will vastly help with giving you visibility into your model’s performance.

29 If you use a neural network using softmax as your last layer for your classification tax, the dimension of this softmax layer is [number_of_hidden_units × number_of_classes]. When the number of classes changes, the number of parameters in your softmax layer changes.

30 You don’t need ground truth labels if you use an unsupervised learning method, but the vast majority of applications today are supervised.