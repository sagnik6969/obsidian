1. Used to solve the problem of overfitting.
2. We reduce no of dimensions or features.
3. Reduces the number of features retaining the most of the feature/information

### How PCA Works
1. It combines highly correlated features together to form a new set of features, smaller in size, called ‘Principal components’ that account for data with highest variance.
2. This method of combining features to form a new set of features is called Feature Extraction.
3. Feature extraction is for creating a new, smaller set of features that still captures most  of the useful information.
4. To put all this simply, just think of principal components as new axes that provide the best angle to see and evaluate the data, so that the differences between the observations are better visible.
5. Principal components are new variables that are constructed as linear combinations or mixtures of the initial variables.
6. These combinations are done in such a way that the new variables (i.e., principal components) are uncorrelated and most of the information within the initial variables is squeezed or compressed into the first components.
7. PCA tries to put maximum possible information in the first component, then maximum remaining information in the second and so on.
### Properties
1. No of PCs ≤ No of dimensions  
2. PC1 will have the largest variance  
3. PC2 will have the second largest variance and will be orthogonal to PC1  
4. PC3 will have the third largest variance and will be orthogonal to PC1 and PC2  
... and so on.

### Steps of principal component analysis


