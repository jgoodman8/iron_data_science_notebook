# Faster R-CNN

Main contributions with respect to [fast-r-cnn.md](fast-r-cnn.md "mention"),

1. **RPN or Region Proposal Network**: NN to generate proposals for different anchor boxes.
2. Uses **anchor boxes** (combination of scale and aspect ratio)
3. CNN weights are shared by the RPN and the Fast R-CNN.



The Faster R-CNN works as follows:

* The RPN generates region proposals. These regions are generated using a trainable network, that could be customized for each detection scenario. And uses the same convolutional layers used in the Fast R-CNN network.
* For all region proposals in the image, a fixed-length feature vector is extracted from each region using the [roi-pooling.md](../techniques/roi-pooling.md "mention")layer.
* The extracted feature vectors are then classified using the Fast R-CNN.
* The class scores of the detected objects in addition to their bounding-boxes are returned.

<figure><img src="../../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

### How are anchor boxes created?

The RPN works on the output feature map returned from the last convolutional layer shared with the Fast R-CNN. A sliding window of size _NxN_ passes through the feature map. For each window, several candidate region proposals are generated. These proposals are not the final proposals as they will be filtered based on their “objectness score”.

Normally, they are defined by two parameters. Combining these parameters we can obtain _K_ number of anchor boxes:

* Scale
* Aspect Ratio

For each window, _K_ proposals are generated and a feature vector of equal size is extracted. Then, it's fed into two FC layers:

* The _cls_ layer generates the **objectness score** for every region proposal as a binary classifier (background vs object).
* The _reg_ layer returns a 4-D vector with the bbox of the region.



Given the [objectness-score.md](../metrics/objectness-score.md "mention"), Faster R-CNN computes these two classes based on it:

<figure><img src="../../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>
