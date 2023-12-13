- Supervised learning
- Used in classification as well as regression
- Face detection
- Text Classification
- classifing images etc

> In case of logistic regression we create only one decision boundary. In case of svm we create 3 lines (1 hipper plane and 2 marginal planes) 
> Try to maximize distance between marginal planes.
> 

## Support Vector Machine Algorithm Explained in Steps:

**1. Data Representation:**

- Each data point is represented as a point in n-dimensional space, where n is the number of features.
- Each feature value corresponds to a specific coordinate.

**2. Choosing the Kernel Function:**

- The kernel function determines how the data is mapped to a higher-dimensional space.
- Essential for non linear decision boundery
- Common kernel functions include linear, polynomial, and radial basis function (RBF).

**3. Identifying Support Vectors:**

- Support vectors are the data points closest to the hyperplane.
- They have a significant impact on the position of the hyperplane and are responsible for its generalization.

**4. Solving the Optimization Problem:**

- The SVM algorithm searches for the optimal hyperplane that maximizes the margin between the classes. The margin refers to the distance between the hyperplane and the closest data points on either side, known as support vectors. These support vectors play a critical role in defining the decision boundary for classification.
- This is achieved by solving a mathematical optimization problem.

**5. Making Predictions:**

- New data points are classified by mapping them to the same high-dimensional space and calculating their distance to the hyperplane.
- The point is assigned to the class closest to the hyperplane.

