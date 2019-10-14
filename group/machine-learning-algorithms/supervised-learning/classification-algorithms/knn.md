# kNN

## **How it works**

![](../../../../.gitbook/assets/image%20%2848%29.png)

For every unlabeled instance \(the ones to be classified\):

1. It measures the distance to every labeled sample.
2. It sorts the distances \(asc\) 
3. It selects the first k instances
4. It takes the class that appears the most times on the selected k instances.

