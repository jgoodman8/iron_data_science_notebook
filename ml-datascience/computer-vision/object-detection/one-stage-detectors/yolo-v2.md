# YOLO v2

* This updated version (2016) uses a CNN backbone called **Darknet-19**
  * a variant of the VGG with simple progressive convolution and pooling layers.
* **Anchor boxes** to determine the final bboxes.
* **Batch normalization** to improve accuracy and stability.
* **Multi-scale training**: training images at multiple scales and average predictions
