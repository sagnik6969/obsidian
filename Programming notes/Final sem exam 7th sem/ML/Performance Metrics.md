<iframe width="560" height="315" src="https://www.youtube.com/embed/5vqk6HnITko?si=rVL7GYmX0IVMYWit" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
##  Confusion Matrix

- A table that summarizes the results of a classification model's predictions on a set of test data.
- a 2 X 2 matrix

**What it shows:**

- **True positives (TP):** Correctly predicted as positive.
- **True negatives (TN):** Correctly predicted as negative.
- **False positives (FP):** Incorrectly predicted as positive (also known as Type I error).
- **False negatives (FN):** Incorrectly predicted as negative (also known as Type II error).

**Example:**

![[Pasted image 20231213113356.png]]

### Accuracy
$$

Formula = (Tp + Tn) /  (Tp + Tn + Fp + Fn)

$$
### Precession
1. Used when dataset is imbalanced. For example suppose 90% of the dataset is true and 10% is false. Then if we output true for all cases we will get 90% accuracy. 
1. This is a common metric used in machine learning, especially for classification tasks. It measures the proportion of positive predictions that are actually correct. This can be calculated as follows:

$$
Precision = True Positives / (True Positives + False Positives)
$$
### Recall
1. Used in the same cases where precession is used
2. The choice between precession and recall depends upon specific application, Whether we want to reduce false positive or false negative.
$$
Recall = True Positives / (True Positives + False Negative)
$$
