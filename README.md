# Predicting-Age-from-Chest-X-Rays-Using-Deep-Learning

## Overview

This is an exploratory project to see if I could create a deep learning model that can predict a patient's age from chest X-ray images. I compare convolutional neural networks trained from scratch with pretrained computer vision models and investigate how model performance varies across patient groups and X-ray view positions.

The project uses Python and PyTorch to perform data preparation, model training, evaluation, and statistical analysis.

This is an experimental machine learning project to try and utilize what I have learned with many areas to improve. This is **not a medical tool**.


## Objectives

Explore and clean a publicly available chest X-ray dataset.

Develop CNN models for age classification and continuous age regression.

Compare different loss functions, optimizers, and model architectures.

Evaluate transfer learning using pretrained image recognition networks.

Compare model performance against simple baseline predictions.

Quantify uncertainty using patient-level bootstrap confidence intervals.

Investigate whether prediction errors differ between AP and PA X-ray views.

### Models Evaluated

The experiments include:

CNN-based age classification.

CNN regression using SmoothL1 loss.

CNN regression using L1 loss and AdamW.

A wider CNN regression model.

ImageNet-pretrained ConvNeXt-Tiny.

TorchXRayVision-pretrained DenseNet121.

The models are evaluated using a held-out test set, with model selection based on validation performance.


## Results

The best-performing model was ConvNeXt-Tiny, pretrained on ImageNet.

Model

Test MAE

### Training-median baseline

14.79 years

### CNN age classifier

15.66 years

### SmoothL1 regression

12.03 years

### L1 regression with AdamW

12.66 years

### Wider CNN

8.93 years

### ConvNeXt-Tiny

5.82 years

### TorchXRayVision DenseNet121

7.82 years

Mean absolute error (MAE) measures the average absolute difference between predicted and actual ages. Lower values indicate better predictions.

The ConvNeXt-Tiny model achieved a test MAE of approximately 5.82 years, compared with 14.79 years for the training-median baseline.

Its reported 95% patient-level bootstrap confidence interval was 5.45 – 6.22 years.

These results indicate that transfer learning substantially improved age prediction in this experiment. They do not guarantee similar performance on other datasets.

### Error Analysis and View-Position Investigation

I also investigated systematic prediction errors and differences between AP and PA X-ray views.

The analysis found that:

- Predictions tended to overestimate ages for younger patients and underestimate ages for older patients.

- AP and PA views had different test-set error distributions for some models.

These findings suggest that view position may be associated with prediction performance. They do not, by themselves, prove that view position causes the differences or that the models rely on it as a shortcut.

## Methodology

The project covers:

- Dataset inspection and exploratory data analysis.

- Age-label cleaning.

- Patient-level training, validation, and test splits.

- CNN training and model comparison.

- Transfer learning with pretrained architectures.

- Test-set MAE and baseline comparisons.

- Patient-level bootstrap confidence intervals.

- R-squared and Pearson correlation analysis.

- Error analysis by age group, sex, and view position.


## Tools and Technologies

- Python

- PyTorch

- Torchvision

- TorchXRayVision

- NumPy

- Pandas

- Matplotlib

- Jupyter Notebook


## Reproducibility

The notebook documents the experiments and their evaluation.

To reproduce the results, obtain the dataset (should just be able to run the code to obtain the dataset), install the required Python dependencies, and run the notebook. Each network code block has no dependencies but you will need to run the first few code blocks where we read/clean/partition the data. Training may require a GPU and a decent amount of time.

Exact reproduction may depend on the random seed and library version.


## Limitations

The results apply to the dataset and evaluation setup used in this project.

Performance on external datasets was not tested.

Predictions should be taken with a grain of salt due to small dataset size and dataset composition.

Associations between view position and model error do not establish causation, only some association.

The models in this project are intended for research and learning only.


## Acknowledgments

This project uses a publicly available chest X-ray dataset. Please consult the original dataset documentation for attribution, access conditions, and permitted uses.

AI assistance was used for coding and debugging, as disclosed in the notebook.
