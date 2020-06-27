# TensorFlow Models

This repository contains a number of different models implemented in [TensorFlow](https://www.tensorflow.org):

The [official models](official) are a collection of example models that use TensorFlow's high-level APIs. They are intended to be well-maintained, tested, and kept up to date with the latest stable TensorFlow API. They should also be reasonably optimized for fast performance while still being easy to read. We especially recommend newer TensorFlow users to start here.

The [research models](research) are a large collection of models implemented in TensorFlow by researchers. It is up to the individual researchers to maintain the models and/or provide support on issues and pull requests.

The [samples folder](samples) contains code snippets and smaller models that demonstrate features of TensorFlow, including code presented in various blog posts.

The [tutorials folder](tutorials) is a collection of models described in the [TensorFlow tutorials](https://www.tensorflow.org/tutorials/).

# Tensorflow Object Detection API for training 
- This is an minimized version of TF object detection API, aims for training models that can be used with Jetson-inference repo. Only custom SSD-mobilenet-v1 has been tested.

**Specs:**
- This code was taken from TF object detection API's commit f8e854b5566ad87834556e96aa4c038a5ebe94b8

**Pre-requirements:**
- CUDA 9.0, CUDNN 7.0
- Tensorflow-gpu version: 1.12.0 (conda install forge -c tensorflow-gpu==1.12.0)
- Other python libraries that required by API
- Testing eviroment to reproduce my result: docker 9.1-cudnn7-devel-ubuntu16.04 (python3.6). Pre-trained ssd-mobilenet-v1 model was put on ```train``` dir.

**How to complie:**
- From install dir, run following commands:
```
cd research
# On window platform, please use protoc.exe instead(which is included in this repository)
protoc object_detection/protos/*.proto --python_out=.
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim
python3 setup.py build
python3 setup.py install
cd slim
python3 setup.py build
python3 setup.py install
# Test everything is OK
python3 object_detection/builders/model_builder_test.py
```
**How to train**
- Please following TF Object Detection training tutorial

**How to get .uff model**
- Use (this)[https://github.com/AastaNV/TRT_object_detection] repository to generate uff file. 

