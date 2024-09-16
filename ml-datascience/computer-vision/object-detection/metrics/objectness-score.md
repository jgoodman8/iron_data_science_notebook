# Objectness Score

{% hint style="info" %}
Understanding Objectness in Object Detection Models ([_Medium_](https://medium.com/@zhao.nathan/understanding-objectness-in-object-detection-models-5d8c9d032488))
{% endhint %}

### What is it?

It measures the probability of an object to exist in a proposed RoI.&#x20;

* High objectness -> image window likely contains an object

If an image has high objectness, we expect it to have:

* Uniqueness in the whole image
* Tight boundaries around the object
* Different appearance to its surroundings

### How is it computed

This score objectness score is given based on the **IoU or Intersection-over-Union**. The min value is 0 and the max is 1.

It's the ratio between:

* the area of intersection between the anchor box and the GT bbox&#x20;
* the area of the union of both boxes.
