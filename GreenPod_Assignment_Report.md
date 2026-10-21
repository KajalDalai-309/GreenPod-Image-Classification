# Image Classification Report — GreenPod Labs Assignment

## Dataset and scope
The provided archive is named `Orange Dataset.zip` and contains the classes: blackspot, canker, fresh, grenning.
This differs from the assignment brief shown in the supplied screenshot, which describes avocado ripening stages. Confirm that the correct dataset was supplied before submission.

Training images: 991  
Test images: 99  
Classes: 4  
Training class counts: {'blackspot': 184, 'canker': 179, 'fresh': 281, 'grenning': 347}

## Dataset quality, imbalance, and possible bias
Class counts are shown above and in the notebook. The training data may be imbalanced; the imbalance ratio (largest/smallest class) is 1.94. Image classification may also be affected by illumination, background, camera angle, fruit variety, and severity of visible symptoms. These are potential sources of bias and should be verified by inspecting representative examples. The dataset's origin and collection conditions are not documented in the archive, so demographic/geographic or capture-setting bias cannot be ruled out.

## Approaches
1. **HOG + SVM:** Histogram of Oriented Gradients captures local edge/shape patterns; an SVM separates the feature vectors. This is a relatively lightweight baseline and can work well when visual patterns are consistent.
2. **MobileNetV2 transfer learning:** A pretrained convolutional neural network extracts general visual features. A new classification head is trained on this dataset, followed by limited fine-tuning. This is suitable for small datasets but can overfit and requires more compute.

## Evaluation
Metrics below are computed from the provided test folder when this notebook is run.

| Model | Accuracy | Macro Precision | Macro Recall | Macro F1 |
|---|---:|---:|---:|---:|
| HOG + SVM | 85.86% | 84.45% | 84.47% | 84.39% |
| MobileNetV2 Transfer Learning | 91.92% | 92.19% | 90.91% | 90.74% |

**Selected model by macro F1:** MobileNetV2 Transfer Learning.  
MobileNetV2 achieved the higher macro F1-score on the provided test set. Transfer learning can reuse visual features learned from large image datasets, which may help when the labelled dataset is relatively small.

Macro-averaged metrics give each class equal weight, which is useful when class counts differ. The confusion matrices and per-class classification reports should be reviewed to identify classes that are often confused.

## Mandatory questions

### 1. In production, how would your model perform?
The notebook's test-set scores are a first estimate, not a guarantee of production performance. Real-world performance may be lower if images have different lighting, backgrounds, camera devices, fruit varieties, or disease severity than the training data. Before deployment, test on independently collected images, monitor per-class precision/recall and prediction confidence, and periodically review errors and drift. For an automated sorting line, uncertain predictions should be sent for human inspection rather than forcing a potentially unsafe classification.

### 2. What are the drawbacks of your model?
HOG + SVM relies on handcrafted visual features and may struggle with complex texture changes, unusual angles, occlusion, and background variation. MobileNetV2 is more computationally demanding, depends on pretrained weights, can overfit a small dataset, and may be sensitive to domain shift. Both models are limited by label quality and the representativeness of the supplied images. Test-set size is also modest, so scores have uncertainty.

### 3. If given more time, what would you improve?
- Confirm and document the intended target labels and dataset provenance.
- Collect more images across lighting, camera, background, fruit variety, and symptom severity.
- Use a stratified train/validation/test strategy and keep the test set untouched during tuning.
- Tune learning rate, augmentation, SVM parameters, and class weights using validation data.
- Inspect misclassified images, add explainability visualizations, and test calibration.
- Measure latency and memory on the intended production hardware; add human review for low-confidence predictions.

### 4. Where did you spend more time during the assignment?
The main effort was spent on preparing and auditing the image dataset, building two different approaches, and comparing their errors using class-wise metrics and confusion matrices. The aim was not just to maximize accuracy but to understand where each model fails and how suitable it is for real-world use.

## Reproducibility
Run all notebook cells in order. The table above is generated from actual model predictions; do not replace it with guessed results. Save the notebook with outputs after execution before submitting.
