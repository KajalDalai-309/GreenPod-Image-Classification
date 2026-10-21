# GreenPod Labs Image Classification Assignment

## Included
- `GreenPod_Orange_Image_Classification.ipynb` — Google Colab notebook with dataset audit, HOG + SVM baseline, MobileNetV2 transfer learning, metrics, confusion matrices, sample prediction, and report generation.
- `README.md` — instructions.

## Important dataset mismatch
The provided archive `Orange Dataset.zip` contains classes `blackspot`, `canker`, `fresh`, and `grenning`, which indicates orange condition/disease classification. The assignment screenshot describes avocado ripening-stage classification. Verify the intended dataset with the recruiter/portal before submitting.

## Run
1. Upload `Orange Dataset.zip` to the root of your Google Drive as `Orange Dataset.zip`.
2. Open the notebook in Google Colab.
3. Choose Runtime → Change runtime type → T4 GPU (recommended).
4. Run all cells from top to bottom.
5. Check the generated metrics and report. Download the notebook with outputs and the generated `GreenPod_Assignment_Report.md`.

Do not invent or manually fill model scores; the notebook computes them from the actual dataset.
