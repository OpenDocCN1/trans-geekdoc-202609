method. These statistics provide insights into the central tendency, dispersion, and shape of the data distribution.

+   Finally, the method displays the summary by invoking the show() method on the generated summary DataFrame.

+   In case the dataset is not loaded (i.e., self.data is None), the method prints a message indicating that the data is not loaded.

Step 8: count_outcome Method Definition

Here, we define the count_outcome method, which is part of the PimaDatasetExplorer class. This serves to tally the occurrences of each outcome value in the diabetes dataset:

```
```python
[In]: def count_outcome(self):
        """
        Counts the occurrences of each outcome value in the dataset.
        """
        if self.data is not None:
            print("Outcome Counts:")
            outcome_counts = self.data.filter(
                (col("Glucose") != 0)
                & (col("BloodPressure") != 0)
                & (col("BMI") != 0)
            ).groupBy("Outcome").count()
            outcome_counts.show()
        else:
            print("Data not loaded.")
```
```