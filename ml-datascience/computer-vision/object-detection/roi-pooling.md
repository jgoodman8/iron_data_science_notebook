# ROI Pooling

{% hint style="info" %}
_Region of interest pooling explained (_[_deepsense.ai_](https://deepsense.ai/region-of-interest-pooling-explained/?ref=blog.paperspace.com)_)_
{% endhint %}

It's a NN layer taking two inputs:

* A fixed-size feature map from a CNN
* A N x 5 matrix of RoIs. With N = #RoI and 5 =  #bbox coordinates + the image index

### How does it work?

For every RoI, it takes the corresponding section of the feature map and scales it to a pre-defined size (eg 5x5). For it,

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>given a RoI proposed</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (4).png" alt="divide the RoI into equal-sized sections " width="375"><figcaption><p>divide the RoI into equal-sized sections</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>apply max-pooling on each section and append it to the output buffer </p></figcaption></figure>

Note: RoI size does not need to be multiple of the grid size (eg a 7x5 region can be divided into a 2x2)
