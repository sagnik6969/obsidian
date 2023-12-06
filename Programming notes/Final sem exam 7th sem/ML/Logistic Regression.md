1. An extension of the linear regression model useful for classification problems  
2. Maps the probabilities into two possible outcomes which is to be used in binary classification
### Problems with linear regression:
1. The linear regression model can work well for regression, but fails for classification.  
2. A linear model treats the classes as numbers (0 and 1) and fits the best hyperplane (for a single feature, it is a line) that minimizes the distances between the points and the hyperplane (or line).
3. So it simply interpolates between the points, and this interpolation cannot be interpreted as probabilities.  
4. Since the predicted outcome is not a probability, but a linear interpolation between points, there is no meaningful threshold at which one can distinguish one class from the other. 
5. A linear model also extrapolates and gives you values below zero and above one.  
### Logistic Regression  
1. A solution for classification leads to logistic regression.  
2. Instead of fitting a straight line or hyperplane, the logistic regression model uses the logistic function to squeeze the output of a linear equation between 0 and 1.  The logistic function is defined as:  The dependent variable y is transformed to logistic(y). Here it is 𝜂.  
4. 𝑙𝑜𝑔𝑖𝑠𝑡𝑖𝑐(𝜂) = 1  / 1 + 𝑒𝑥𝑝(−𝜂) = 1 / 1 + exp(-(bx + a))

![[Pasted image 20231206173316.png]]
![[Pasted image 20231206173502.png]]
![[Pasted image 20231206173826.png]]
