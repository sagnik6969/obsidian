- In case of random forests decision trees are parallelly connected
- in case of boosting techniques decision trees are sequentially connected.

![[Pasted image 20231214173419.png]]

- These d trees are weak learners
- DT1 keeps correctly predicted outputs with itself and wrongly predicted outputs are forwarded to dt2.
- Same is for dt2.
- When we combine the decision trees it becomes strong learner.
- Weak learners => haven't learnt much from the training dataset.
- In random forest majority of output is considered as ans. in boosting weight (considence) is associated with each weak learners..
![[Pasted image 20231214174143.png]]

### Ada boost
- If the depth of a decision tree is 1 then it is called decision tree stump.
![[Pasted image 20231214174731.png]]
- We assign a sample weight to each record.
![[Pasted image 20231214174912.png]]
- 7 is the no of recored
- 
Lasso regression
regfit
bagging
