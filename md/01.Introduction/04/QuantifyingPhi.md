# **Quantifying Phi Family**

Model quantization refers to the process of mapping the parameters (such as weights and activation values) in a neural network model from a large value range (usually a continuous value range) to a smaller finite value range. This technology can reduce the size and computational complexity of the model and improve the operating efficiency of the model in resource-constrained environments such as mobile devices or embedded systems. Model quantization achieves compression by reducing the precision of parameters, but it also introduces a certain loss of precision. Therefore, in the quantization process, it is necessary to balance the model size, computational complexity, and precision. Common quantization methods include fixed-point quantization, floating-point quantization, etc. You can choose the appropriate quantization strategy according to the specific scenario and needs.

We hope to deploy GenAI model to edge devices and allow more devices to enter GenAI scenarios, such as mobile devices, AI PC/Copilot+PC, and traditional IoT devices. Through the quantization model, we can deploy it to different edge devices based on different devices. Combined with the model acceleration framework and quantization model provided by hardware manufacturers, we can build better SLM application scenarios.

In the quantization scenario, we have different precisions (INT4, INT8, FP16, FP32). The following is an explanation of the commonly used quantization precisions

### **INT4**

INT4 quantization is a radical quantization method that quantizes the weights and activation values ​​of the model into 4-bit integers. INT4 quantization usually results in a larger loss of precision due to the smaller representation range and lower precision. However, compared with INT8 quantization, INT4 quantization can further reduce the storage requirements and computational complexity of the model. It should be noted that INT4 quantization is relatively rare in practical applications, because too low accuracy may cause significant degradation in model performance. In addition, not all hardware supports INT4 operations, so hardware compatibility needs to be considered when choosing a quantization method.

### **INT8**

INT8 quantization is the process of converting a model’s weights and activations from floating point numbers to 8-bit integers. Although the numerical range represented by INT8 integers is smaller and less precise, it can significantly reduce storage and calculation requirements. In INT8 quantization, the weights and activation values ​​of the model go through a quantization process, including scaling and offset, to preserve the original floating point information as much as possible. During inference, these quantized values ​​will be dequantized back to floating point numbers for calculation, and then quantized back to INT8 for the next step. This method can provide sufficient accuracy in most applications while maintaining high computational efficiency.

### **FP16**

The FP16 format, that is, 16-bit floating point numbers (float16), reduces the memory footprint by half compared to 32-bit floating point numbers (float32), which has significant advantages in large-scale deep learning applications. The FP16 format allows loading larger models or processing more data within the same GPU memory limitations. As modern GPU hardware continues to support FP16 operations, using the FP16 format may also bring about improvements in computing speed. However, the FP16 format also has its inherent disadvantages, namely lower precision, which may lead to numerical instability or loss of precision in some cases.

### **FP32**

The FP32 format provides higher precision and can accurately represent a wide range of values. In scenarios where complex mathematical operations are performed or high-precision results are required, the FP32 format is preferred. However, high accuracy also means more memory usage and longer calculation time. For large-scale deep learning models, especially when there are many model parameters and a huge amount of data, the FP32 format may cause insufficient GPU memory or a decrease in inference speed.

On mobile devices or IoT devices, we can convert Phi-3.x models to INT4, while AI PC / Copilot PC can use higher precision such as INT8, FP16, FP 32.

At present, different hardware manufacturers have different frameworks to support generative models, such as Intel's OpenVINO, Qualcomm's QNN, Apple's MLX, and Nvidia's CUDA, etc., combined with model quantization to complete local deployment.

In terms of technology, we have different format support after quantization, such as PyTorch / Tensorflow format, GGUF, and ONNX. I have done a format comparison and application scenarios between GGUF and ONNX. Here I recommend the ONNX quantization format, which has good support from the model framework to the hardware. In this chapter, we will focus on ONNX Runtime for GenAI, OpenVINO, and Apple MLX to perform model quantization (if you have a better way, you can also give it to us by submitting PR)

**This chapter includes**

1. [Quantizing Phi-3.5 / 4 using llama.cpp](./UsingLlamacppQuantifyingPhi.md)

2. [Quantizing Phi-3.5 / 4 using Generative AI extensions for onnxruntime](./UsingORTGenAIQuantifyingPhi.md)

3. [Quantizing Phi-3.5 / 4 using Intel OpenVINO](./UsingIntelOpenVINOQuantifyingPhi.md)

4. [Quantizing Phi-3.5 / 4 using Apple MLX Framework](./UsingAppleMLXQuantifyingPhi.md)



