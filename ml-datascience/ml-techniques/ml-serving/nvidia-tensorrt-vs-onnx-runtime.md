# NVIDIA TensorRT vs ONNX Runtime

## TL;DR

* **ONNX Runtime** is a versatile, hardware-agnostic inference engine with support for multiple execution providers, making it suitable for various deployment environments beyond NVIDIA hardware. It focuses on general-purpose optimization and cross-platform compatibility.
* **NVIDIA TensorRT** is a specialized inference engine for NVIDIA GPUs, offering advanced, GPU-specific optimizations that maximize performance, especially for low-latency and real-time applications.

## [NVIDIA TensorRT](https://developer.nvidia.com/tensorrt)

It's a high-performance deep learning inference SDK specifically optimized for NVIDIA GPUs. It is tailored for maximum efficiency on NVIDIA hardware and offers deep integration with CUDA and cuDNN libraries to extract the best possible performance from GPU resources.

These are the main features:

1. NVIDIA Hardware-Specific and CUDA support.
2. Layer and Kernel Auto-Tuning ([kernel-auto-tuning.md](kernel-auto-tuning.md "mention"))
3. [quantization.md](quantization.md "mention")
4. Tensor Memory management: allocates memory on GPU only when needed. This allows for more available GPU memory and bigger batch sizes.

## [ONNX Runtime](https://onnxruntime.ai/)

It's an open-source inference engine that executes models in the **Open Neural Network Exchange (ONNX)** format. It's designed to be hardware-agnostic, allowing models to be deployed across various hardware platforms such as CPUs, GPUs, FPGAs, and specialized accelerators.

Main features:

1. Hardware-Agnostic
2. Model flexibility (TensorFlow, PyTorch, Keras, MXNet ...)
3. Graph optimizations like constant folding, operator fusion, and dead node elimination.
4. [quantization.md](quantization.md "mention")
5. Dynamic input shapes

## Comparison of features

<table data-full-width="true"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td><strong>Features</strong></td><td><strong>ONNX Runtime</strong></td><td><strong>NVIDIA TensorRT</strong></td></tr><tr><td><strong>Hardware Support</strong></td><td>Multi-platform: CPUs, NVIDIA GPUs, Intel hardware, FPGAs, custom accelerators.</td><td>NVIDIA GPUs only</td></tr><tr><td><strong>Execution Providers</strong></td><td>CUDA, TensorRT, OpenVINO, DirectML, etc.</td><td>CUDA and TensorRT for NVIDIA GPUs.</td></tr><tr><td><strong>Model Format</strong></td><td>Supports ONNX models (from TensorFlow, PyTorch, Keras, etc)</td><td>TensorFlow, PyTorch, ONNX, Caffe. Converts them to TensorRT's format.</td></tr><tr><td><strong>Optimization Techniques</strong></td><td>Graph optimizations, and basic kernel auto-tuning (depending on the execution provider).</td><td>Advanced kernel auto-tuning, mixed-precision, and INT8 quantization.</td></tr><tr><td><strong>Precision Support</strong></td><td>Supports FP32, FP16, and INT8 quantization.</td><td>Optimized support for FP16 and INT8 with extensive calibration tools.</td></tr><tr><td><strong>Dynamic Shapes</strong></td><td>Natively supports dynamic input sizes and batch dimensions.</td><td>Supports dynamic shapes but requires explicit optimization during engine building.</td></tr><tr><td><strong>Use Case Flexibility</strong></td><td>Suitable for a wide range of hardware and model types, adaptable to various deployment environments.</td><td>Best for high-performance, low-latency applications on NVIDIA GPUs.</td></tr><tr><td><strong>Ease of Use</strong></td><td>More flexible; integrates with different backends using execution providers.</td><td>More complex; requires NVIDIA GPU-specific setup and optimizations.</td></tr></tbody></table>

