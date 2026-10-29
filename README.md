# Colon Histopathology Classification and Explainable AI

This project examined how deep learning models classified benign and cancerous colon tissue images from the LC25000 dataset. I compared a baseline CNN with EfficientNetB3 and ConvNeXt-Tiny, then used Grad-CAM++ to explore which image regions influenced their predictions.

## Project workflow

1. **[Data preparation and EDA](notebooks/01-colon-histopathology-eda-portfolio.ipynb)** — I examined duplicate and visually similar images before creating group-aware training, validation, and test partitions. After removing 475 exact duplicate files, 9,525 images remained.
2. **[Model training and evaluation](notebooks/02-colon-histopathology-training-portfolio.ipynb)** — I trained and compared a baseline CNN, EfficientNetB3, and ConvNeXt-Tiny on the prepared dataset.
3. **[Explainable AI](notebooks/03-colon-histopathology-xai-portfolio.ipynb)** — I generated Grad-CAM++ explanations and examined changes in prediction confidence using image-masking and faithfulness evaluations.

## Results

| Model | Test accuracy | Adenocarcinoma recall |
| --- | ---: | ---: |
| Baseline CNN | 99.27% | 98.55% |
| EfficientNetB3 | 100.00% | 100.00% |
| ConvNeXt-Tiny | 100.00% | 100.00% |

These results were obtained on a held-out partition of 963 LC25000 images. Although I grouped perceptually similar images before splitting the data, patient- and slide-level independence was not established. The models were not externally validated, so these results should not be interpreted as evidence of clinical reliability.

## Data and reproducibility

The `data/` folder contains the training, validation, and test CSVs used in the experiments. The notebooks contain saved outputs, so the analyses can be inspected without rerunning GPU training. To rerun model evaluation or explainability analysis, the original LC25000 images and trained model files are also required; these large files are not included in this repository.

## Acknowledgement

The baseline CNN was adapted from an existing implementation associated with Li (2025):

Li, J. (2025). *CNN-based colon cancer detection – Python code*. https://doi.org/10.7910/DVN/B7OXBS

## Kaggle Notebooks

The project was developed using Kaggle. The original notebooks, including the code and saved results, are available below.

- [01 — Data Preparation and EDA](https://www.kaggle.com/code/educatedfish808/01-colon-histopathology-eda)
- [02 — Model Training and Evaluation](https://www.kaggle.com/code/educatedfish808/02-colon-histopathology-training)
- [03 — Explainable AI](https://www.kaggle.com/code/educatedfish808/03-colon-histopathology-xai)

The trained models and saved outputs are also available in the [colon_project_results dataset](https://www.kaggle.com/datasets/educatedfish808/colon-project-results).
