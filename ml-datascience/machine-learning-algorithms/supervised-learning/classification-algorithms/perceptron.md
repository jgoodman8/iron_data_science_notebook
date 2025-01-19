# Perceptron

* It's the foundation of MLP and Deep Learning
* Each input value has a related weight and a bias value is added:

$$
z^{[i]} := b + \sum_{j=1}^n x_j^{[i]} * w_j \rightarrow 1\ if\ z^{[i]} > 0; 0\ otherwise
$$

<figure><img src="../../../../.gitbook/assets/image (7).png" alt="" width="505"><figcaption></figcaption></figure>

* To update the weights iteratively, we compute the errors on each iteration:

$$
error := y^{[i]} - ŷ^{[i]} \\
w_j := w_j + error * x_j^{[i]}
$$

* Only capable of classifying using a linear boundary

<figure><img src="../../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>



