# Race Classification with YOLO and CNN Model

## Project Overview

This project aims to classify human faces into different race categories using a deep learning model based on the InceptionV3 architecture, combined with the YOLOv8 object detection model to detect faces in images. The workflow includes:
1. Detecting faces in an image using YOLOv8.
2. Cropping the detected face regions.
3. Classifying the race of each detected face using a pre-trained CNN model.

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Preprocessing](#preprocessing)
- [Model Architecture](#model-architecture)
- [Training](#training)
- [YOLO Object Detection](#yolo-object-detection)
- [Evaluation](#evaluation)

## Dataset

The project uses the FairFace dataset, which contains images labeled into different race categories:
- **White** (combined with Middle Eastern and Latino)
- **Black** (combined with Indian)
- **Asian**

### Dataset Structure
The dataset has been grouped into 4 main categories:
1. **White** (White, Middle Eastern, Latino)
2. **Black** (Black, Indian)
3. **Asian** (East Asian)

#### Example folder structure:
/train 
  /White
  /Black 
  /Asian
/val
  /White
  /Black
  /Asian

## Preprocessing

### Image Preprocessing:
- **Resizing**: All images were resized to 224x224 pixels.
- **Normalization**: Pixel values were normalized between 0 and 1.
- **Data Augmentation**: Augmentation techniques such as flipping and rotation were applied to the training dataset to increase generalization.

## Model Architecture

### InceptionV3-based CNN
- The race classification model was built using **InceptionV3** as a base model with pre-trained weights from ImageNet.
- The final layers of the model consist of a global average pooling layer, followed by a dense layer with 1024 units and a softmax activation for 3 output classes.

### YOLOv8 for Face Detection
- **YOLOv8** object detection was used to detect persons in an image. The model crops the detected regions and passes them to the race classifier for prediction.

## Training

- The model was trained on the **FairFace** dataset with the following specifications:
  - **Batch Size**: 32
  - **Image Size**: 224x224
  - **Optimizer**: Adam
  - **Loss Function**: Sparse Categorical Crossentropy
  - **Accuracy Achieved**: 83% (Initial model performance)

## YOLO Object Detection

**YOLOv8** detects faces in input images, and only the cropped faces are passed to the classifier. Some custom logic was added to filter out blurred images or low-quality detections using a confidence threshold.

## Evaluation

The model was evaluated on a validation dataset using:
- **Accuracy**: Primary metric for evaluating model performance.
- **Confusion Matrix**: Used to understand the distribution of misclassifications across different classes.









