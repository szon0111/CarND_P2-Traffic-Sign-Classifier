#**Project: Build a Traffic Sign Recognition Program**
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

Overview
---
Implement and train a convolutional neural network to classify traffic signs included in the [German Traffic Sign Dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset). Use validation sets, pooling, and dropout to choose a network architecture and improve performance.

Log
---
###2017/2/23:
 - Validation Accuracy: **91.7%**
 - Model: LeNet-5
 - Parameters: Epochs = 100, Batch size = 128, learn rate = 0.0005, mu = 0, sigma = 0.1 
 - Pre-processing: shuffling, grayscale conversion, normalization

###2017/2/24:
 - Validation Accuracy: **93.3%**
 - Model: LeNet-5
 - Parameters: Epochs = 100, Batch size = 128, learn rate = 0.0007, mu = 0, sigma = 0.1 
 - Pre-processing: shuffling, grayscale conversion, normalization

###2017/2/26:
 - Validation Accuracy: **94.8%**
 - Model: LeNet-5
 - Parameters: Epochs = 100, Batch size = 256, learn rate = 0.0005, mu = 0, sigma = 0.1, dropout = 0.75
 - Pre-processing: shuffling, grayscale conversion, normalization

###2017/2/26:
 - Validation Accuracy: **95.6%**
 - Model: LeNet-5
 - Parameters: Epochs = 100, Batch size = 256, learn rate = 0.0005, mu = 0, sigma = 0.1, dropout = 0.75
 - Pre-processing: shuffling, grayscale conversion, normalization
 - Data-augmentation: 4440 new images with random rotations (-20, 20) for classes less than 500 images

###2017/2/27:
- Validation Accuracy: **97.5%**
- Model: Modified LeNet-5 with 3 Convolution layers(3x3) + 3 Fully connected layers
- Parameters: Epochs = 80, Batch size = 256, learn rate = 0.0005, mu = 0, sigma = 0.1, dropout = 0.5
- Pre-processing: shuffling, grayscale conversion, normalization
- Data-augmentation: NONE

###2017/2/27:
- **Test Accuracy: 95.4%**
- Model: Modified LeNet-5 with 3 Convolution layers(3x3) + 3 Fully connected layers
- Parameters: Epochs = 80, Batch size = 256, learn rate = 0.0005, mu = 0, sigma = 0.1, dropout = 0.5
- Pre-processing: shuffling, grayscale conversion, normalization
- Data-augmentation: NONE
