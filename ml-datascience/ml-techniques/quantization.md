# Quantization

A technique that **reduces the numerical precision** of a model's weights and activations. Typically, from FP32 to lower precision formats like FP16, INT8, or INT4.&#x20;

Benefits:

* Smaller model size
* Faster inference speed
* Lower power consumption

Problems:

* Accuracy loss
* Additional complexity



## 1. Post-training quantization

It happens once the model has been trained using full precision (FP32).

### 1.1. Dynamic quantization (or runtime quantization)

* Only weights are quantized.
* Activations are kept in FP32.
* At **runtime**, activations are quantized based on the range observed for each input batch.

Pros:

* No calibration data is needed

Cons:&#x20;

* This may imply a slight loss in accuracy



### 1.2. Static quantization

* Both weights and activations are quantized
* Uses a calibration process: with a small training/validation sample to observe the range of layer's activations. Normally INT8 is used

Pros:

* Faster due to INT8 precision
* Better accuracy

Cons:

* More complex process



## 2. Quantization-Aware Training

* The model simulates the quantization of weights and activations to help the model adapt to lower precisions.
* "Fake" quantized nodes are used for forward passes, but not in backpropagation.

Pros:

* High accuracy
* Robust

Cons:

* Complexity&#x20;
* Longer training time.
