# Freight Rate Prediction — ML Assessment

Machine learning solution for predicting freight rates from historical truck/load data.

See **`freight-rate-ml-assessment.pdf`** for the assessment instructions.



## Workflow

The solution is implemented in four notebooks:

1. **`01_EDA.ipynb`** — Exploratory data analysis and data cleaning
2. **`02_Feature_Engineering.ipynb`** — Feature selection and preprocessing
3. **`03_Model_Training.ipynb`** — Model training, cross-validation and hyperparameter tuning
4. **`04_Evaluation.ipynb`** — Validation predictions and December evaluation

The final model is a **Random Forest Regressor**.

## Setup

Clone the repository:

```bash
git clone https://github.com/lakshan0714/truck-freight-rate-prediction..git
cd truck-freight-rate-prediction.
```

Create a virtual environment:

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

Install dependencies:

```bash
python -m pip install -r requirements.txt
```

## Model Weights

## Running the Notebooks

Run the notebooks in this order:

```text
01_EDA.ipynb
      ↓
02_Feature_Engineering.ipynb
      ↓
03_Model_Training.ipynb
      ↓
04_Evaluation.ipynb
```

### 1. EDA

`01_EDA.ipynb` performs:

* Data exploration
* Missing-value analysis
* Negative-value checks
* Outlier detection
* Data cleaning
* Exploratory visualizations

### 2. Feature Engineering

`02_Feature_Engineering.ipynb` performs:

* Feature selection
* Correlation analysis
* Random Forest feature importance
* Feature preprocessing
* Train/test preparation

Processed datasets are saved under:

```text
dataset/processed/
```

### 3. Model Training

`03_Model_Training.ipynb` performs:

* Time-based train/test split
* Feature scaling
* Random Forest training
* Hyperparameter tuning
* 5-fold cross-validation
* Model evaluation

The final model is selected based on validation performance.

### 4. Evaluation

`04_Evaluation.ipynb` performs:

* Loading the trained model
* Processing the validation dataset
* Generating predictions for all validation loads
* Creating `validation_predictions.csv`
* Preparing December prediction inputs




## Run the Scorer

Install the required dependencies:

```bash
python -m pip install -r requirements.txt
```

Then run:

```bash
python score.py --predictions validation_predictions.csv --december-predictions dataset/december-chart-inputs.csv
```

## Project Structure

```text
.
├── dataset/
│   ├── train-test.csv
│   ├── validation.csv
│   ├── validation-predictions-template.csv
│   ├── december-chart-inputs.csv
│   │
│   └── processed/
│       ├── cleaned_freight_data.csv
│       ├── train_scaled.csv
│       └── test_scaled.csv
│
├── notebooks/
│   ├── 01_EDA.ipynb
│   ├── 02_Feature_Engineering.ipynb
│   ├── 03_Model_Training.ipynb
│   ├── 04_Evaluation.ipynb
│   └── december_completed.csv
│
├── results/
│
├── score_results/
│   └── candidate_december.png
│
├── weights_backup/
│
├── freight-rate-ml-assessment.pdf
├── requirements.txt
├── score.py
├── validation_predictions.csv
├── .gitignore
└── README.md
```

The scorer generates the required December evaluation output.

## Key Technical Decisions

* **Time-based validation** to better represent future freight-rate prediction.
* **Domain-aware outlier treatment** instead of blindly removing extreme observations.
* **Feature selection** using correlation analysis and Random Forest feature importance.
* **StandardScaler** fitted only on the training data to avoid preprocessing leakage.
* **Random Forest Regressor** for nonlinear relationships and feature interactions.
* **RandomizedSearchCV with 5-fold cross-validation** for hyperparameter tuning.
* Explicit handling of missing model features in the December evaluation.

## Final Deliverables

```text
validation_predictions.csv
```

contains the required predictions for the 12,000 validation loads.

The complete implementation, notebooks, preprocessing outputs, scoring script and documentation are included in this repository.
