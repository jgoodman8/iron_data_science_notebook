# NMS

NMS or **non-maximum suppression** is a post-processing technique used in object detection to improve accuracy and efficiency.

### Why?

It's common to find multiple bboxes generated per object. Normally, they overlap or are at different locations, but they are trying to "detect" the same object.

So, it's used to identify and remove redundant bboxes.

### How?

It considers two factors:

* [objectness-score.md](../metrics/objectness-score.md "mention")
* [nms.md](nms.md "mention")

And it follows these steps:

1. **Order the bboxes** based on their **confidence** ratings.
2. The bbox with the **best confidence** rating should be chosen and **saved as a detection**.
3. Remove all bounding boxes that substantially overlap the chosen bounding box. A predetermined threshold value normally determines how much overlap there is.
4. Repeat steps 2–3 until no more bounding boxes remain.

### Applications

* [faster-r-cnn.md](../two-stage-detectors/faster-r-cnn.md "mention") incorporates NMS by using an RPN to generate the RoIs.
* [yolo.md](../one-stage-detectors/yolo.md "mention") family applies NMS at different grid cells and scales.
