#### ONNX运行时是一个跨平台的推理和训练加速器，兼容流行的ML/DNN框架，包括PyTorch、TensorFlow/Keras、scikit-learn等。
##### 你可以受益于ONNXruntime，如果你想:
* 提高多种ML模型的推理性能
* 减少训练大型模型的时间和成本
* Python训练，但是想要应用到C#/C++/java app中
* 在不同的硬件和操作系统上运行
* 使用在不同框架中创建的模型训练和执行推理

##### [ONNXruntime推理](https://microsoft.github.io/onnxruntime/docs/get-started/inference.html)api自2019年10月发布[1.0](https://github.com/microsoft/onnxruntime/releases/tag/v1.0.0)以来就很稳定，可以投入生产，可以提供更快的客户体验和更低的成本。 

##### [ONNXruntime training](https://microsoft.github.io/onnxruntime/docs/get-started/training.html)该功能是在2020年5月的预览版中引入的。该特性支持在transformer模型的多节点NVIDIA gpu上加速PyTorch训练。这个特性的其他更新很快就会发布。

#### Install ONNX Runtime
目录

**Prerequisites**
* Linux/CPU
* Linux/GPU
* Windows/CPU
* Windows/GPU

**Install**

使用本指南为您的目标操作系统、硬件、加速器和语言安装ONNX运行时及其依赖项。
有关概述，请参见此[安装矩阵](https://onnxruntime.ai/)。

**Prerequisites**
#### Linux/CPU
1. English language package with the en_US.UTF-8 locale
* [Install language-pack-en package](https://packages.ubuntu.com/search?keywords=language-pack-en)
* Run locale-gen en_US.UTF-8
* Run update-locale LANG=en_US.UTF-8
2. OpenMP
* apt-get install libgomp1, which installs libgomp.so.1
 


#### Linux/GPU
1. English language package with the en_US.UTF-8 locale
* [Install language-pack-en package](https://packages.ubuntu.com/search?keywords=language-pack-en)
* Run locale-gen en_US.UTF-8
* Run update-locale LANG=en_US.UTF-8
2. CUDA 10.1 and cuDNN 7.6.5
* 旧的ONNX运行时版本的版本依赖关系可以在[以前的版本说明](https://github.com/microsoft/onnxruntime/releases)中找到。
 

#### Windows/CPU
1.  English language package with the en_US.UTF-8 locale
2.  [Visual C++ 2019 runtime](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads)
3.  OpenMP
* 与Visual C运行时一起安装
* 也可以作为redist包[vc_redist.x64.exe](https://aka.ms/vs/16/release/vc_redist.x64.exe)和[vc_redist.x86.exe](https://aka.ms/vs/16/release/vc_redist.x86.exe)使用


Windows/GPU
1.  English language package with the en_US.UTF-8 locale
2.  [Visual C++ 2019 runtime](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads)
3.  CUDA 10.1 and cuDNN 7.6.5
* 旧的ONNX运行时版本的版本依赖关系可以在[以前的版本说明](https://github.com/microsoft
 

#### Install

* Default CPU Provider (Eigen + MLAS)
* GPU Provider - NVIDIA CUDA
* GPU Provider - DirectML (Windows)
* 在Windows上，建议使用[DirectML](https://github.com/microsoft/onnxruntime/tree/master/docs/execution_providers/DirectML-ExecutionProvider.md)执行提供程序来获得最佳性能和与广泛的gpu集的兼容性。

如果使用pip，运行pip install --upgrade pip 升级pip。


语言 | 官方build | 简洁build
---|---|---
Python | CPU [onnxruntime](https://pypi.org/project/onnxruntime) |  [ort_nightly(dev)](https://test.pypi.org/project/ort-nightly)
Python | GPU  [onnxruntime-gpu](https://pypi.org/project/onnxruntime-gpu)| [ort_gpu_nightly(dev)](https://test.pypi.org/project/ort-gpu-nightly)
C#/C/C++ | CPU [Microsoft.ML.OnnxRuntime](https://www.nuget.org/packages/Microsoft.ML.OnnxRuntime) |  [ort_nightly(dev)](https://aiinfra.visualstudio.com/PublicPackages/_packaging?_a=feed&feed=ORT-Nightly)
C#/C/C++ | GPU [Microsoft.ML.OnnxRuntime.gpu](https://www.nuget.org/packages/Microsoft.ML.OnnxRuntime.gpu) |  [ort_nightly(dev)](https://aiinfra.visualstudio.com/PublicPackages/_packaging?_a=feed&feed=ORT-Nightly)
Java | CPU [com.microsoft.onnxruntime/onnxruntime](https://search.maven.org/artifact/com.microsoft.onnxruntime/onnxruntime) |
Java | GPU [com.microsoft.onnxruntime/onnxruntime_gpu](https://search.maven.org/artifact/com.microsoft.onnxruntime/onnxruntime_gpu) |
略 | 略

**注意:从主分支创建的Dev构建可用于测试官方版本之间的更新更改。请自行承担风险。我们强烈建议不要将它们部署到生产工作负载中，因为对dev构建的支持是有限的。**

## ONNX Runtime Samples and Tutorials
https://github.com/microsoft/onnxruntime/tree/master/samples/#CC

## 基于C++的mnist数字识别
样本是Model Zoo中的mnist: https://github.com/onnx/models/tree/master/vision/classification/mnist


### 目录
#### Requirements
* Build
* How to use it
* How it works
* Preprocessing the data
* Postprocessing the output
* The Ort::Session

* Requirements
编译动态库 Onnxruntime.dll / lib (link to instructions on how to build dll) Windows Visual Studio Compiler (cl.exe)

* Build
运行当前目录中的 ‘build.bat’  调用 cl.exe 生成 MNIST.exe ，然后运行 MNIST.exe

* 如何使用
使用鼠标左键（或touch）在框中画一个数字，然后释放鼠标，模型即会运行并返回识别结果。请注意，当绘制数字需要多次绘制笔画时，模型将在每一笔画结束时运行，可能会出现错误的预测(但这很有趣，并避免了需要按下“运行模型”按钮)。


使用鼠标右键在任意位置点击即可清除图像。
To clear the image, click the right mouse button anywhere.

* 如何工作
How it works

* 创建一个全局的Ort::Env初始化运行环境
 https://github.com/microsoft/onnxruntime/blob/521dc757984fbf9770d0051997178fbb9565cd52/samples/c_cxx/MNIST/MNIST.cpp#L12

* MNIST结构体抽象了与Onnx runtime创建张量和运行模型的所有交互。

* WWinMain是Windows的入口点，它创建主窗口。
 
* WndProc是窗口的窗口程序，处理鼠标输入和绘制图形

* 数据预处理
MNIST的输入是{1,1,28,28}形状的 float tensor,它本质上是一个28x28的浮点灰度图像 (0.0 = background, 1.0 = foreground).

* 该示例将图像存储在每像素32位的windows DIB部分中，因为这便于为windows在屏幕上绘图。DIB就是在这里创建的 https://github.com/microsoft/onnxruntime/blob/521dc757984fbf9770d0051997178fbb9565cd52/samples/c_cxx/MNIST/MNIST.cpp#L109-L121

* 将DIB数据转换成模型输入张量的函数: https://github.com/microsoft/onnxruntime/blob/521dc757984fbf9770d0051997178fbb9565cd52/samples/c_cxx/MNIST/MNIST.cpp#L77-L92

* 后处理输出
* MNIST的输出是一个简单的{1,10}浮点张量，它包含每个数字的可能性权重。值最大的数是模型的最佳猜测

* mnist结构体使用 std::max_element去做这件事，然后将它存储在result_中: https://github.com/microsoft/onnxruntime/blob/521dc757984fbf9770d0051997178fbb9565cd52/samples/c_cxx/MNIST/MNIST.cpp#L31

* 为了让事情更有趣，窗口绘制处理程序将概率绘制成图表，并在这里显示权重:
https://github.com/microsoft/onnxruntime/blob/521dc757984fbf9770d0051997178fbb9565cd52/samples/c_cxx/MNIST/MNIST.cpp#L164-L183

* 创建 Ort::Session: Ort::Session 在mnist中这样被创建: https://github.com/microsoft/onnxruntime/blob/521dc757984fbf9770d0051997178fbb9565cd52/samples/c_cxx/MNIST/MNIST.cpp#L43

* 设置输入输出: 输入输出张量这样创建: https://github.com/microsoft/onnxruntime/blob/521dc757984fbf9770d0051997178fbb9565cd52/samples/c_cxx/MNIST/MNIST.cpp#L19-L23
在这种用法中，我们为数据提供内存位置，而不是让Ort分配缓冲区。在本例中，这更简单，因为缓冲区很小，只能是MNIST结构的固定成员。

运行: Run()方法中定义了如何运行: https://github.com/microsoft/onnxruntime/blob/521dc757984fbf9770d0051997178fbb9565cd52/samples/c_cxx/MNIST/MNIST.cpp#L25-L33


























