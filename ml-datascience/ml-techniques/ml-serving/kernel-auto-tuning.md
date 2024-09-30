# Kernel Auto-Tuning

* It's a process to optimize deep-learning models by selecting the best-performing kernel.
* "Kernel" refers to a function that tuns on the GPU to compute efficiently, like:
  * Convolutions
  * Pooling
  * Activations
  * ....
* The performance of these functions can vary depending on
  * the model architecture,&#x20;
  * **input size**:  a kernel optimized for large matrix multiplications might be inefficient for smaller matrices due to memory access patterns.
  * **hardware architecture: d**ifferent NVIDIA GPUs have varying capabilities in terms of memory bandwidth, compute units, and support for certain operations.
  * **precision**: kernels tailored for FP16 or INT8 computations will generally run faster and use less memory than those designed for FP32
* So, Kernel Auto-Tuning will help to adapt each of these functions to the best kernel.



There are different tools available for this task: [NVIDIA TensorRT](https://developer.nvidia.com/tensorrt), [Apache TVM](https://tvm.apache.org/), [OpenXLA](https://openxla.org/xla), [OpenVINO](https://docs.openvino.ai/2024/index.html), [ONNX Runtime](https://onnxruntime.ai/) or [cuDNN](https://developer.nvidia.com/cudnn).

