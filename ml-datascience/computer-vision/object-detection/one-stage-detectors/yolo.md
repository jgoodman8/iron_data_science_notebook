# YOLO

{% hint style="info" %}
YOLO: Algorithm for Object Detection Explained \[+Examples] ([_V7Labs_](https://www.v7labs.com/blog/yolo-object-detection))

A comprehensive review of YOLO architectures in Computer Vision: From YOLOV1 to YOLOV8 and YOLO-NAS ([_arXiv_](https://arxiv.org/pdf/2304.00501))
{% endhint %}

You Only Look Once (YOLO) achieved SoTA results in real-time detectors in 2015. A family of detectors emerged since then:

<figure><img src="../../../../.gitbook/assets/image (1).png" alt="" width="375"><figcaption></figcaption></figure>

The YOLO architecture is simple:&#x20;

* 24 convolutional layers and two end FC layers.
* The first 20 layers are pre-trained on Imagenet with half-resolution images
* Then it's trained on detection with full-resolution images

<figure><img src="../../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

* YOLO divides the input image into a S × S grid&#x20;
* and predicts B bounding boxes of the same class, along with its confidence for C different classes per grid element
* Each bbox prediction consists of five values: Pc, bx, by, bh, bw (Pc is the confidence score)
* Uses 1 × 1 Conv layers to reduce the number of feature maps and keep the #parameters relatively low
* The output of YOLO is a tensor of _S × S × (B × 5 +C)_ optionally followed by non-maximum suppression (NMS) to remove duplicate detections.&#x20;
* In the original YOLO paper, the authors used&#x20;
  * the PASCAL VOC dataset that contains 20 classes (C = 20)
  * a grid of 7 × 7 (S = 7)
  * and at most 2 classes per grid element (B = 2)

<figure><img src="../../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

* YOLO uses **NMS** (non-maximum suppression) to improve accuracy.&#x20;

### Pros & Cons

* Much faster than the existing object detectors allowing real-time performance.
* However, the localization error was larger compared to SOTA methods such as Fast R-CNN.
  * It could only detect at most two objects of the same class in the grid cell, limiting its ability to predict nearby objects.
  * It struggled to predict objects with aspect ratios not seen in the training data.&#x20;
  * It learned from coarse object features due to the down-sampling layers.

