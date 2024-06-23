# Hybrid CNN-RNN-LSTM Model for Precipitation Prediction

## Project Overview
This project aims to predict precipitation over a specific region of Michigan Lake by integrating satellite cloud imagery with ground-based meteorological data. Using a combination of Convolutional Neural Networks (CNNs), Recurrent Neural Networks (RNNs), and Long Short-Term Memory networks (LSTMs), this model provides forecasts based on different prediction timelines.

## Dataset Description
The dataset spans from October 2006 to March 2017, containing:
- Satellite images of cloud cover over Michigan Lake, processed to extract pixel intensity values indicating cloud cover.
- Ground meteorological data, including temperature, humidity, wind speed, direction, and few other features.

Data was cleansed to handle missing values and normalized for use in machine learning models. Temporal features from date-time data were engineered into cyclic features to capture the inherent cyclicity of time.

## Methodologies and Steps
### 1. Data Loading and Preprocessing
- **Loading Data:** Data from various sources including satellite images and meteorological stations is loaded.
- **Cleaning Data:** Handling missing values using forward filling for meteorological data and setting cloud image data missing values to zero.
- **Feature Engineering:** Transformation of date and time into cyclic features to capture time-based patterns effectively. 

### 2. Exploratory Data Analysis (EDA)
- **Correlation Analysis:** Identifying and removing highly correlated meteorological features to avoid multicollinearity.
- **Session Windowing:** Dividing the day into three parts and summarizing data by maximum precipitation recorded to reduce data size and focus on significant events.

### 3. Feature Engineering
- **Wind Vector Calculation:** Transforming wind speed and direction into vector components to more accurately model their effects.
- **Cloud Cover Feature:** Extracting numerical values from cloud images representing the density and coverage, providing a direct input for the model.

### 4. Model Building
- **Sequence Creation:** Generating data sequences for model training where past three days’ data is used to predict future precipitation.
- **Hybrid Model Architecture:** Utilizing a CNN to process cloud imagery and an RNN to handle time-series meteorological data.
- **Class Imbalance Handling:** Implementing techniques like class weights and categorical focal loss to balance the dataset.

### 5. Model Training and Evaluation
- **Training Scenarios:** Training separate models to predict next day, and one and two days ahead precipitation.
- **Evaluation:** Using confusion matrices and accuracy metrics to evaluate model performance and adjust parameters.

### 6. Results Compilation and Analysis
- **Performance Analysis:** Assessing each model’s ability to predict various precipitation classes and summarizing findings.
- **Conclusion and Recommendations:** Drawing conclusions from the model performance and providing recommendations for future work.

## Conclusion
This project illustrates the potential of hybrid deep learning architectures in enhancing weather prediction models by integrating satellite imagery and meteorological data. Despite the challenges posed by differing data scales—24-hour meteorological records versus only 8-hour relevant satellite data—the project demonstrates a promising approach to combining these datasets. However, the disparity in the temporal resolution of the datasets presents an ongoing challenge, highlighting the need for innovative methods beyond simple concatenation to merge CNN and RNN outputs more effectively.

Handling class imbalance in this heavily skewed dataset has been a significant challenge, as standard approaches like class weights, initial bias, and focal loss have not fully addressed the imbalance. This suggests a need for more sophisticated techniques or entirely new approaches to model training that can better manage the nuances of time-series data in weather prediction.

Future work could explore alternative hybrid modeling techniques that might offer more nuanced integration of spatial and temporal data, potentially leading to improved predictive performance. Additionally, further research into balancing techniques tailored specifically for time-series data could pave the way for more accurate and reliable weather forecasting models.
