# YOLOX

* Released in 2021, from the [yolo-v3.md](yolo-v3.md "mention") implementation
* **Anchor-free architecture**
* **Multi positives**: for compensating the large imbalance that the abserce of anchors produces, added center sampling with 3 x 3 areas as positives.
* &#x20;**Decoupled head:** separates classification confidence and localization accuracy into two heads (classification and regression).
* **Advanced label assignment:** to avoid the problem the GT label assignment could have ambiguities when the boxes of multiple objects overlap.
* **Strong augmentations**: uses MixUP and Mosaic, avoiding ImageNet pretraining.



### Center sampling

In anchor-free object detection models, predictions are typically made at various points (or pixels) on a feature map. During training, these models need to determine which points should be classified as positive samples (those belonging to an object) and which should be negatives (background). This selection process is crucial for learning accurate object localization and classification.

**Center sampling** focuses on assigning positive samples only to points that are closer to the center of an object's bounding box, rather than to every point within the bounding box. Here’s how it generally works:

1. **Bounding Box Center Region:** A region around the center of each object's bounding box is defined. This region is usually a smaller, central area of the entire bounding box. The size of this center region can be fixed or dynamically adjusted based on the size of the object.
2. **Sample Assignment:** During training, only the points (or pixels) within this center region are considered as potential positive samples for that object. Points outside this center region are considered negative, even if they lie within the bounding box. This reduces the ambiguity of sample selection and helps the model focus on more informative areas.
3. **Dynamic Sampling:** Some implementations of center sampling allow the size of the central region to adapt based on the size of the object. For example, the central region might be a fraction of the width and height of the bounding box, ensuring that the model can handle objects of various sizes.
