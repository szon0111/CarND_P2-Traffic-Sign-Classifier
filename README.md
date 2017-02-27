#**Project: Build a Traffic Sign Recognition Program**
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

Overview
---
In this project, you will use what you've learned about deep neural networks and convolutional neural networks to classify traffic signs. You will train and validate a model so it can classify traffic sign images using the [German Traffic Sign Dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset). After the model is trained, you will then try out your model on images of German traffic signs that you find on the web.

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
- Validation Accuracy: **98.2%**
- Model: LeNet-5 + 1 Convolutional layer + 1 Fully Connected layer
- Parameters: Epochs = 80, Batch size = 256, learn rate = 0.0005, mu = 0, sigma = 0.1, dropout = 0.5
- Pre-processing: shuffling, grayscale conversion, normalization
