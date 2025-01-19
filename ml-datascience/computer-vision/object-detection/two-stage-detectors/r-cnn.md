# R-CNN

Compared to the generic traditional pipeline, the feature extraction is performed using a CNN. This way:

1. Selective Search produces 2,000 region proposals
2. The CNN model extracts a 4,096 vector for each region.
3. An SVM classifies the region into background or object classes.

<figure><img src="../../../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

**Drawbacks:**

1. Multi-stage model ->  cannot be trained end-2-end.
2. Uses disk caching of the extracted features -> exponential growth of disk usage.
3. Selective Search is slow.
4. The CNN is run on each independent region -> very slow
