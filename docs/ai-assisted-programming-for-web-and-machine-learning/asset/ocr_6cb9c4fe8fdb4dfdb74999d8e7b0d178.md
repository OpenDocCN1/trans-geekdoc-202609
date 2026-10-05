The following code applies k-means clustering to segment customers and visualizes the groups in a 2D scatter plot:

```
# Assume df includes 'Annual Income' and 'Spending Score'
from sklearn.cluster import KMeans
import seaborn as sns
import matplotlib.pyplot as plt
X_customer = df['Annual Income', 'Spending Score']
kmeans = KMeans(n_clusters=4)
df['Segment'] = kmeans.predict(X_customer)
sns.scatterplot(x='Annual Income', y='Spending Score', hue='Segment', palette='Set1')
plt.show()
```

This scatter plot reveals how customers are grouped, making it easy to identify segments like high-income frequent spenders or budget-conscious buyers.

# AI assistance

AI tools like GitHub Copilot and ChatGPT streamline both the implementation and interpretation of customer segmentation:

+   **GitHub Copilot:** GitHub Copilot improves code clarity and organization by recommending meaningful variable names and intuitive labels based on data context:
    * Intelligently suggests variable names like **X_customer** based on column headers such as **'Annual Income'** and **'Spending Score'**.
    * Autocomplete column assignments and proposes intuitive new labels like **'Segment'** or **'Customer_Type'**.

+   **ChatGPT:** ChatGPT extends support beyond coding by offering guidance on interpreting clustering results in a