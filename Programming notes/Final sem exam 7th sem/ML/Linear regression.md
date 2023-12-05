  
Linear regression is a statistical method used to model the relationship between a dependent variable and one or more independent variables by fitting a linear equation to the observed data. The goal is to find the best-fitting line that represents the relationship between the variables. This line is called the regression line.

Here's a detailed explanation of linear regression:

### Basic Equation:

In simple linear regression, with one independent variable, the equation of the regression line is given by:

`Y = bx + a`

where:

- Y is the dependent variable.
- X is the independent variable.
- β​ is the intercept (the value of Y when X is 0).
- a​ is the slope (the change in Y for a one-unit change in X).

### Objective:

The objective in linear regression is to find the values of b​ and a​ that minimize the sum of squared differences between the observed values (Yi​) and the values predicted by the regression line (Yi​) using `gradient decent algorithm`. This is often referred to as the least squares method.

![[Pasted image 20231206000457.png]]


### Example
Suppose the response vector y represents the sales of a product  
 `sales = advertising * badv + shops * bshop + price * bprice + a`  
The bias a represents the prediction baseline when all the features have  values of zero.
- Each b represents a numeric value that describes the intensity of the relationship to the  
response.

### Gradient decent algorithm / Iterative linear regression

1. Take decision on  
        a. 𝛼, the learning rate  
        b. 𝜖, the precision (threshold)  
        c. Stopping criterion
2. Initialize the weight vector 𝑤⃗⃗ (0) prior to the first iteration:  
        i. Usually initialized with 0’s or close to 0’s  
        OR  
        ii. May be done randomly
3. Improve 𝑤⃗⃗ by using: 𝑤⃗⃗ (𝑘+1) = 𝑤⃗⃗ (𝑘) − 𝛼∇𝑤⃗⃗ 𝐽(𝑘) in the 𝑘th iteration.
   ![[Pasted image 20231206002117.png]]
   ![[Pasted image 20231206002213.png]]


   4. If stopping criterion is met, stop. Otherwise, go to Step 3.
   ![[Pasted image 20231206002831.png]]
   


### Model Evaluation:

To assess how well the model fits the data, various metrics such as the coefficient of determination (R2) can be used. �2R2 measures the proportion of the variance in the dependent variable that is predictable from the independent variable(s).

### Assumptions of Linear Regression:

Linear regression makes several assumptions, including:

1. **Linearity:** The relationship between the variables is linear.
2. **Independence:** Observations are independent.
3. **Homoscedasticity:** Residuals have constant variance.
4. **Normality:** Residuals are normally distributed.
5. **No or little multicollinearity:** Independent variables are not highly correlated.

### Multiple Linear Regression:

Linear regression can be extended to multiple independent variables (features) with the equation:

![[Pasted image 20231205235006.png]]


### Practical Application:

Linear regression is widely used in various fields, including economics, finance, biology, and social sciences, to model and analyze relationships between variables.

In summary, linear regression is a powerful statistical tool for modeling and analyzing the relationship between variables, providing insights into the underlying patterns in the data and making predictions based on those patterns.