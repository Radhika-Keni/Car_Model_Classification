# Car_Model_Classification


## Objective of this notebook
- The purpose of this notebook is to build a Deep learning based car identification model that classifies the name/make of the car
- Details of the **problem statement**  , **data set** ,  **summary of the code/solution**  and **final result** of the project are listed in the sections to follow.

## Problem Statement 
Computer Vision can be used to automate supervision and generate action appropriate action trigger  if the event is predicted from the image of interest.
In this particular use case, we will be exploring how a car moving on the road can be easily identified by a camera by identifying the make of the car, type, color, number plates, etc.This could be very useful for monitoring criminal activity, identifying fake license plates, etc. It could also be useful in several other use-cases like identifying popularity of certain car types/make in certain geographies etc


## Data Description:
- Data Set:Stanford Car Data Set hosted by Kaggle
- The Cars dataset contains 16,185 images of 196 classes of cars. The data is split into 8,144 training images and 8,041 testing images, where each class has been split roughly in a 50-50 split. Classes are typically at the level of Make, Model, Year, e.g. 2012 Tesla Model S or 2012 BMW M3 coup
- Train Images: Consists of real images of cars as per the make and year of the car. 
- Test Images: Consists of real images of cars as per the make and year of the car. 
- Train Annotation: Consists of bounding box region for training images(Side Note :This notebook performs classification only  hence we will not use the bounding boxes in the model building process , however during the visualisation of the original data , we have displayed the labels with the bounding boxes in the  EDA file) 
- Test Annotation: Consists of bounding box region for testing images(Side Note :This notebook performs classification only hence we will not use the bounding boxes in the model building process , however during the visualisation of the original data , we have displayed the labels with the bounding boxes in the  EDA file) 

## Domain:
  Automotive Surveillance

## Summary of the Solution/Code:
The code aims at building a Custom CNN model.
- We begin by doing an Exploratory Data analyses and Visualisation on the images , refer **python worksheet EDA_And_Preprocessing.ipynb** 
- We then do the required pre-processing for the data . We augment the train data using albumentations library
- We also perform the data splits because we will not be using 16,000  images due to hardware constraints , we will perform a Train Data Split Size=6500 Records and Validation Data Split Size=1629 Records
- We then move on to Model building where we will build a Convolution Neural Network using a base skeleton of EfficientNet pre-trained on Image Net and rebuild the top layer.We use a cyclic learning rate , nestrov optimizer and img size as 224 as the hyper params . We train the model for 5 epochs and freeze the weights at this point.
- We then tune the params once again to an img_size of 300 , change the optimizer to lamb , unfreeze top 20 layers and re-train from the previous point for another 15 epochs in total
- The best model resulting from the above iterative process is chosen as the model refer **python worksheet  Classification_Model.ipynb**


## Result
- This model was able to obtain an accuracy of 0.7045 .Refer **python worksheet  Classification_Model.ipynb**

## References & Guidance
- PGP GL/UAT study material 
- Capstone Mentor guidance @ https://github.com/sheikmohdimran/Experiments_2021/blob/main/Vision
/Effnet_TF2_Albumentation.ipyn
