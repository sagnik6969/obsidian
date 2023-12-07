> Used for overcoming the problem of overfitting in decision tree.

> Multiple training datasets are created from from training datasets using random sampling method. The datasets are not distinct. For each data set a decision tree is created. the result is calculated by combining the result of all the decision trees. In case of classification majority voting is taken into account. In case of regression mean of the outputs is taken as result.


### Advantage of  Random forest over Decision tree 

**Reduced Overfitting:**
Decision trees are prone to overfitting, capturing noise in the training data and performing poorly on new, unseen data. Random Forests mitigate this issue by building multiple trees on different subsets of the data and then averaging or voting on the predictions. This ensemble averaging helps reduce overfitting.
=> Generalized very poorly to new unseen data.
**Increased Robustness:**
The random sampling of data and features during the construction of each tree in a Random Forest makes the model more robust. It is less sensitive to outliers and noisy data points, as the impact of individual data points is reduced by considering multiple trees.

**Improved Accuracy:**
Random Forests generally provide higher accuracy compared to individual decision trees. By aggregating predictions from multiple trees, the ensemble approach helps to reduce overfitting and variance, resulting in a more robust and accurate model.


### Bagging
is the process of sampling with replacement (sample drawn at random, are stored separately and its copy is put back to the dataset so that the dataset maintains its original size).

### Disadvantages:  
Random forests are slow in generating predictions due to multiple decision trees.


### Write the decision tree algo.
1. Why needed
2. Algo
3. How output is calculated
4. advantages
5. disadvantages
