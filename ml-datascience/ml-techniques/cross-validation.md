# Cross-validation

{% hint style="info" %}
\_\_[_Scikit-Learn: Cross-validation: evaluating estimator performance_](https://scikit-learn.org/stable/modules/cross_validation.html)\_\_

\_\_[_A Gentle Introduction to k-fold Cross-Validation_](https://machinelearningmastery.com/k-fold-cross-validation/)

\_\_[_Why and how to Cross Validate a Model?_](https://towardsdatascience.com/why-and-how-to-cross-validate-a-model-d6424b45261f)
{% endhint %}

## Why is it needed?

Learning the parameters of a prediction function and testing it on the same data is a methodological mistake: a model that would just repeat the labels of the samples that it has just seen would have a perfect score but would **fail to predict** anything useful **on yet-unseen data**. This situation is called **overfitting**. To avoid it, it is common practice when performing a \(supervised\) machine learning experiment to hold out part of the available data as a test set X\_test, y\_test. Here is a flowchart of typical cross-validation workflow in model training. The best parameters can be determined by grid search techniques.

![](../../.gitbook/assets/image%20%28104%29.png)

## About the validation set

If we use a random train-test split into 70%-30% or 80%-20%, there is a possibility of high bias if we have limited data. If our data is huge and our test sample and train sample has the same distribution then this approach is acceptable.

If that's not the case, when evaluating different _hyperparameters_, there is still a r**isk of overfitting on the test set** because the parameters can be tweaked until the estimator performs optimally. This way, **knowledge about the test set can be “leaked” into the model**, and evaluation metrics no longer report on generalization performance.

To solve this problem, yet another part of the dataset can be held out as a so-called “validation set”: training proceeds on the training set, after which **evaluation is done on the validation set**, and when the experiment seems to be successful, **final evaluation can be done on the test set**.

## Cross-validation

However, by partitioning the available data into three sets, we **drastically reduce the number of samples which can be used for learning the model**, and the results can depend on a particular random choice for the pair of \(train, validation\) sets.

By applying [cross-validation](https://en.wikipedia.org/wiki/Cross-validation_%28statistics%29), a test set should still be held out for final evaluation, but the validation set is no longer needed when doing CV. In the basic approach, called _**k**_**-fold CV**, the training set is split into _k_ smaller sets \(other approaches are described below, but generally follow the same principles\). The following procedure is followed for each of the _k_ “folds”:

* a model is trained using k−1 of the folds as training data
* the resulting model is validated on the remaining part of the data \(i.e., it is used as a test set to compute a performance measure such as accuracy\)
* the performance measure reported by k-fold cross-validation is then the average of the values computed in the loop.

![](../../.gitbook/assets/image%20%28105%29.png)

{% hint style="success" %}
[Example](https://scikit-learn.org/stable/auto_examples/model_selection/plot_grid_search_digits.html) of parameter estimation using grid search with CV
{% endhint %}

### Stratified k-fold cross-validation

Similar to K-fold cross-validation, [Stratified K-fold](https://scikit-learn.org/stable/modules/cross_validation.html#stratified-k-fold) returns stratified folds. This is: while making the folds it maintains the percentage of samples for each class in every fold. So that model gets equally distributed data for training/validation folds.

### **Repeated K-Fold**

It repeats K-Fold n times. It can be used when one requires to run K-fold n times, producing different splits in each repetition.

### Leave One Out

[LOOCV](https://machinelearningmastery.com/loocv-for-evaluating-machine-learning-algorithms/) is a simple cross-validation: each learning set is created by taking all the samples except one, the test set being the sample left out. Thus, for samples, we have different training sets and different tests set. 

This cross-validation procedure does not waste much data as **only one sample is removed from the training set**. Thus, it's appropriate when you have a small dataset or when an accurate estimate of model performance is more important than the computational cost of the method.

* **Don’t Use LOOCV**: Large datasets or costly models to fit.
* **Use LOOCV**: Small datasets or when estimated model performance is critical.

{% hint style="info" %}
Related: [Leave P Out \(LPOCV\)](https://scikit-learn.org/stable/modules/cross_validation.html#leave-p-out-lpo)
{% endhint %}

