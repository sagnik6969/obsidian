#### Definition:
It is a tree-structured learning technique that is used for classification as well as regression.
#### Types of nodes:
**Decision nodes :**  
o A test is performed to choose between two or more paths  
o The test is done based on the values of a feature or attribute of the instance  
**Leaf nodes :**  
o Indicates the class of an example  
o Value of the example, i.e., probability, score

> Goal is to construct the smallest decision tree possible
> Features of small decision tree is 1. Smaller no of nodes 2. smaller depth

> In each decision node we calculate the information gain for different attributes and choose the attribute with the highest information gain. This process continues until we reach a leaf node.

> To create the topmost node  Which attribute should be tested first. Algorithm determines the information gain for each candidate attribute. Outlook, Temperature, Humidity, Wind. Select that one with highest information gain.

> If all the outputs are same returner the output.
> If attribute set is empty return the most common output.
### Algorithm
https://www.youtube.com/watch?v=CWzpomtLqqs

### Entropy
###### Entropy: 
Measure of the uncertainty or randomness of a random variable of a random variable.
![[Pasted image 20231207095201.png]]
![[Pasted image 20231207095232.png]]
![[Pasted image 20231207095329.png]]
![[Pasted image 20231207095347.png]]
### Information Gain:
The expected reduction in Entropy  Caused by partitioning the examples according to this attribute.
![[Pasted image 20231207100209.png]]
