# Facial Detection and Augmentation with OpenCV

## Overview
In this project, we leveraged OpenCV's facial detection and image processing capabilities. Key steps included:
1. **Data Cleansing**: Used Pandas to filter out images with no faces or multiple faces, keeping only those with exactly one face from the `faces_meta_data.csv` file.
2. **Celebrity Selection**: Refined the dataset to focus on 14 specific celebrities listed in `celebs4face_detection.csv`, displaying two sample images for each.
3. **Dataset Creation**: Created a custom Dataset object, with methods returning both the celebrity label and the corresponding image, including five image augmentations to enhance model performance.
4. **Face Detection and Swapping**: Detected faces using OpenCV and implemented a function to swap faces between two images by adjusting bounding boxes and resizing the images for a seamless face swap.

---

## Project Overview
This project focuses on creating a pipeline for facial detection and augmentation using OpenCV, with applications in facial recognition and face swapping. The process includes data preprocessing, augmentation, and real-time face swapping functionality.

### Key Features
- **Data Cleansing**: Filter images with one face, based on detection scores.
- **Custom Dataset Object**: Dataset handling with integrated augmentation.
- **Augmentations**: Five types of image augmentations to improve facial recognition performance.
- **Face Detection**: Using OpenCV's pre-trained models for efficient and accurate face detection.
- **Face Swapping**: Swap faces between images with precise alignment and resizing.

---

## Project Breakdown

### 1. Load the Data
We used Pandas to load the metadata from `faces_meta_data.csv`, which includes:
- `photo_taken`: The year the photo was taken.
- `full_path`: The image path.
- `gender`: The gender of the celebrity.
- `name`: The celebrity's name.
- `face_score`: Face detection score (higher is better).
- `second_face_score`: Score of the second face, useful to filter out images with multiple faces.
- `celeb_id`: Celebrity index.

We cleaned the dataset by removing images without faces and those with multiple faces (i.e., with non-empty `second_face_score`).

### 2. Celebrity Filtering
We used the `celebs4face_detection.csv` file to filter our dataset, focusing on images of 14 specific celebrities.

### 3. Download the Images
The dataset was downloaded from the `imdb_crop` collection using the `wget` command. Some images were falsely tagged and manually removed.

---

## Dataset Object and Augmentations

### 1. Dataset Object
We created a custom `Dataset` object with the following outputs:
- **data**: The features of the images.
- **targets**: Labels corresponding to celebrities.
- **transforms**: Augmentations applied to each image.
- **image**: The transformed image.
- **label**: The celebrity label.

### 2. Image Augmentations
To increase the diversity and generalization of the model, we applied the following augmentations:
- **Blur**: Helps recognize faces with different focus levels.
- **Rotate**: Makes the model robust to different orientations.
- **Horizontal Flip**: Teaches the model to identify mirrored faces.
- **Random Brightness Contrast**: Helps the model recognize faces in various lighting conditions.
- **Gauss Noise**: Adds noise to simulate low-quality images and improve model robustness.

---

## Face Detection and Swapping

### 1. Face Detection
Using OpenCV's pre-trained models (like Haar Cascades or DNN), we implemented a reliable face detection mechanism. This pre-trained approach allowed us to focus on data preparation and augmentations, without requiring custom face detection model training.

### 2. Face Swapping
We implemented a face-swapping function that uses the detected faces, resizes them, and then swaps them between two images. This technique is widely used in applications like augmented reality and entertainment.
