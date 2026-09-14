 Diabetes_Preprocessing
 01) Progress Review I — Data Preprocessing & EDA

=> Project Overview
Predicting whether a patient has diabetes (binary classification) using the
**Pima Indians Diabetes Database** (768 patients, 8 diagnostic features + `Outcome`
label). The original Kaggle listing (`uciml/pima-indians-diabetes-database`) was
taken down; the dataset is sourced instead via a verified direct CSV mirror of the
identical data (see `data/raw/`).

02) Dataset
- Source (mirror): https://raw.githubusercontent.com/npradaschnor/Pima-Indians-Diabetes-Dataset/master/diabetes.csv
- Original dataset: UCI Machine Learning Repository / National Institute of Diabetes
  and Digestive and Kidney Diseases
- 768 rows, 9 columns: `Pregnancies, Glucose, BloodPressure, SkinThickness, Insulin,
  BMI, DiabetesPedigreeFunction, Age, Outcome`

03) Group Member Roles

| IT Number |    Name              | Preprocessing Technique        | Notebook                                       |

| IT25103555 | Ishki M A           | Missing Data Handling          | `notebooks/IT_25103555_MissingData.ipynb`      |
| IT25101680 | Ligasaran N         | Outlier Detection & Removal    | `notebooks/IT_25101680_OutlierRemoval.ipynb`   |
| IT25102488 | Pathirana M P K S J | Encoding Categorical Variables | `notebooks/IT_25102488_Encoding.ipynb`         |
| IT25101457 | Jayaratne L S       | Normalization / Scaling        | `notebooks/IT_25101457_Scaling.ipynb`          |
| IT25103341 | Navoda W P T        | Feature Selection              | `notebooks/IT_25103341_FeatureSelection.ipynb` |
| IT25100533 | Sharaas M S M       | Dimensionality Reduction (PCA) | `notebooks/IT_25100533_PCA.ipynb`              |

05) Pipeline Order (and why)
1. Missing Data Handling** — must run first; several columns encode missing
   values as `0`, which would corrupt outlier detection and scaling if left as-is.
2. Outlier Removal** — runs on the imputed data so real biological outliers are
   detected, not artifacts of missing-value zeros.
3. Encoding Categorical Variables** — engineered BMI/Age categories added.
4. Feature Selection** — reduce to the most predictive columns.
5. Normalization / Scaling** — scale only the selected features.
6. Dimensionality Reduction (PCA)** — for visualization / compressed input.

=> How to Run
1. Open `group_pipeline.ipynb` in Google Colab.
2. Run all cells top to bottom (no local file needed — data loads directly from the
   CSV mirror URL).
3. Each member's individual notebook can be run independently for the viva —
   they each reload the raw dataset and demonstrate their technique in isolation.
4. Final processed dataset is written to `results/outputs/processed_diabetes_dataset.csv`.
5. All EDA charts are saved to `results/eda_visualizations/`.

=> Repository Layout

Group-Y2-S1-MLB-B7G1-08/
├── README.md
├── data/
│   ├── raw/            # place a local copy of diabetes.csv here if required
│   
├── notebooks/          # one preprocessing notebook per member
├── group_pipeline.ipynb
└── results/
    ├── eda_visualizations/
    └── outputs/
