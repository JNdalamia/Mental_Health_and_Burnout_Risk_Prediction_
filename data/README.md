# Data

This folder is reserved for the dataset used in the **Mental Health and Burnout Risk Prediction** project.

## Dataset Source

The dataset is publicly available on Kaggle:

**Mental Health and Burnout Prediction Dataset**  
https://www.kaggle.com/datasets/mobeenfatimah/mental-health-and-burnout-prediction-dataset

The dataset contains **50,000 records and 40 columns** covering demographic, work-related, lifestyle, mental-health, and burnout-related variables.

## Download the Dataset

1. Open the Kaggle dataset page above.
2. Download the dataset as a CSV file.
3. Place the downloaded CSV file in this `data/` folder.
4. Update the notebook's file path if the filename differs from the one used in the notebook.

Example:

```text
project/
├── data/
│   ├── README.md
│   └── <downloaded-dataset>.csv
├── notebooks/
├── outputs/
├── requirements.txt
├── .gitignore
└── README.md
```

## Why the Dataset Is Not Included

The raw dataset is **not stored in this GitHub repository**. It can be downloaded directly from Kaggle using the link above.

This keeps the repository lightweight and avoids unnecessarily committing raw data files.

The project's `.gitignore` also excludes common data files such as:

```text
*.csv
*.xlsx
*.xls
*.parquet
```

## Dataset Usage

The dataset is used for:

- Exploratory Data Analysis (EDA)
- Statistical analysis
- Feature preprocessing and encoding
- Burnout-risk classification
- Machine learning model comparison
- Model evaluation and interpretation

The prediction target is:

```text
Burnout_Risk
```

with three classes:

- `Low`
- `Moderate`
- `High`

## Reproducibility

To reproduce the analysis:

1. Download the dataset from Kaggle.
2. Place the CSV file in this folder.
3. Install the dependencies listed in `requirements.txt`.
4. Open the project notebook and run the analysis from the beginning.

> **Note:** The dataset is used for educational and portfolio purposes. The project demonstrates machine-learning techniques and should not be interpreted as a clinical diagnostic system.
