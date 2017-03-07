#**Project: Build a Traffic Sign Recognition Program**
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

Overview
---
Implement and train a convolutional neural network to classify traffic signs included in the [German Traffic Sign Dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset). Use validation sets, pooling, and dropout to choose a network architecture and improve performance.

####The goals / steps of this project are the following:

* Load the data set
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report

Project Deliverables
---
* `Traffic_Sign_Classifier.ipynb` is the jupyter notebook with all codes
* `report.html` is the exported html file from the jupyter notebook with all code outputs
* `writeup.md` explains the project in depth with answers to some important questions

Data Collection
---
This project uses the [German Traffic Sign Dataset](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset). A few additional traffic sign images were collected from the web to test the model on new images. The dataset contains 51,839 images of 43 different traffic sign classes

Data Augmentation
---
Images with random rotations between -15 to 15 degrees were added for traffic sign classes that had less than 1,000 images to balance the distribution. However, the model did not use the augmented data at the end as the performance increase of less than 1% was not worth the heavy computing power.

Data Pre-processing
---
Images were grayscaled as the presence of colors did not help and converting RGB to a single channel significantly reduces the computing power needed. In fact, the model performed better in grayscale. Input images were normalized as well.

Model Architecture
---
The architecture is a modified form of LeNet-5 with 3 convolution layers and 3 fully connected layers. Dropouts with a keep probability of 0.5 were added to address overfitting.

Results
---
The model had a 95.4% accuracy on the test set and managed to identify all 6 new images from the web correctly.
