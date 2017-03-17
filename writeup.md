# **Traffic Sign Classifier - Report** 


**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report


[//]: # (Image References)

[image1]: ./examples/visualization.jpg "Visualization"
[image2]: ./examples/grayscale.jpg "Grayscaling"
[image3]: ./examples/random_noise.jpg "Random Noise"
[image4]: ./examples/placeholder.png "Traffic Sign 1"
[image5]: ./examples/placeholder.png "Traffic Sign 2"
[image6]: ./examples/placeholder.png "Traffic Sign 3"
[image7]: ./examples/placeholder.png "Traffic Sign 4"
[image8]: ./examples/placeholder.png "Traffic Sign 5"
[barchart]: https://cloud.githubusercontent.com/assets/10526591/23443677/c554d81c-fe73-11e6-800d-b4e08af69ccd.png
[ex_17]: https://cloud.githubusercontent.com/assets/10526591/23449466/00dd6e46-fe9a-11e6-9fe0-423c7ec87768.png
[ex_17_processed]: https://cloud.githubusercontent.com/assets/10526591/23449467/00fbc86e-fe9a-11e6-9d6e-9a8507f9bc0c.png
[ex_17_rotate]: https://cloud.githubusercontent.com/assets/10526591/23449468/0107eaea-fe9a-11e6-8601-26ab314aa991.png
[1]: https://cloud.githubusercontent.com/assets/10526591/23447853/125fbc22-fe91-11e6-93e1-10167aaebee3.PNG
[2]: https://cloud.githubusercontent.com/assets/10526591/23447854/12652130-fe91-11e6-8d52-e178abdfd9aa.PNG
[3]: https://cloud.githubusercontent.com/assets/10526591/23447855/126a5fd8-fe91-11e6-9e39-e4aef0db86f1.PNG
[4]: https://cloud.githubusercontent.com/assets/10526591/23463157/ec8c9068-fed3-11e6-8f0f-213271c90b90.png
[5]: https://cloud.githubusercontent.com/assets/10526591/23447851/12217eee-fe91-11e6-918d-e2bfb293b455.png
[6]: https://cloud.githubusercontent.com/assets/10526591/23447852/124efdc4-fe91-11e6-8482-7fd9d0f5d248.PNG
[softmax_13]: https://cloud.githubusercontent.com/assets/10526591/23463515/29689ae4-fed5-11e6-9823-8a38db707a29.png
[softmax_25]: https://cloud.githubusercontent.com/assets/10526591/23463516/296ca1c0-fed5-11e6-86ea-f4f8ae1be7ff.png
[softmax_36]: https://cloud.githubusercontent.com/assets/10526591/23463518/296e72ac-fed5-11e6-9717-5e622bb7dcb4.png
[softmax_1]: https://cloud.githubusercontent.com/assets/10526591/23463520/29753056-fed5-11e6-97bf-e53acc66e0ae.png
[softmax_3]: https://cloud.githubusercontent.com/assets/10526591/23463517/296e0312-fed5-11e6-9815-888e0b569343.png
[softmax_12]: https://cloud.githubusercontent.com/assets/10526591/23463519/29712d30-fed5-11e6-8d3c-c0fb34096613.png
[wild]: https://cloud.githubusercontent.com/assets/10526591/23448814/8b391ed6-fe96-11e6-976b-331fe1e0b368.png


---
*Here is my [project code](https://github.com/szon0111/CarND_P2-Traffic-Sign-Classifier/blob/master/Traffic_Sign_Classifier.ipynb) in jupyter notebook*

### Data Set Summary & Exploration

#### 1. Provide a basic summary of the data set and identify where in your code the summary was done. In the code, the analysis should be done using python, numpy and/or pandas methods rather than hardcoding results manually.

The code for this step is contained in the second code cell of the Jupyter notebook.  

I used the numpy library to calculate summary statistics of the traffic
signs data set:

* The size of training set: 34799
* The size of validation set: 4410
* The size of test set: 12630
* The shape of a traffic sign image: 32x32x3 
* The number of unique classes/labels in the data set: 43

#### 2. Include an exploratory visualization of the dataset and identify where the code is in your code file.

The code for this step is contained in cell 6 of the Jupyter notebook.  

Here is an exploratory visualization of the data set. It is a bar chart showing the distribution of the 43 traffic sign classes.
![bar][barchart]

We can see that the distribution is uneven with many classes that are underrepresented.

### Design and Test a Model Architecture

#### 1. Describe how, and identify where in your code, you preprocessed the image data. What techniques were chosen and why did you choose these techniques? Consider including images showing the output of each preprocessing technique. Pre-processing refers to techniques such as converting to grayscale, normalization, etc.

The code for this step is contained in cells 12 through 15 of the jupyter notebook.

As a first step, I decided to convert the images to grayscale because the inclusion of color did not improve the model performance. In fact, the model performed better in grayscale and lower dimension of the images helped train the model faster.

Here is an example of a traffic sign image before and after grayscaling.

![ex_17][ex_17]
![ex_17_processed][ex_17_processed]

As a last step, I normalized the image data in order to prevent my gradient from going out control in such wide pixel range. This will help avoid my model getting stuck in local minima when I use a single, global learning rate.

#### 2. Describe how, and identify where in your code, you set up training, validation and testing data. How much data was in each set? Explain what techniques were used to split the data into these sets. (OPTIONAL: As described in the "Stand Out Suggestions" part of the rubric, if you generated additional data for training, describe why you decided to generate additional data, how you generated the data, identify where in your code, and provide example images of the additional data)

The images were loaded from pickled data divided into training, validation, and testing data. The number of images were 34799, 4410, and 12630, respectively. 

Code cell 9 contains the code for augmenting the data set. I decided to generate additional data because many classes are significantly under-represented as seen in the distriution plot above. To add more data to the the data set, I added images with random rotations between -15 and 15 degrees to the classes that have less than 1000 images each.

Here is an example of an original image and an augmented image:

![ex_17][ex_17]
![ex_17_rotate][ex_17_rotate]

As a result, 16891 images were added, increasing the training data size to 51690 images.
HOWEVER, I ended up not using the augmented data set as the increase in validation and test accuracy was less than a percent, which is not worth all the computation, time, and additional data.
I plan on revisiting my model later on to try other data augmentation methods such as adding random noise and adjusting brightness, etc.

#### 3. Describe, and identify where in your code, what your final model architecture looks like including model type, layers, layer sizes, connectivity, etc.) Consider including a diagram and/or table describing the final model.

The code for my final model is located in the seventh cell of the Jupyter notebook. 

My final model consisted of the following layers:

| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x1 grayscale image   							| 
| Convolution 3x3     	| 1x1 stride, valid padding, outputs 28x28x6 	|
| Max pooling	      	| 2x2 stride,  outputs 14x14x6 				|
| RELU					|												|
| Convolution 3x3	    | 1x1 stride, valid padding, outputs 10x10x16 	|
| Convolution 3x3	    | 1x1 stride, valid padding, outputs 6x6x64 	|
| Dropout | keep_prob = 0.5  |
| Max pooling	      	| 2x2 stride,  outputs 3x3x64 				|
| RELU					|												|
| Flattening       | outputs 576 |
| Fully connected		| outputs 240        									|
| Dropout | keep_prob = 0.5  |
| RELU					|												|
| Fully connected		| outputs 168        									|
| Dropout | keep_prob = 0.5  |
| RELU					|												|
| Fully connected		| outputs 84        									|
| Dropout | keep_prob = 0.5  |
| RELU					|												|
| Softmax				| outputs 43      									|
 


#### 4. Describe how, and identify where in your code, you trained your model. The discussion can include the type of optimizer, the batch size, number of epochs and any hyperparameters such as learning rate.

For the model, I used the adam optimizer with a batch size of 256, 80 epochs, learning rate of 0.0005, and keep probability of 0.5
I played with various hyperparemeters and analyzed the results by plotting the loss and accuracy results. I fine tuned my parameters to come up with the final values that would not overfit or underfit the data.

#### 5. Describe the approach taken for finding a solution. Include in the discussion the results on the training, validation and test sets and where in the code these were calculated. Your approach may have been an iterative process, in which case, outline the steps you took to get to the final solution and why you chose those steps. Perhaps your solution involved an already well known implementation or architecture. In this case, discuss why you think the architecture is suitable for the current problem.

My final model results were:
* Training set accuracy: 99.9% 
* Validation set accuracy: 97.5%
* Test set accuracy: 95.4%

I started out by implementing the original Lenet-5 architecture. The Lenet-5 architecture works well with classification in images because it starts with simpler features and moves on to classify more complex features as the input goes through the layers. Also, concepts such as parameter sharinga and pooling reduce the size of data and computation, thus allowing faster training with relatively good results. More efficient networks such as Alexnet, GoogLenet, Densenet, etc have been introduced in recent years but I wanted to try improving on the original Lenet-5 architecture myself.
I started with grayscale conversion, normalization, and shuffling of the dataset, which resulted in around 91.7% validation accuracry. Ajusting some of the hyperparameters brought that up to 93.3% but the model showed overfitting soon as the validation accuracy was significantly lower than training accuracy. This issue could not be solved simply by adjusting the hyperparameters. 
Adding dropout immediately improved the validation accuracy to 94.6% and the random disconnections of networks helped reduce overfitting.
Adding some augmented data produced from random rotations did improve the accuracy but not by much. This is where the model showed its limitation as adjusting hyperparemets nor adding even more augmented data could improve the validation accuracy.
Deepening the model seemed to be the reasonable move and indeed, the addition of one convolution layer and one full connected layer improved the accuracy drastically. After some fine-tuning, the model achieved 97.5% accuracy even without any augmented data.

 

### Test a Model on New Images

#### 1. Choose at least five German traffic signs found on the web and provide them in the report. For each image, discuss what quality or qualities might be difficult to classify.

Here are six German traffic signs that I found on the web:

![sign][1] ![sign2][2] ![sign3][3] 
![sign4][4] ![sign5][5] ![sign6][6]

I expect the model to have a hard time classifying the fourth sign, which is for "road work", due to the presence of other signs on the edges.

#### 2. Discuss the model's predictions on these new traffic signs and compare the results to predicting on the test set. Identify where in your code predictions were made. At a minimum, discuss what the predictions were, the accuracy on these new predictions, and compare the accuracy to the accuracy on the test set.

The code for making predictions on my final model is located in the tenth cell of the Jupyter notebook.

Here are the results of the prediction:

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| 13, Yield      		| 13   									| 
| 1, Speed Limit 30     			| 1 										|
| 3, Speed Limit 60					| 3											|
| 25, Road Work	      		| 25					 				|
| 36, Go Straight or Right			| 36      							|
| 12, Priority Road			| 12      							|

The model was able to correctly guess all 6 traffic signs, which gives an accuracy of 100%, including the fourth sign that I was worried about. This compares favorably to the accuracy on the original test set.

#### 3. Describe how certain the model is when predicting on each of the six new images by looking at the softmax probabilities for each prediction and identify where in your code softmax probabilities were outputted. Provide the top 5 softmax probabilities for each image along with the sign type of each probability.

![softmax_13][softmax_13]
![softmax_1][softmax_1]
![softmax_3][softmax_3]
![softmax_25][softmax_25]
![softmax_36][softmax_36]
![softmax_12][softmax_12]

As seen from the results above, the model had no problem identifying all six images with high confidence including the fourth one with partial view of two other signs.

Log
---
### 2017/2/23:
 - Validation Accuracy: **91.7%**
 - Model: LeNet-5
 - Parameters: Epochs = 100, Batch size = 128, learn rate = 0.0005, mu = 0, sigma = 0.1 
 - Pre-processing: shuffling, grayscale conversion, normalization

### 2017/2/24:
 - Validation Accuracy: **93.3%**
 - Model: LeNet-5
 - Parameters: Epochs = 100, Batch size = 128, learn rate = 0.0007, mu = 0, sigma = 0.1 
 - Pre-processing: shuffling, grayscale conversion, normalization

### 2017/2/26:
 - Validation Accuracy: **94.8%**
 - Model: LeNet-5
 - Parameters: Epochs = 100, Batch size = 256, learn rate = 0.0005, mu = 0, sigma = 0.1, dropout = 0.75
 - Pre-processing: shuffling, grayscale conversion, normalization

### 2017/2/26:
 - Validation Accuracy: **95.6%**
 - Model: LeNet-5
 - Parameters: Epochs = 100, Batch size = 256, learn rate = 0.0005, mu = 0, sigma = 0.1, dropout = 0.75
 - Pre-processing: shuffling, grayscale conversion, normalization
 - Data-augmentation: 4440 new images with random rotations (-20, 20) for classes less than 500 images

### 2017/2/27:
- Validation Accuracy: **97.5%**
- Model: Modified LeNet-5 with 3 Convolution layers(3x3) + 3 Fully connected layers
- Parameters: Epochs = 80, Batch size = 256, learn rate = 0.0005, mu = 0, sigma = 0.1, dropout = 0.5
- Pre-processing: shuffling, grayscale conversion, normalization
- Data-augmentation: NONE

### 2017/2/27:
- **Test Accuracy: 95.4%**
- Model: Modified LeNet-5 with 3 Convolution layers(3x3) + 3 Fully connected layers
- Parameters: Epochs = 80, Batch size = 256, learn rate = 0.0005, mu = 0, sigma = 0.1, dropout = 0.5
- Pre-processing: shuffling, grayscale conversion, normalization
- Data-augmentation: NONE
