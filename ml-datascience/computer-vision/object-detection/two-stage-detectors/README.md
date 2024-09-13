# Two-Stage detectors

This set of models needs two passes of the input image.

* The first pass to generate proposals of regions where objects possibly are
* The second pass is to refine proposals and generate predictions.

**PROS:**

* Normally, more accurate when compared to single-stage detectors
* Deal better with small objects

**CONS:**

* More computationally expensive
* Slower
