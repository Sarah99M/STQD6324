#  Human Activity Recognition using Smartphones (STQD6324 Assignment 1)

This project explores the possibility of recognizing human daily activities using smartphone sensor data (accelerometer and gyroscope), combining big data tools like **Apache Hive** with **Python-based analysis and visualization** in **Jupyter Notebook**.

---

##  Dataset Description

The dataset used is the [UCI HAR Dataset](https://archive.ics.uci.edu/dataset/240/human+activity+recognition+using+smartphones), collected from 30 volunteers (aged 19–48) who wore a Samsung Galaxy S smartphone on their waist while performing 6 daily activities:

| Label | Activity            |
|-------|---------------------|
| 1     | Walking             |
| 2     | Walking Upstairs    |
| 3     | Walking Downstairs  |
| 4     | Sitting             |
| 5     | Standing            |
| 6     | Laying              |

The original dataset has 561 features. In this project, **only the first 100 features** were used for Hive-based analysis.

---

##  Tools Used

-  Apache Hive (via Ambari + Hive View)
-  Python 3 + Jupyter Notebook
-  pandas / seaborn / matplotlib
-  Hive + Python connected via `impala.dbapi`

---

##  Project Workflow

### 1. Data Preparation
- Extracted nested zip files
- Loaded and merged training/test datasets
- Selected top 100 features
- Checked and confirmed no missing values
- Saved cleaned CSV for Hive upload

### 2. Hive Integration
- Cleaned data was uploaded to Hive as table `har_features_sample`
- Used Hive SQL (via Python) to query:
  - Sample count per activity
  - Average acceleration (`tBodyAcc-mean()-X`) per activity
  - Feature distribution for specific activities (e.g., Walking vs Sitting)

### 3. Data Visualization
-  Barplots: sample distribution & mean feature comparison
-  PCA: dimensionality reduction showing class separability
-  Boxplots: variance across activities for key features

---

##  Key Insights

- Activity classes are well balanced (≈1400–1900 samples per class)
- `tBodyAcc-mean()-X` shows clear variation across activities
- Walking Downstairs (Activity 3) has highest average acceleration
- Sitting and Laying activities are harder to separate with a single feature
- PCA shows certain clustering tendency, though some overlap exists

---

##  Recommendations

- Combine multi-axis features and derive new metrics (e.g., energy, jerk)
- Explore feature selection or use all 561 features for better model accuracy
- Use deep learning methods (e.g., CNN, LSTM) to capture temporal dependencies
- Consider data augmentation to boost underrepresented class performance

---

##  Project Structure

