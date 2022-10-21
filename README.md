<h1 align="left"> Deep learning approaches for depth-map prediction in fringe projection profilometry. </h1>

### This is the main repository of the DL4CV course project *developed by Fernando Quintero*.

In this project we propose the implementation of variants of the classic U-Net to train a model to make depth map (Z-coordinate) predictions given a single shot of a fringe image. These variants include Attention U-Net, U-Net plus plus, and R2-U-Net, etc. The purpose of this implementation is to analyze the performance of these network architectures and then make a comparison of the evaluation metrics for linear activation outputs including MSE and RMS.

#### **Table of Contents**
[1. Import the required libraries.](#implibraries)
<br/>[2. Loading the CIFAR10 images database.](#loadcifar)
<br/>[3. Compile the model and training (with Batch Normalization).](#trainingmodel)
<br/>[4. Compile the model and training (without Batch Normalization).](#trainingmodelnoBN)
<br/>[5. Comparison of two trained models.](#modelscomparison)
<br/>[6. Implementing learning rate schedulers.](#lrschedule) 
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[*6.1. Without learning rate schedule.*](#nolrschedule)
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[*6.2. Step-based Decay.*](#stepdecay)
<br/>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[*6.3. Custom learning-rate.*](#customlr)
<br/>[7. Predictions with selected trained model.](#predictions)

### 1. About the dataset.

- **H. Nguyen, Y. Wang, and Z. Wang, “Single-Shot 3D Shape Reconstruction Using Structured Light and Deep Convolutional Neural Networks” Sensors 20(13), 3718, 2020.
https://figshare.com/articles/dataset/Single-shot_3D_shape_reconstruction_datasets/7636697 CC BY 4.0**

| Feature       | Value      |
|---------------|------------|
| Image width   | 640 px     |
| Image height  | 480 px     |
| Data type     | Float32    |
| Train data    | 600 images |
| Test data     | 48 images  |

### 2. model.
| `keras_unet_collection.models` | Name | Reference |
|:---------------|:----------------|:----------------|
| `unet_2d`      | U-net           | [Ronneberger et al. (2015)](https://link.springer.com/chapter/10.1007/978-3-319-24574-4_28) |
| `vnet_2d`      | V-net (modified for 2-d inputs) | [Milletari et al. (2016)](https://arxiv.org/abs/1606.04797) |
| `unet_plus_2d` | U-net++         | [Zhou et al. (2018)](https://link.springer.com/chapter/10.1007/978-3-030-00889-5_1) |
| `r2_unet_2d`   | R2U-Net         | [Alom et al. (2018)](https://arxiv.org/abs/1802.06955) |
| `att_unet_2d`  | Attention U-net | [Oktay et al. (2018)](https://arxiv.org/abs/1804.03999) |
| `resunet_a_2d` | ResUnet-a       | [Diakogiannis et al. (2020)](https://doi.org/10.1016/j.isprsjprs.2020.01.013) |
| `u2net_2d`     | U^2-Net         | [Qin et al. (2020)](https://arxiv.org/abs/2005.09007) |
| `unet_3plus_2d` | UNET 3+        | [Huang et al. (2020)](https://arxiv.org/abs/2004.08790) |
| `transunet_2d` | TransUNET       | [Chen et al. (2021)](https://arxiv.org/abs/2102.04306) |
| `swin_unet_2d` | Swin-UNET       | [Hu et al. (2021)](https://arxiv.org/abs/2105.05537) |
 
 
### 2. Dependencies
<a href="https://www.blender.org/" target="_blank" rel="noreferrer"> <img src="https://download.blender.org/branding/community/blender_community_badge_white.svg" alt="blender" width="40" height="40"/> </a><a href="https://www.python.org" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a><a href="https://opencv.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/opencv/opencv-icon.svg" alt="opencv" width="40" height="40"/> </a><a href="https://numpy.org/" target="_blank" rel="noreferrer"> <img src="https://cdn.worldvectorlogo.com/logos/numpy-1.svg" alt="numpy" width="38" height="38"/> </a><a href="https://opencv.org/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/opencv/opencv-icon.svg" alt="opencv" width="40" height="40"/> </a>

- [TensorFlow 2.5.0](https://www.tensorflow.org/)
- [Keras 2.5.0](https://keras.io/)
- [Python3](https://www.python.org/)
- [NumPy](https://numpy.org/)
- [OpenCV](https://opencv.org/)
- [Blender](https://www.blender.org/) 
