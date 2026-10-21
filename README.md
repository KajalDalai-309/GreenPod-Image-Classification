# GreenPod Labs – Image Classification Assignment

## Overview
This project compares two image classification approaches on the provided orange image dataset.

## Dataset
The dataset contains four classes:
- Blackspot
- Canker
- Fresh
- Grenning

The dataset includes training and testing images.

**Note:** The supplied dataset contains orange classes, while the assignment brief refers to avocado ripening stages. This discrepancy should be confirmed with the recruiter.

## Models Implemented
1. **HOG + SVM** – A classical computer vision approach.
2. **MobileNetV2** – A deep learning approach using transfer learning.

## Results

| Model | Test Accuracy |
|---|---:|
| HOG + SVM | 85.86% |
| MobileNetV2 | 91.92% |

MobileNetV2 achieved the higher test accuracy in this experiment.

## Files
- `GreenPod_Orange_Image_Classification.ipynb` – Notebook containing the workflow and model evaluation.
- `GreenPod_Assignment_Report.md` – Assignment report and responses to the required questions.

## How to Run
Open the notebook in Google Colab, upload the dataset in the expected location, and run the cells in order.

## Tools and Technologies
Python, TensorFlow/Keras, OpenCV/image processing, scikit-learn, NumPy, Pandas, Matplotlib.
