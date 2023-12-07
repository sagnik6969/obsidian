- K nearest neighbours
- Simplest classification algorithm 
![[Pasted image 20231207130351.png]]![[Pasted image 20231207130447.png]]
**Step2 :** select K nearest neighbors. 
**Step 3 :** Majority voting (classification).

## K-Nearest Neighbors (KNN) Algorithm: Step-by-Step Breakdown

**KNN** is a simple yet powerful  machine learning algorithm used for both classification and regression tasks. It relies on the **principle of similarity**, where the label or value of a new data point is predicted based on its **nearest neighbors** in the training dataset.

**Here's a step-by-step breakdown of the KNN algorithm:**

**1. Training Phase:**
* **Store the entire training dataset.** This includes all data points with their corresponding labels or values. 
* **Choose a distance metric.** This determines how similar two data points are. Common distance metrics include Euclidean distance, Manhattan distance, and Hamming distance.

**2. Prediction Phase:** 
* **Present a new, unlabeled data point.**
* Find the K nearest neighbors to the new data point in the training dataset based on the chosen distance metric. 
* **Classification:** * 
* **For majority vote:** Determine the most frequent class among the K nearest neighbors. Assign the new data point to this class. 
* **For weighted vote:** Assign weights to the neighbors based on their distance to the new data point. Classify the new data point based on the weighted average of its neighbors' classes. 
* **Regression:** 
* **Calculate the average or weighted average of the values of the K nearest neighbors.** This average becomes the predicted value for the new data point.

**4. Evaluation:** * **Evaluate the performance of the KNN model using appropriate metrics.** Common metrics for classification include accuracy, precision, recall, and F1 score. For regression, the mean squared error (MSE) or the R-squared coefficient are typically used.

**Advantages of KNN:**

- Easy to implement and understand.
- No need for explicit training or feature engineering.
- Works well for both classification and regression tasks.

**Disadvantages of KNN:**

- Sensitive to irrelevant features and noisy data.
- High computational cost for large datasets.
- Can suffer from the curse of dimensionality.

