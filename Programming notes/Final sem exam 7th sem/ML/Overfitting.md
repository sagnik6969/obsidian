### Definition
Overfitting is a common problem in machine learning where a model learns the training data too well, including the noise or random fluctuations in the data, and as a result, it performs poorly on new, unseen data. In other words, the model fits the training data too closely and fails to generalize well to new, unseen examples.

![[Pasted image 20231206194337.png]]

![[Pasted image 20231206194600.png]]
### Reasons behind overfitting:
1. **Complex Models :** Models with a high degree of complexity, such as high-order polynomials or models with a large number of parameters, have a greater capacity to fit the training data precisely. While this can be beneficial to capture intricate patterns, it also increases the risk of fitting noise.
2.  **Limited Training Data :**  When the size of the training dataset is small, complex models may find it easier to memorize the data rather than generalize from it. Insufficient data may not adequately represent the underlying patterns in the broader population.
3. **Inclusion of Outliers or Irrelevant Features:** If the training data contains outliers or irrelevant features, the model may learn to fit these anomalies, leading to poor generalization. Noise in the data can mislead the model.

### Underfitting  
occurs when the model is too simple; both training and test errors are high.

### How to prevent overfitting ?
Preventing overfitting in machine learning involves employing various techniques and strategies to ensure that the model generalizes well to new, unseen data. Here are several approaches to prevent overfitting:

1. **Cross-Validation:**
    
    - Implement cross-validation techniques, such as k-fold cross-validation, to evaluate the model's performance on different subsets of the data. This helps assess how well the model generalizes to diverse datasets.
-![[Pasted image 20231206195958.png]]

1. **Regularization:**
    
    - Apply regularization techniques, such as L1 or L2 regularization, to penalize large coefficients or complex model structures. This discourages the model from fitting the training data too closely.
3. **Use Simpler Models:**
    
    - Choose simpler models with fewer parameters, especially when the amount of training data is limited. Less complex models are less prone to overfitting.
4. **Feature Engineering:**
    
    - Conduct thorough feature engineering to select relevant features and remove redundant or irrelevant ones. Feature engineering helps the model focus on the most informative aspects of the data.
5. **Increase Training Data:**
    
    - Provide a larger and more diverse training dataset. More data helps the model generalize better and reduces the risk of memorizing noise in smaller datasets.
6. **Early Stopping:**
    
    - Implement early stopping during training, where the training process halts once the model's performance on a validation set starts to degrade. This prevents the model from overfitting as it continues to train.
7. **Dropout (Neural Networks):**
    
    - For neural networks, use dropout during training. Dropout involves randomly deactivating some neurons during each training iteration, preventing the network from relying too heavily on any particular set of neurons.
