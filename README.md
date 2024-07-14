# Room Occupancy Estimation

This repository contains the code and documentation for the Room Occupancy Estimation project. The primary goal of this project is to develop a predictive model for estimating room occupancy using non-intrusive environmental sensors like CO2, temperature, sound, and light sensors. By accurately estimating the number of occupants in a room, energy-saving measures can be implemented, reducing both energy consumption and carbon footprint.

## Table of Contents
- [Introduction](#introduction)
- [Data Description](#data-description)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Model Implementation](#model-implementation)
- [Dimensionality Reduction](#dimensionality-reduction)
- [Results and Conclusion](#results-and-conclusion)
- [Team Members](#team-members)
- [Instructor](#instructor)
- [Date](#date)

## Introduction
In modern sustainable building management, understanding and optimizing indoor environments for comfort and energy efficiency are crucial objectives. This study focuses on predicting room occupancy using non-intrusive environmental sensors.

## Data Description
The dataset used in this project is sourced from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/864/room+occupancy+estimation). It captures room occupancy in a 6m x 4.6m room with 7 sensor nodes and an edge node. Data was collected wirelessly every 30 seconds over four days, containing 10,129 data points and 18 columns. 

### Columns
- `Date`: Date of the experiment (yy/mm/dd format)
- `Time`: Time of the experiment (00:00:00)
- `S1_Temp`, `S2_Temp`, `S3_Temp`, `S4_Temp`: Temperature readings in Celsius from Sensor nodes 1 through 4.
- `S1_Light`, `S2_Light`, `S3_Light`, `S4_Light`: Light intensity readings in Lux from Sensor nodes 1 through 4.
- `S1_Sound`, `S2_Sound`, `S3_Sound`, `S4_Sound`: Sound sensor readings in Volts from Sensor nodes 1 through 4.
- `S5_CO2`: CO2 concentration in parts per million (PPM) from Sensor Node 5.
- `S5_CO2_Slope`: Slope of CO2 values taken in a sliding window.
- `S6_PIR`, `S7_PIR`: Binary values conveying motion detection from Sensor nodes 6 and 7.
- `Room_Occupancy_Count`: Count of room occupancy (0 to 3).

## Exploratory Data Analysis
Initial exploration of the data involved examining data types, summary statistics, and null values. We created new features, `hour_of_the_day` and `day_of_the_week`, from the `Date` and `Time` columns for further analysis. We addressed class imbalance and identified and treated outliers using various transformations.

## Model Implementation
The main focus of this project was to build models from scratch. All models were studied in depth, including their underlying conditions, assumptions, and the mathematics behind them. Based on this comprehensive study, we selected three candidate models and built them from scratch without using any libraries.

### Naive Bayes
Naive Bayes was chosen for its simplicity and effectiveness in handling categorical data. We used Laplace smoothing to handle zero-frequency issues and computed the parameters of the Gaussian distribution for each class.

### Support Vector Machines (SVM)
SVM was used to find the optimal hyperplane separating different classes. We employed gradient descent to optimize the cost function and included regularization to prevent overfitting.

### Logistic Regression
Logistic Regression was selected due to the independent and identically distributed nature of our data. We used one-vs-all classification and applied various transformations to handle outliers.

## Dimensionality Reduction
### PCA
Principal Component Analysis (PCA) was applied to reduce the number of variables while retaining most of the variance. PCA enabled us to capture approximately 94% of the variance with just 7 principal components.

## Results and Conclusion
We evaluated the performance of Naive Bayes, SVM, and Logistic Regression models. Logistic Regression emerged as the top performer in terms of overall accuracy, precision, and recall across all classes, making it the most suitable choice for this classification task.

