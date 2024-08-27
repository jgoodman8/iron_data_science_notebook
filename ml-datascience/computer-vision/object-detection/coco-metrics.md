# Coco Metrics

{% content-ref url="../../frequent-questions/precision-vs-recall.md" %}
[precision-vs-recall.md](../../frequent-questions/precision-vs-recall.md)
{% endcontent-ref %}

{% hint style="info" %}
#### Summary of Key Concepts:

* **AP (Average Precision)**: Measures the model's precision across various IoU thresholds and object sizes.
* **AR (Average Recall)**: Measures how well the model can recall (find) all object instances, given a certain number of detections.
* **IoU (Intersection over Union)**: Indicates how much overlap exists between the predicted bounding box and the ground truth. Different IoU thresholds (e.g., 0.50 or 0.75) correspond to different degrees of overlap required for a correct detection.
{% endhint %}

## Average Precision Metrics

The metric reflects the average precision across all object catogories. Aside from the main AP metric, other metrics are performed to provide a better understanding of how the model performs:

* **For @IoU**: evaluation is performed across various IoU thresholds.
  * **bbox\_mAP**: is computed from 0.5 to 0.95 in steps of 0.05.
  * **bbox\_mAP\_50**:  at IoU = 0.5.
  * **bbox\_mAP\_75**: at IoU = 0.75.
* **For the bbox size**:
  * **bbox\_mAP\_s**: for small objects (with an area below 32² pixels).
  * **bbox\_mAP\_m**: for medium objects (with an area between 32² and 96² pixels inclusive).
  * **bbox\_mAP\_l**: for large objects (with an area above 96² pixels).

## Average Recall Metrics

**Captures the model's ability to find all objects, emphasizing the minimum amount of false negatives.**

* **bbox\_AR@100**: considering only up to 100 detections per image.
* **bbox\_AR@300**: considering up to 300 detections per image.
* **bbox\_AR@1000**: considering up to 1000 detections per image.
* **bbox\_AR\_s@1000**: considering up to 1000 small detections per image.
* **bbox\_AR\_m@1000**: considering up to 1000 medium detections per image.
* **bbox\_AR\_l@1000**: considering up to 1000 large detections per image.



