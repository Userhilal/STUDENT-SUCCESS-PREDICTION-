# Student Success Prediction

This project analyzes and predicts student academic success using the **UCI Student Performance Dataset**.
The main objective is to study the factors that influence students' final grades and to build machine learning models capable of predicting academic performance.

## Project Objective

The goal of this project is to understand which factors can influence student success, such as:

* previous grades;
* study time;
* absences;
* family background;
* internet access;
* school support;
* social and educational variables.

The project includes both:

* **Regression**, to predict the final grade `G3`;
* **Classification**, to predict whether a student passes or fails.

The classification target is created using the rule:

```text
G3 >= 10 → Pass
G3 < 10  → Fail
```

## Dataset

The dataset used is the **Student Performance Dataset** from UCI.

It contains two CSV files:

* `student-mat.csv` for Mathematics;
* `student-por.csv` for Portuguese.

The two datasets are merged into one dataframe, with an additional column called `subject` to identify the course.

After merging, the dataset contains:

* 1044 students;
* 34 initial variables;
* academic, demographic, social and family-related features.

Important grade variables:

```text
G1 = first period grade
G2 = second period grade
G3 = final grade
```

## Exploratory Data Analysis

The EDA part includes:

* descriptive statistics of numerical variables;
* distribution of categorical variables;
* distribution of the final grade `G3`;
* analysis of the success rate;
* observation of students with `G3 = 0`;
* correlation analysis;
* boxplots and visual comparisons.

The purpose of EDA is to better understand the dataset before applying machine learning models.

## Data Preparation

Several preprocessing steps are applied:

* binary encoding for variables such as `yes/no`, `F/M`, `U/R`;
* OneHotEncoding for categorical variables with multiple categories;
* creation of the target variable `pass`;
* creation of derived variables such as:

  * `avg_parent_edu`;
  * `social_outings_index`;
  * `high_absence`;
  * `progression_G2_G1`;
* train/test split with 80% training data and 20% test data.

Two feature sets are created:

### Full Features

This version includes `G1` and `G2`.

It usually gives better performance because previous grades are strongly related to the final grade `G3`.

### Reduced Features

This version excludes `G1` and `G2`.

It is more useful for early prediction, because it tries to predict success before having previous grades.

## Machine Learning Models

The project uses several machine learning models.

### Regression Models

Used to predict the final grade `G3`:

* Linear Regression;
* Ridge Regression;
* Random Forest Regressor.

Evaluation metrics:

* RMSE;
* MAE;
* R² score.

### Classification Models

Used to predict pass or fail:

* Logistic Regression;
* Random Forest Classifier.

Evaluation metrics:

* Accuracy;
* Precision;
* Recall;
* F1-score;
* ROC-AUC.

## Pipeline

A Scikit-learn pipeline is used to organize preprocessing and modeling.

The pipeline includes:

* `StandardScaler` for numerical variables;
* `OneHotEncoder` for categorical variables;
* the selected machine learning model.

This makes the workflow cleaner and avoids preprocessing errors.

## Results and Interpretation

The project compares models with and without `G1` and `G2`.

Main observations:

* models using `G1` and `G2` perform better;
* previous grades are strong predictors of final performance;
* without `G1` and `G2`, other factors such as absences, previous failures, study time and family background become more important;
* ROC curves are used to evaluate classification performance;
* feature importance helps interpret the Random Forest model;
* residual analysis is used to understand regression errors.

## Technologies Used

* Python;
* Pandas;
* NumPy;
* Matplotlib;
* Seaborn;
* Scikit-learn;
* Jupyter Notebook.

## How to Run the Project

1. Clone the repository:

```bash
git clone https://github.com/Userhilal/STUDENT-SUCCESS-PREDICTION-.git
```

2. Open the project folder:

```bash
cd STUDENT-SUCCESS-PREDICTION-
```

3. Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

4. Launch Jupyter Notebook:

```bash
jupyter notebook
```

5. Open the notebook and run all cells.

## Project Structure

```text
STUDENT-SUCCESS-PREDICTION-
│
├── student-mat.csv
├── student-por.csv
├── Projet10_Reussite_Scolaire.ipynb
├── README.md
└── presentation_notes.md
```

## Conclusion

This project shows how data mining and machine learning can be used to analyze student performance and predict academic success.

The results confirm that previous grades are the strongest predictors, but other factors such as absences, failures, study habits and social variables can also provide useful information, especially for early prediction.

The project can help identify students at academic risk and support better educational decision-making.
