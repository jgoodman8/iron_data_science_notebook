# Intrinsic and extrinsic parameters

{% hint style="info" %}
What are Intrinsic and Extrinsic Camera Parameters in Computer Vision? ([_Aqeel Anwar_](https://towardsdatascience.com/what-are-intrinsic-and-extrinsic-camera-parameters-in-computer-vision-7071b72fb8ec))
{% endhint %}

These are parameters used for transforming the world into a 2D plane. More specificly, they are transformation matrices to convert points from one system to another.

<figure><img src="../../../.gitbook/assets/image (127).png" alt=""><figcaption></figcaption></figure>



## Extrinsic parameters

* Depends on the localization and orientation of the camera in the world coordinate system.
* They describe the transformation from the world coordinates to the camera's coordinate system.
*   They are:

    * **Rotation Matrix (R):**
      * A 3x3 matrix that represents the rotation of the camera in the world coordinate system. It describes how the camera's axes are oriented relative to the world's axes.
    *   **Translation Vector (t):**

        * A 3x1 vector that defines the camera's position in the world coordinate system. It describes the shift from the world's origin to the camera's origin.



    The extrinsic parameters are usually combined into a 3x4 matrix:

$$
E = [R | t]
$$

## Intrinsic parameters

* Properties of the camera itself and relate to how it captures images.
* The matrix transforms 3D world coordinates to the 2D image coordinates in the camera frame.
* These are some of the parameters:
  * **Focal length (f)**: distance between the camera's lens and the image sensor.
  * **Principal Point (c)**: point in the image where the optical axis intersects the image plane.
  * **Skew Coefficient (s):** angle between the x and y pixel axes.
  * **Distortion Coefficients**

The intrinsic parameters are typically represented in a 3x3 matrix:

$$
K = \begin{bmatrix} f_x & s & c_x \\ 0 & f_y & c_y \\ 0 & 0 & 1 \end{bmatrix}
$$

Where:

* f\_x​ and f\_y​ are the focal lengths along the x and y axes.
* s is the skew coefficient.
* (c\_x, c\_y) is the principal point.
