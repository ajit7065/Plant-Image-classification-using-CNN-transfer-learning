A self case study in deep learning based computer vision. Transfer Learning with VGG16, ResNet50 and MobileNet.

The Dataset
The dataset can be obtained from Kaggle : https://www.kaggle.com/competitions/plant-seedlings-classification/overview
This Data contains around 5545 images of size 150x150 distributed under 12 categories.
The categories are:
Black-grass
Charlock
Cleavers
Common Chickweed
Common wheat
Fat Hen
Loose Silky-bent
Maize
Scentless Mayweed
Shepherd's Purse
Small-flowered Cranesbill
Sugar beet

The Train, Test and Prediction data is separated . There are around 3319 images in Train, 794 in Test and 1431 in validation.
The Train and validation images are grouped in folders according to their classes and hence ImageDataGenerated gets hold of their class labels.
The images from test folder are used for validation during training.
Prediction images are not grouped in folders according to their classes and hence we can not calculate test accuracy using these images.
Prediction images are used to check predictions on individual images.
All images are of size 150 x 150.
The problem statement
Its a multiclass classification problem with six classes in Intel image scene dataset.

Preprocessing
Different preprocessing is done for different models

Data Augmentation is used for VGG16, Inception and mobileNet.
For ResNet50 the in built preprocessing provided by tf.keras.applications.resnet.preprocess_input is used.
The Data Augmentation, when used, is applied only to train set and not to validation and test set.
Rescaling to 1/255 is done for all sets
Batch sizes used 10 for all models.

Modeling
Cusomized CNN model used as once of model to train
Pretrained models having imagenet weights are used with transfer learning.
Modeling is done with VGG16, ResNet50 and MobileNet.
All the layers except last few layers of the model are frozen.
The top layer of the model is not used. Instead, a dense layer with 6 units and softmax activation is used.
VGG16 took the longest to train while mobileNet is the quickest.
Results
Accuracy and loss plots along with Confusion matrix is plotted for all models.
Validation accuracies are as follows
Customized CNN - 89%
VGG16 - 89.13%
Inception_V3 - 85.8%
ResNet50 - 82%
mobileNet - 91%
MobileNet is best in all aspects (Accuracy,Precision,Recall)
