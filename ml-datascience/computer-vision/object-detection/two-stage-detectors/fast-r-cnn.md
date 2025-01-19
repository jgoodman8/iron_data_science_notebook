# Fast R-CNN

Improvements w.r.t. [r-cnn.md](r-cnn.md "mention")are:

1. **ROI Pooling**: to extract an equal-length vector from all the proposed regions
2. **Single stage model**
3. Shares the CNN layers across all regions, thanks to the ROI Pooling.
4. No disk caching
5. Higher accuracy

<figure><img src="../../../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

The feature map from the last convolutional layer is fed to an ROI Pooling layer to extract a fixed-length vector from each region. ROI Pooling splits the region in a grid and applies **max pooling** on each cell.

For further info, check the [roi-pooling.md](../techniques/roi-pooling.md "mention") section.



The ROI Pooling output is fed into a FC layer that splits into two branches:

1. **Softmax layer** to predict class scores
2. **FC layer** with a regression head to predict bounding boxes

**Drawbacks**

* Depends on Selective Search -> very slow
