# SORT

{% hint style="info" %}
Deep SORT Object Tracking Guide ([_Ikomia_](https://www.ikomia.ai/blog/deep-sort-object-tracking-guide))
{% endhint %}

The base of the [deep-sort.md](deep-sort.md "mention")algorithm, which adds deep-learning features.

1. It uses a detection-based approach to associate objects in consecutive frames
2. Then employs a Kalman filter to predict the future position of the objects and correct the association based on the actual measurements.
