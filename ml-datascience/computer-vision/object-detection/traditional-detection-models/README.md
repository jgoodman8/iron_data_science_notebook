# Traditional Detection Models

{% hint style="info" %}
_Faster R-CNN Explained  for Object Detection Tasks (_[_DigitalOcean_](https://www.digitalocean.com/community/tutorials/faster-r-cnn-explained-object-detection)_)_
{% endhint %}

Normally, the traditional detection pipeline follows three major tasks:

* **Region Proposal**: identify candidate regions potentially containing objects (> 2.000).
  * Selective Search
  * Edge Boxes
* **Feature Extraction**: fixed-length feature vector using image descriptors.
* **Classification**: to assign the background class or one of the object classes to detect.  Initially using an SVM classifier.

