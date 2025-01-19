# Hyperparameter tuning

![](https://media.giphy.com/media/zZe6jL6FSQm08/giphy.gif)

## Model parameter vs model hyperparameter

Model **parameters are internal to the model** whose values **can be estimated from the data** and we are **often trying to estimate them as best as possible**.&#x20;

Whereas **hyperparameters** **are external to our model** and **cannot be directly learned from the regular training process**. These parameters express “higher-level” properties of the model such as its complexity or how fast it should learn. Hyperparameters are model-specific properties that are **‘fixed’ before you even train and test** your model on data.

## Finding hyperparameters

### **Grid Search**

It takes a **dictionary** of all of the **different hyperparameters** that you want to test, and then feeds all of the **different combinations through the algorithm** for you and then reports back to you which one had the highest accuracy. The disadvantage of this method is its high computational cost.

### Random Search

To avoid going through all the possible combinations, this method **evaluates&#x20;**_**n**_**&#x20;uniformly random points in the hyperparameter space**, and selects the one producing the best performance.

### Hand tunning

Well, this is adjusting the hyperparameters manually based on experience or deep knowledge of the data and the picked estimator.

