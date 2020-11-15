# Image-Classification-with-Deep-Learning

This project makes a model to analyze chest X-ray images of children in age 1 to 5, and predicts Whether they have normal or Pneumonia lung.


## Directory Structure

### [Reference](https://github.com/aligodspeed/Image-Classification-with-Deep-Learning/tree/main/Reference%20)
This folder contains outside reference that we used for extra information during our project.

### [img](https://github.com/aligodspeed/Image-Classification-with-Deep-Learning/tree/main/img)
This folder contains images and visualizations of our project.

### [notebooks](https://github.com/aligodspeed/Image-Classification-with-Deep-Learning/tree/main/notebooks)
This folder contains jupyter notebooks with eda data analyses and our final report notebook. 

### [reports](https://github.com/aligodspeed/Image-Classification-with-Deep-Learning/tree/main/reports)
This folder contains a non-technical presentation pdf file.

### [src](https://github.com/aligodspeed/Image-Classification-with-Deep-Learning/tree/main/src)
This folder contains the source code for created functions for use during this project.

### [README](https://github.com/aligodspeed/Image-Classification-with-Deep-Learning/blob/main/README.md)
This folder contains a brief explanation of the project.

## Overview and Business Question.
In this notebook, we got our dataset form Kaggle. Our dataset is over 5000 images of X-ray chest from childern. This dataset has 3 different folders train, test and val. every folder contains subfolders Normal and Pneumonia which included X-ray images. The Pneumonia subfolder has 2 different type of images. These images are X_ray from people with Pneumonia from Bacteria and Virus.

Pneumonia images are different than Normal images while Pneumonia images are distinguished from each other too. With these differentiations, we can make model to find the pattern between images, and use that pattern to predict and recognize other future images.

The Business problem is that False Negative predictions. Like other medical cases, false negatives are really important. False negatives are predictions of Normal X-ray while they are Pneumonia. This become really dangerous when we say people that they are not sick, but they are.

Our goal here is to make model with lower False Negativ and higher metrics scores.

## Understanding of some concepts 
[Pneumonia ](https://github.com/aligodspeed/Image-Classification-with-Deep-Learning/blob/main/img/pneu.jpg)
What is Pneumonia ?
Pneumonia is an infection that inflames the air sacs in one or both lungs. The air sacs may fill with fluid or pus (purulent material), causing cough with phlegm or pus, fever, chills, and difficulty breathing. A variety of organisms, including bacteria and viruses can cause pneumonia.

Pneumonia can range in seriousness from mild to life-threatening. It is most serious for infants and young children, people older than age 65, and people with health problems or weakened immune systems.

## Data
The [chest_xray](https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia) data is provided by Kaggle. We don't import data into the repo, because it was huge file which will make trouble during uploading into the repo. This data is available for public to download. The dataset already splits to three folders test, train and validation. Each folder has 2 Subfolders which are Normal and Pneumonia. Inside of these folders there are chest-Xrays of peopel with diagnosed of Pneumonia and peopel with Normal lung.

## Data Preperation/Exploration
This datset is already clean and since we only work with images, we don't need preperation for data. But, after loading and craeting the first simple model, we saw a strange behavior on graph from validation accuracy and validation loss. This unusual behavior is caused by the number of validation folders. In the otiginal folders, there are only 16 images inisde the folder and this is causing a Roller coasters behavior from validation accuracy and validation loss.
I added equal number of images into both Pneumonia and Normal folders. Then make new simple model. Also, I used data Augmentation to dealing with Imbalance data.

## Model
In this project we used convolutional neural network(CNN) for deep learning and image classification. For the first model, I only used input, flatten and output layer.Then, I changed epochs and steps to get better result. None of the results from simple CNN models were meet our expectations.
To Improve my model and getting better results, I created model with more layers (4 Conv2D, 4Maxxpooling2D, 1flatten and 2Dense layers). This new model gave me better result and accuracy score, but not good enough to say this is my final model.

A problem with training neural networks is in the choice of the number of training epochs to use as you can see in the last model.
Too many epochs can lead to overfitting of the training dataset, whereas too few may result in an underfit model. Early stopping is a method that allows you to specify an arbitrary large number of training epochs and stop training once the model performance stops improving on a hold out validation dataset.

I added early stop and I got %83 accuracy, and good other scores. All info is [here](https://github.com/aligodspeed/Image-Classification-with-Deep-Learning/blob/main/notebooks/final_notebook/final_notebook.ipynb)
