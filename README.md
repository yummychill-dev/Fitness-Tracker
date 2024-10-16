# 🏋️‍♂️ Barbell Exercise Classifier using Meta Motion Sensor

This project implements a **Barbell Exercise Classifier** that uses **Meta Motion Sensor** data to classify various barbell exercises. The model utilizes **accelerometer** and **gyroscope** data to track movement patterns and classify exercises such as **squat, bench press**, and more.

## 🚀 Features

- **Accelerometer and Gyroscope Data**: Utilizes both accelerometer and gyroscope data captured at high frequency.
- **Real-Time Classification**: Provides real-time exercise classification using sensor data.
- **Multi-Exercise Classification**: Classifies multiple barbell exercises such as squats, bench press, and rows.
- **Data Processing Pipelines**: Includes functions for data preprocessing, feature extraction, and filtering.
- **Model Training**: Supports machine learning model training for accurate exercise classification.

## 📁 Data Pipeline

1. **Data Collection**: 
   - Raw data from Meta Motion sensors is collected, containing accelerometer and gyroscope readings during exercises.
   
2. **Preprocessing**:
   - The data is cleaned, and features such as acceleration and gyroscope measurements along three axes (`acc_x, acc_y, acc_z` and `gyr_x, gyr_y, gyr_z`) are extracted.
   - Sensor data is resampled and synchronized for consistency across readings.

3. **Feature Engineering**:
   - Features such as mean, standard deviation, and frequency domain transformations are computed to capture important patterns in the exercise movements.

4. **Clustering and Outlier Detection**:
   - Outliers are identified using methods like Interquartile Range (IQR), Local Outlier Factor (LOF), and Chauvenet's criterion. The data is then cleaned to ensure consistency.

5. **Training**:
   - Machine learning models such as **Random Forest**, **K-Nearest Neighbors (KNN)**, and **Feedforward Neural Networks** are trained using the extracted features.

## 📊 Model Training

1. **Load Data**: The dataset is loaded from Meta Motion sensor readings.
2. **Feature Extraction**: Features such as PCA components, accelerometer and gyroscope data, and temporal abstractions are generated.
3. **Model Setup**: A variety of machine learning models are trained and evaluated, including KNN, Random Forest, and Neural Networks.
4. **Evaluation**: Models are evaluated on test data using accuracy and confusion matrices to measure classification performance.

## 🔄 Inference

To classify new exercise data:

```python
from LearningAlgorithms import ClassificationAlgorithms
# Load the processed dataset
df = pd.read_pickle("../../data/interim/03_data_features.pkl")

# Load the classifier and make predictions
learner = ClassificationAlgorithms()
X_new = df.drop("label", axis=1)
y_pred = learner.random_forest(X_new)
print("Predicted Exercise:", y_pred)
```

## 📊 Results

- The classifier is evaluated using **accuracy** as the main performance metric, achieving robust results on the test dataset.
- Example: Correctly classifies exercises such as "squat" and "bench press."

## 🔧 Future Work

- **Enhanced Classification**: Incorporate more exercises and fine-tune models for higher accuracy.
- **Real-Time Deployment**: Deploy the classifier in a real-time setting with edge devices for live exercise tracking.
- **Sensor Fusion**: Combine additional sensors to enhance the quality of the exercise classification.
